# 1. HDFS Java API
## 1.1. 简介
想要使用`HDFS API`，需要导入依赖`hadoop-client`。如果是`CDH`版本的`Hadoop`，还需要额外指明其`仓库地址`：
        
```html
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
         http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.cyx</groupId>
    <artifactId>hdfs-java-api</artifactId>
    <version>1.0</version>


    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <hadoop.version>2.6.0-cdh5.15.2</hadoop.version>
    </properties>


    <!---配置 CDH 仓库地址-->
    <repositories>
        <repository>
            <id>cloudera</id>
            <url>https://repository.cloudera.com/artifactory/cloudera-repos/</url>
        </repository>
    </repositories>


    <dependencies>
        <!--Hadoop-client-->
        <dependency>
            <groupId>org.apache.hadoop</groupId>
            <artifactId>hadoop-client</artifactId>
            <version>${hadoop.version}</version>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

</project>
```
        
## 1.2. API使用
### 1.2.1. FileSystem
`FileSystem`是所有 HDFS 操作的主入口。由于之后的每个单元测试都需要用到它，这里使用`@Before`注解进行标注。
       
```java
private static final String HDFS_PATH = "hdfs://192.168.0.106:8020";
private static final String HDFS_USER = "root";
private static FileSystem fileSystem;

@Before
public void prepare() {
    try {
        Configuration configuration = new Configuration();
        // 这里我启动的是单节点的 Hadoop,所以副本系数设置为 1,默认值为 3
        configuration.set("dfs.replication", "1");
        fileSystem = FileSystem.get(new URI(HDFS_PATH), configuration, HDFS_USER);
    } catch (IOException e) {
        e.printStackTrace();
    } catch (InterruptedException e) {
        e.printStackTrace();
    } catch (URISyntaxException e) {
        e.printStackTrace();
    }
}


@After
public void destroy() {
    fileSystem = null;
}
```
      
### 1.2.2. 创建目录
支持递归创建目录。
     
```java
@Test
public void mkDir() throws Exception {
    fileSystem.mkdirs(new Path("/hdfs-api/test0/"));
}
```
        
### 1.2.3. 创建指定权限的目录
`FsPermission(FsAction u, FsAction g, FsAction o)`的三个参数分别对应：`创建者权限`，`同组其他用户权限`，`其他用户权限`，权限值定义在 FsAction 枚举类中。
        
```java
@Test
public void mkDirWithPermission() throws Exception {
    fileSystem.mkdirs(new Path("/hdfs-api/test1/"),
            new FsPermission(FsAction.READ_WRITE, FsAction.READ, FsAction.READ));
}
```
       
### 1.2.4. 创建文件，并写入内容
```bash
@Test
public void create() throws Exception {
    // 如果文件存在，默认会覆盖, 可以通过第二个参数进行控制。第三个参数可以控制使用缓冲区的大小
    FSDataOutputStream out = fileSystem.create(new Path("/hdfs-api/test/a.txt"),
                                               true, 4096);
    out.write("hello hadoop!".getBytes());
    out.write("hello spark!".getBytes());
    out.write("hello flink!".getBytes());
    // 强制将缓冲区中内容刷出
    out.flush();
    out.close();
}
```
        
### 1.2.5. 判断文件是否存在
```bash
@Test
public void exist() throws Exception {
    boolean exists = fileSystem.exists(new Path("/hdfs-api/test/a.txt"));
    System.out.println(exists);
}
```
      
### 1.2.6. 查看文件内容
查看小文本文件的内容，直接转换成字符串后输出：
       
```java
@Test
public void readToString() throws Exception {
    FSDataInputStream inputStream = fileSystem.open(new Path("/hdfs-api/test/a.txt"));
    String context = inputStreamToString(inputStream, "utf-8");
    System.out.println(context);
}
```
       
`inputStreamToString`是一个自定义方法，代码如下：
        
```java
/**
 * 把输入流转换为指定编码的字符
 *
 * @param inputStream 输入流
 * @param encode      指定编码类型
 */
private static String inputStreamToString(InputStream inputStream, String encode) {
    try {
        if (encode == null || ("".equals(encode))) {
            encode = "utf-8";
        }
        BufferedReader reader = new BufferedReader(new InputStreamReader(inputStream, encode));
        StringBuilder builder = new StringBuilder();
        String str = "";
        while ((str = reader.readLine()) != null) {
            builder.append(str).append("\n");
        }
        return builder.toString();
    } catch (IOException e) {
        e.printStackTrace();
    }
    return null;
}
```
       
### 1.2.7. 文件重命名
```java
@Test
public void rename() throws Exception {
    Path oldPath = new Path("/hdfs-api/test/a.txt");
    Path newPath = new Path("/hdfs-api/test/b.txt");
    boolean result = fileSystem.rename(oldPath, newPath);
    System.out.println(result);
}
```
       
### 1.2.8. 删除目录或文件
```java
public void delete() throws Exception {
    /*
     *  第二个参数代表是否递归删除
     *    +  如果 path 是一个目录且递归删除为 true, 则删除该目录及其中所有文件;
     *    +  如果 path 是一个目录但递归删除为 false,则会则抛出异常。
     */
    boolean result = fileSystem.delete(new Path("/hdfs-api/test/b.txt"), true);
    System.out.println(result);
}
```
         
### 1.2.9. 上传文件到HDFS
```java
@Test
public void copyFromLocalFile() throws Exception {
    // 如果指定的是目录，则会把目录及其中的文件都复制到指定目录下
    Path src = new Path("D:\\BigData-Notes\\notes\\installation");
    Path dst = new Path("/hdfs-api/test/");
    fileSystem.copyFromLocalFile(src, dst);
}
```
       
### 上传大文件并显示上传进度
```java
@Test
    public void copyFromLocalBigFile() throws Exception {

        File file = new File("D:\\kafka.tgz");
        final float fileSize = file.length();
        InputStream in = new BufferedInputStream(new FileInputStream(file));

        FSDataOutputStream out = fileSystem.create(new Path("/hdfs-api/test/kafka5.tgz"),
                new Progressable() {
                  long fileCount = 0;

                  public void progress() {
                     fileCount++;
                     // progress 方法每上传大约 64KB 的数据后就会被调用一次
                     System.out.println("上传进度：" + (fileCount * 64 * 1024 / fileSize) * 100 + " %");
                   }
                });

        IOUtils.copyBytes(in, out, 4096);

    }
```
        
