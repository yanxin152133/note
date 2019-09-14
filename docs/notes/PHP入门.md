# 代码仓库
仓库地址：[GitHub](https://github.com/yanxin152133/PHP.git)
        
**环境**：      
- Apache/2.4.39 (Win64)
- PHP 7.3.6
- PhpStorm 2019.2
- MySQL 5.6
        
**软件安装路径**
- Apache **D:\server\apache**
- PHP **D:\server\php7**
       
# 演示地址
[Demo](http://139.159.236.98/php/)
        
# 视频地址
参考：
- 链接: https://pan.baidu.com/s/1oxqVH8_GH94bhbpmQ4b-8Q 提取码: wsfd 
         
      
# PHP手册
文件名为**php_manual_zh.chm**即为PHP手册。
      
打不开参考下面链接：    
- [解决win10中无法打开CHM文件的方法](https://blog.csdn.net/qq_14998713/article/details/52155834)
       
# 搭建环境（Windows）
## 较早版本Apache 下载
下载地址：[Apache msi](https://archive.apache.org/dist/httpd/binaries/win32/)
<!--more-->
![](https://live.staticflickr.com/65535/47942980403_d6cb5a4b44_b.jpg)
      
## 较早版本Apache 安装
1. 双击下载的文件。
2. 相关配置。
![](https://live.staticflickr.com/65535/47943015906_fd90108b4a_z.jpg)
3. 选择自定义安装模式
![](https://live.staticflickr.com/65535/47942997977_460a18ec9d_z.jpg)
      
### Apache 目录结构说明
![](https://live.staticflickr.com/65535/47942998182_e4d3bab27e_z.jpg)
      
### Apache-httpd.exe介绍
Httpd.exe的详细应用      
      
1. 服务器进程：运行之后才能够使用。
![](https://live.staticflickr.com/65535/47978909873_f73c0d5d20_z.jpg)
     
2. 用来查看Apache具有哪些功能以及配置文件是否有错：httpd或者httpd.exe（文件所在目录）
![](https://live.staticflickr.com/65535/47978911057_67194e20c5_z.jpg)
     
3. 查看使用的模块：httpd -M
![](https://live.staticflickr.com/65535/47979212733_7e7d0c55bc_b.jpg)
      
4. 验证配置文件是否有效：httpd -t
![](https://live.staticflickr.com/65535/47979219121_af7c01dac5_b.jpg)

##  Apache/2.4.39 (Win64)下载与安装
### 下载
下载地址： [Apache/2.4.39 (Win64)](https://httpd.apache.org/download.cgi)
         
![](https://live.staticflickr.com/65535/48443791046_79bba8ccdc_b.jpg)
       
点击之后以**Apache Lounge**为例进行下载
         
![](https://live.staticflickr.com/65535/48443950892_a0944b542c_b.jpg)
        
之后根据自己安装的是哪个vc对应进行下载
      
### 安装、运行、卸载
1. 对下载的文件进行解压，选择自己需要安装的地方。
2. 打开conf\httpd.conf，将所有的**c:/Apache24** 替换为自己的安装目录。
3. 以**管理员身份**运行**CMD**，进入**\bin 目录**（httpd.exe所在目录）。
4. 输入 httpd.exe -k install -n "Apache24"  进行安装。
5. 至此，安装基本完成。到安装目录下的bin目录中找到 ApacheMonitor.exe ,双击运行,启动apache服务。
6. 如果要卸载这个服务 先要停止这个服务，然后输入httpd.exe -k uninstall –n “Apache24"进行卸载。
       
## PHP 安装
### 下载
下载地址：[PHP 7.3 (7.3.7)](https://windows.php.net/download#php-7.3)     
     
**关于php下载时VC各版本的区别和Non Thread Safe、Thread safe的简单辨析**
     
参考：[php下载时VC各版本的区别和Non Thread Safe、Thread safe的简单辨析](https://blog.csdn.net/yeweiyang16/article/details/71108427)
      
### 安装
1. 解压缩
2. 将压缩包放到E:/server/,同时重命名为PHP7
        
## 配置 Apache 加载 PHP 模块
      
**需改内容之后都需要重启apache**
         
1. Apache 加载 PHP 模块：在Apache的主配置文件中加载对应的PHP提供的模块
         
在apache安装目录的**conf目录**下对**httpd.conf**进行添加一下内容：     
      
```
#加载PHP
LoadModule php7_module 'D:/server/php7/php7apache2_4.dll'
```
2. 验证
     
      
**需改内容之后都需要重启apache**
       
```shell
Microsoft Windows [版本 10.0.17763.615]
(c) 2018 Microsoft Corporation。保留所有权利。

C:\Users\Yan>D:

D:\>cd server\apache\bin

D:\server\apache\bin>httpd.exe -t
AH00558: httpd.exe: Could not reliably determine the server's fully qualified domain name, using fe80::3993:9c4f:39af:664d. Set the 'ServerName' directive globally to suppress this message
Syntax OK

D:\server\apache\bin>httpd.exe -M
AH00558: httpd.exe: Could not reliably determine the server's fully qualified domain name, using fe80::3993:9c4f:39af:664d. Set the 'ServerName' directive globally to suppress this message
Loaded Modules:
 core_module (static)
 win32_module (static)
 mpm_winnt_module (static)
 http_module (static)
 so_module (static)
 actions_module (shared)
 alias_module (shared)
 allowmethods_module (shared)
 asis_module (shared)
 auth_basic_module (shared)
 authn_core_module (shared)
 authn_file_module (shared)
 authz_core_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 dir_module (shared)
 env_module (shared)
 include_module (shared)
 isapi_module (shared)
 log_config_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 setenvif_module (shared)
 php7_module (shared)   ##需要出现这个即可
```
       
3. Apache 分配工作给PHP模块：如果是PHP代码就交给PHP处理（通过文件后缀名.php进行识别）
     
4. 在apache安装目录的**conf目录**下对**httpd.conf**进行添加一下内容：     
      
```
# 分配给PHP
AddType application/x-httpd-php .php
```
      
**需改内容之后都需要重启apache**
     
5. 将PHP的配置文件加载到Apache配置文件中，使之共同生效。
- 在Apache中指定PHP配置文件所在路径
              
**httpd.conf**中添加：   

```
#加载PHP配置文件
PHPIniDir 'D:/server/php7'
```
      
- php.ini 文件是默认不存在的，是以development和production格式存在，需要格式化。
      
- 将php安装目录中的**php.ini-development**文件复制一个副本并重名为**php.ini**,然后重启Apache。
       
说明：PHP的配置文件已经加入到Apache的配置项中，意味着php.ini的修改需要Apache重启才会生效。
        
## httpd.conf
       
```
#加载PHP
LoadModule php7_module 'D:/server/php7/php7apache2_4.dll'
#加载PHP配置文件
PHPIniDir 'D:/server/php7'
# 分配给PHP
AddType application/x-httpd-php .php
```
         
## 配置PhpStorm
首先使用PhpStorm打开自己的项目，然后**File | Settings | Build, Execution, Deployment | Deployment**。
       
配置如下图：    
     
![](https://live.staticflickr.com/65535/48510854551_028b46b36c_h.jpg)
       
![](https://live.staticflickr.com/65535/48510854501_13337df58c_h.jpg)
          
![](https://live.staticflickr.com/65535/48511036182_0b8832317c_b.jpg)

**Folder**为apache的资源文件部署位置。
          
![](https://live.staticflickr.com/65535/48511036087_789e0cb919_b.jpg)
        
**Local path**为自己项目的位置，**Deployment path**为部署到apache中的映射文件名称，**Web path**为自己运行项目后需要输入到浏览器的路径名。多练习练习总会找到自己无法解决的关键。
       
![](https://live.staticflickr.com/65535/48510856301_8bbe50b2a2_b.jpg>)

这一步是将自己的代码同步到apache的htdocs文件夹下，**只需点击一次即可之后会自动同步。**
       
### 同步自己的代码到远程服务器
- 搭建自己的远程服务器环境
       
参考以下文章：    
- [docker搭建php、apache](https://yanxin152133.github.io/2019/08/12/Docker%E6%90%AD%E5%BB%BAPHP%E3%80%81apache%E7%8E%AF%E5%A2%83/)
      
- 配置phpstorm
	- 首先使用PhpStorm打开自己的项目，然后**File | Settings | Build, Execution, Deployment | Deployment**。
	- 点击`+`
	- 其他步骤如下图所示
       
![](https://live.staticflickr.com/65535/48525752431_76f90221a3_b.jpg)
         
![](https://live.staticflickr.com/65535/48525912012_7ddf7da41f_b.jpg)
         
![](https://live.staticflickr.com/65535/48525911917_c42d4a5eb7_b.jpg)
         
![](https://live.staticflickr.com/65535/48525752271_e63a5138d9_b.jpg)
         
![](https://live.staticflickr.com/65535/48525752171_6a6167224a_b.jpg)
         
![](https://live.staticflickr.com/65535/48525752106_fb77e430f5_b.jpg)
               
这个时候上传的选项就要选择远程服务器那个选项，而不是图中的本地的选项。**上图只是展示与本地不一样的地方**
         
## 安装MySQL
为了方便安装，使用docker来搭建MySQL环境。没有条件的可以百度自行安装MySQL。
         
      
### 安装Docker
参考：     
- [Ubuntu18.04 安装 Docker](https://yanxin152133.github.io/2019/05/26/Ubuntu18.04%20%E5%AE%89%E8%A3%85%20Docker/)
     
### 安装MySQL
输入以下命令：    
      
```bash
## 拉取官方的镜像,标签为5.6
docker pull mysql:5.6
## 运行
docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.6 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci

## -p 3306:3306：将容器的 3306 端口映射到主机的 3306 端口。
## e MYSQL_ROOT_PASSWORD=123456：初始化 root 用户的密码。
## --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci：解决中文问题

## 进入MySQL
docker exec -it mysql bash
## 登录MySQL
mysql -u root -p
## 然后输入密码
```
       
### MySQL的目录结构说明（Windows）
       
![](https://live.staticflickr.com/65535/48444297712_23161d2721_b.jpg)
       
**bin目录**
     
![](https://live.staticflickr.com/65535/48444166761_0c2857d850_b.jpg)
      
>软件设计结构：C/S和B/S
>C/S:Client客户端/Server服务端，用户需要安装客户端产品才能访问服务器，而且只能访问一种软件（当前自己）
>B/S:Browser浏览器和/Server服务端，用户只需要安装浏览器，就可以访问所有的服务器（B/S架构服务）
       
### MySQL的访问流程
>MySQL是一款C/S架构的软件，需要通过客户端来访问服务（MySQL其实也提供了其他模式的访问：通过一些插件扩展来充当客户端）

1. 启用MySQL客户端：mysql.exe,该软件本身可以通过CMD控制台运行。
2. MySQL客户端访问服务端需要进行寻找匹配：连接认证
连接：ip和端口确认，如果是本地都可以省略。
           
    -h 主机地址----》 -hlocalhost(可以是IP)       
    -P 端口---》-P3306      
    认证：通过用户名和密码进入服务器       
    -u 用户名---》-uroot,不可以省略（匿名用户除外） 
    -p 密码---》-proot
       
3. 退出命令：\q
           
**注意：通常连接认证的时候密码不建议明文，可以在输入-p之后回车，系统会再次让输入密码，这个时候就是密文**
       
## PHP连接MySQL数据库  
**PHP7正式移除了mysql 扩展，推荐使用mysqli或者pdo_mysql**
          
### php7配置mysqli或者pdo_mysql和使用mysqli或者pdo_mysql连接MySQL
        
#### 我是该用 MySQLi ，还是 PDO?
>如果你需要一个简短的回答，即 "你习惯哪个就用哪个"。
MySQLi 和 PDO 有它们自己的优势：
PDO 应用在 12 种不同数据库中， MySQLi 只针对 MySQL 数据库。
所以，如果你的项目需要在多种数据库中切换，建议使用 PDO ，这样你只需要修改连接字符串和部分查询语句即可。 使用 MySQLi, 如果不同数据库，你需要重新编写所有代码，包括查询。
两者都是面向对象, 但 MySQLi 还提供了 API 接口。
两者都支持预处理语句。 预处理语句可以防止 SQL 注入，对于 web 项目的安全性是非常重要的。
          
- 首先配置**php.ini**文件
- 编辑**php.ini**
    - 将 **;extension=mysqli** 改为**extension=mysqli**。有的版本中会是 **;extension=php_mysqli.dll**，原理都是将前面的 **;** 去掉
    - 将 **;extension=pdo_mysql** 改为**extension=pdo_mysql**。有的版本中会是 **;extension=php_pdo.dll**，原理都是将前面的 **;** 去掉
- 再次编辑**php.ini**
    - 将 **extension_dir = "ext"**改为 **extension_dir = "D:/server/php7/ext"**，**D:/server/php7/ext**为自己**安装php**的**绝对路径**
- **重启apache服务**
- 编辑**index.php**
          
```php
<?php
    phpinfo();
?>
```
        
- 浏览器输入：http://localhost:80/index.php
- 验证
       
![](https://live.staticflickr.com/65535/48461097092_ed8fd6cd37_b.jpg)
       
![](https://live.staticflickr.com/65535/48461096952_19ff034f6c_b.jpg)
       
- 数据库连接（三种方式）
- MySQLi - 面向对象

```php
<?php
$servername = "localhost";
$username = "username";
$password = "password";
 
// 创建连接
$conn = new mysqli($servername, $username, $password);
 
// 检测连接
if ($conn->connect_error) {
    die("连接失败: " . $conn->connect_error);
} 
echo "连接成功";
?>
```

- MySQLi - 面向过程
     
```php
<?php
$servername = "localhost";
$username = "username";
$password = "password";
 
// 创建连接
$conn = mysqli_connect($servername, $username, $password);
 
// 检测连接
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}
echo "连接成功";
?>
```
     
- PDO
             
```php
<?php
$servername = "localhost";
$username = "username";
$password = "password";
 
try {
    $conn = new PDO("mysql:host=$servername;", $username, $password);
    echo "连接成功"; 
}
catch(PDOException $e)
{
    echo $e->getMessage();
}
?>
```
       
参考链接：     
- [PHP 连接 MySQL](https://www.runoob.com/php/php-mysql-connect.html)
        
## 设定PHP的系统时区
- 编辑**php.ini**     
- 修改为以下内容
      
```ini
date.timezone = PRC
```

- 重启Apache服务
        
![](https://live.staticflickr.com/65535/48461241292_16bb9f32e5_b.jpg)
       
# PHP标记与注释
## PHP语法初步
PHP是一种运行在服务器端的脚本语言，可以嵌入到HTML中。
      
## PHP代码标记
在PHP历史发展中，可以使用多种标记来区分PHP脚本。
       
- ASP标记：<% php 代码 %>
- 短标记：<? php代码 ?>
      
以上两种基本弃用，如果需要使用则需要在配置文件中开启。
        
- 脚本标记：< script language="php">php代码</ script >
        
```php
<html>
<body>
    <b>
        <script language="php">
            <!--脚本标记-->
            echo 'hello world';
        </script>
    </b>
</body>
</html>


```        
       
注：移除了 ASP 和 script PHP 标签
        
- 标准标记（常用）：<?php php代码?>
      
```php
<html>
<body>
    <b>
        <?php
            echo 'hello world';
        ?>
    </b>
</body>
</html>
```
      
## PHP注释
>习惯：所有的代码在写的过程中都必须进行注释。

PHP注释分为两种：行注释和块注释。

- 行注释：一次注释一行
    `//`：后面跟的所有内容都是注释
    `#`：与`//`一样
      
- 块注释：一次注释多行
    `/**/`:`**`之间的全部都是注释。

      
代码示例：    
      
```php
<?php
   // 在脚本开始前：会对脚本功能进行简单阐述
   //  注释的内容会在PHP解析的过程中忽略


    // 块注释
    /*
     * @功能说明：注释说明
     * @作者：XXX
     * @版本：Version01
     */
    echo 'hello world';

?>

```
       
## PHP语句分隔符
语句分隔符：在PHP中，代码是以行为单位，系统需要通过判断行的结束，该结束通常都是一个符号：分号”`;`“(**英文状态下的分号**)。

代码示例：     

```php
<?php


/**
 * Create by PhpStorm
 * Date: 2019/8/6
 * Time: 21:38
 * Features: 语句分隔符
 */

    // 语句结束符
    // 动手试一下前一个语句不加语句结束符的概况和后一个语句不加语句结束符的概况
    // echo 'hello world'
    echo 'hello world';

?>

```
            
特殊说明：     
1. PHP标记结束符`?>`有自带语句结束符的效果，最后一行PHP代码可以没有语句结束符”`;`“。
2. PHP中其实很多代码的书写并不是嵌入到HTML中，而是单独存在，通常书写习惯中就不建议使用标记结束符`?>`，PHP会自动从开始到最后全部认为是PHP代码，从而解析。
         
# 变量
>PHP是一种动态网站开发的脚本语言,动态语言特点是交互性，会有数据的传递，而PHP作为”中间人“，需要进行数据的传递，传递的前提就是PHP能自己存储数据（临时存储）。
       
## 变量的基本概念
>变量来源于数学，是计算机语言中**能储存计算结果**或能表示值抽象概念。**变量可以通过变量名访问**。在指令式语言中，**变量通常是可变的**。

1. 变量是用来存储数据的。
2. 变量是存在名字的。
3. 变量是通过名字来访问的：数据
4. 变量是可以改变的：数据。
             
## 变量的使用
>PHP中的所有变量都必须使用”`$`“符号。
      
1. 定义：在系统中增加对应的变量名字（内存中）
2. 赋值：可以将数据赋值给变量名（可以在定义的同时完成）
3. 可以通过变量名访问存储的数据
4. 可以将变量从内存中删除
       
代码示例：     
      
```php
<?php


/*
 * Create by PhpStorm
 * Author: Yan
 * Date: 2019/8/6
 * Time: 22:03
 * Features: 定义变量
 *
 */

    // 变量
    // 定义变量：在PHP中不需要任何关键字诋毁能够以变量（赋值）

    $var1;    //定义变量
    $var1=1;
    $var2=1;    //定义同时赋值

    // 访问变量
    echo $var2; //通过var2变量名字找到存储的内容1，然后输出

    //修改变量
    $var2=2;
    echo '<hr/>',$var2;

    // 删除变量：使用unset(变量名字)
    unset($var2);
    echo $var2;

    // 第一，文件末尾的 ? >可以省略
    // 第二，该脚本若被其他脚本包含，所以该脚本不需要结束，否则会报错，因为是要和其他脚本衔接，只有在php代码后面需要写html的才使用闭合标签。
?>
```
      
## 变量命名规则
1. 在PHP中变量名必须以“`$`”符号开始；
2. 名字由字母、数字和下划线“`_`”构成，但是不能以数字开头；
3. 在PHP中本身还允许中文变量（不建议）
　　　　　

代码示例：　　　　
          
```php
    // 变量命名规则
    $var_1;$var_var_1;$_var1;   //正确格式

    $1var;     //不正确格式

    // 中文变量
    $中国=‘china’;
```
         
## 预定义变量
>预定义变量：提前定义的变量，系统定义的变量，存储许多需要用到的数据（预定义变量都是数组）。
        
- `$_GET`：获取所有表单以get方式提交的数据
- `$_POST`：POST提交的数据都会保存在此
- `$_REQUEST`：GET和POST提交的都会保存
- `$GLOBALS`：PHP中所有的全局变量
- `$_SERVER`：服务器信息
- `$_SESSION`：session会话数据
- `$_COOKIE`：cookie会话数据
- `$_ENV`：环境信息
- `$_FILES`：用户上传的文件信息
     
## 可变变量
>可变变量：如果 一个变量保存的值 刚好是另外一个变量的名字，那么可以直接通过访问一个变量得到另外一个变量的值：在变量前面在多加一个`$`符号。
      
代码示例：       
      
```php
<?php


    /*
    * Create by PhpStorm
    * Author: Yan
    * Date: 2019/8/7
    * Time: 15:15
    * Features: 可变变量
    */

    // 可变变量

    // 定义两个变量
    $a = 'b';
    $b = 'bb';

    echo $$a;
    // 1、找到$a，解析结果：b
	// 2、将前面的$符号与结果  b绑定：$b
	// 3、解析 
?>
```
       
## 变量传值
>将一个变量赋值给另外一个变量：变量传值。
       
变量传值一共有两个方式：值传递 ，引用传递。
       
- 值传递：将变量保存的值赋值一份，然后将新的值给另外一个变量保存。（两个变量没有关系）
        
![](https://live.staticflickr.com/65535/48478623067_44b462675f_b.jpg)
          
- 引用传递：将变量保存的值所在的内存地址，传递给另外一个变量：两个变量指向同一块内存空间。（两个变量是同一个值）
       
![](https://live.staticflickr.com/65535/48478474166_16933fb2d4_b.jpg)
       
在内存中，通常有以下几个分区：      
       
- 栈区：程序可以操作的内存部分（不存数据，运行程序代码），少但是快
- 代码段：存储程序的内部部分（不执行）
- 数据段：存储普通数据 （全局区和静态区）
- 堆区：存储复杂数据，大但是效率低
        
代码示例：      
         
```php
<?php


/*
 * Create by PhpStorm
 * Author: Yan
 * Date: 2019/8/7
 * Time: 16:04
 * Features: 变量传值
 */

	// 变量传值
 	// 值传递
	$a=10;
	$b=$a;
	$b=5;
	echo $a,$b,'</br>';

	//引用传递
	$c=10;
	$d=&$c;
	$c=5;
	echo $c,$d,'</br>';
?>
```
        
# 常量
>常量与变量 一样，都是用来保存数据的。
      
## 常量基本概念
>常量：const/constant，是一种在程序运行当中，不可改变的量（数据）。
常量一旦定义，通常数据不可改变（用户级别）。
      
## 常量定义形式
在PHP中常量有两种定义方式（5.3之后才有两种）：

- 使用定义常量的函数:`define('常量名',常量值);`
- 5.3之后才有的：`const 常量名=值;`
        
代码示例：     
      
```php
<?php


/*
 * Create by PhpStorm
 * Author: Yan
 * Date: 2019/8/7
 * Time: 16:27
 * Features: 常量
 */

	// 常量
	// 使用函数定义常量:define
	define('PI',3.14);

	// 使用const关键字定义
	const PII=3;
?>
```
      
常量名字的命名规则：    
1. 常量不需要使用“`$`”符号，一旦使用系统就会认为是变量
2. 常量的名字组成由字母、数字和下划线组成，不能以数字开头
3. 常量的名字通常是以大写字母为主（与变量以示区别）
4. 常量命名的规则比变量要松散，可以使用一些特殊字符，该方式只能使用define定义
       
代码示例：     
      
```php
<?php


/*
 * Create by PhpStorm
 * Author: Yan
 * Date: 2019/8/7
 * Time: 16:27
 * Features: 常量
 */

	// 常量
	// 使用函数定义常量:define
	define('PI',3.14);

	// 使用const关键字定义
	const PII=3;

	// 定义特使常量
	define('-_-','small');
	// const -_-='smali';   //错误
?>
```
      
注意细节：     
1. define和const定义的常量是由区别的：在于访问权限区别。
2. 定义常量通常不区分大写写，但是可以区分，可以参照define函数的第三个参数。

## 常量使用形式
>常量的使用与变量一样：不可改变值（在定义的时候必须赋值）。
      
>有的时候还需要使用另外一种形式来访问（针对的是特殊名字的常量），需要用到另外一个访问常量的函数：`constant('常量名')`。
       
>说明：常量和变量的使用
>1. 凡是数据会可能变化的，那么肯定使用变量
>2. 数据不一定会变，可以使用常量或者变量（变量居多）
>3. 数据不允许被修改的，一定用常量

代码示例：     

```php
<?php


/*
 * Create by PhpStorm
 * Author: Yan
 * Date: 2019/8/7
 * Time: 16:27
 * Features: 常量
 */

	// 常量
	// 使用函数定义常量:define
	define('PI',3.14);

	// 使用const关键字定义
	const PII=3;

	// 定义特使常量
	define('-_-','small');
	// const -_-='smali';   //错误

	// 使用常量
	echo PI;

	// echo -_-;    //特殊符号不能直接使用
    echo constant('-_-');
?>
```
          
## 系统常量
>系统常量：系统帮助用户定义的常量，用户可以直接使用。
      
**常用的几个系统常量**
      
`PHP_VERSION`:PHP版本号
`PHP_INT_SIZE`:整型大小
`PHP_INT_MAX`:整型能表示的最大值(PHP中整型是允许出现负数的：带符号)
      
代码示例：    
     
```php
<?php
    // 系统常量
    echo '</br>',PHP_VERSION,'</br>',PHP_INT_SIZE,'</br>',PHP_INT_MAX;
?>
```
      
在PHP中还有一些特殊的常量，他们由双下划线开始+常量名+双下划线结束，这种常量称之为系统魔术常量：魔术常量的值通常会跟着环境变化，但是用户改变不了。     
       
`__DIR__`:当前被执行的脚本所在电脑的绝对路径 
`__FILE__`:当前被执行的脚本所在的电脑的绝对路径（带自己文件的名字）
`___LINE__`:当前所属的行数
`_NAMESPACE__`:当前所属的命名空间
`__CLASS__`:当前所属的类
`__METHOD__`:当前所属的方法
      
代码示例：    
     
```php
<?php
    // 魔术常量
	echo '<hr/>';
	echo __DIR__,'<br/>',__FILE__,'<br/>',__LINE__,'<br/>';
    echo __LINE__;
?>
```
         
# 数据类型
>数据类型：data type,在PHP中指的是存储的数据本身的类型，而不是变量的类型。PHP是一种弱类型语言，变量本身没有数据类型。
        
## PHP的八种数据类型
>在PHP中将数据分为三大类八小类：
>- 简单（基本）数据类型:4个小类
>   - 整型：int/integer，系统分配4个字节存储，表示整数类型（有前提）
>   - 浮点型：float/double，系统分配8个字节存储，表示小数或者整型存不下的整数
>   - 字符串型：string，系统根据实际长度分配，表示字符串（引号）
>   - 布尔类型：bool/boolean，表示布尔类型，只有两个值：true和false
>- 复合数据类型：2个小类
>   - 对象类型：object，存放对象（面向对象）
>   - 数组类型：array，存储多个数据（一次性）
>- 特殊数据类型：2个小类
>   - 资源类型：resource，存放资源数据（PHP外部数据，如数据库、文件）
>   - 空类型：NULL，只有一个值就是NULL（不能运算）
       
## 类型转换
>类型转换：在很多的条件下，需要指定的数据类型，需要外部数据（当前PHP取得的数据），转换成目标数据类型。
         
在PHP中有两种类型转换方式：    
    
1. 自动转换：系统根据需求自己判定，自己转换（用的比较多，效率偏低）
2. 强制（手动）转换：认为 根据需要的目标类型转换
       
强制转换规则：在变量之前增加一个括号`()`，然后在里面写上对应类型：int/integer....其中NULL类型用到`unset()`。
         
       
在转换过程中，用的比较多的就是转布尔类型（判断）和转数值类型（算术运算）。
           
其他类型转布尔类型：true或者false，在PHP中比较少类型换变成false
         
![](https://live.staticflickr.com/65535/48486081426_2e19c56fa6_b.jpg)
        
其他类型转数值的说明     
1. 布尔true为1，false为0
2. 字符串转数值有自己的规则
2.1 以字母开头的字符串，永远为0
2.2 以数字开头的字符串，取到碰到字符串为止（不会同时包含两个小数点）
        
代码示例：     
       
```php
<?php


/*
 * Create by PhpStorm
 * Author: Yan
 * Date: 2019/8/8
 * Time: 15:06
 * Features: 数据类型
 */
	// 数据类型
	// 创建数据
	$a='abc1.1.1';
	$b='1.1.1.abc';

	// 自动转换
	echo $a+$b;    //算术运算，系统先转换成数值类型（整型和浮点型），然后运算

	//强制转换
    echo '<br/>',(float)$a,(float)$b;
?>
```
        
## 类型判断
>通过一组类型判断函数，来判断变量，最终返回这个变量所保存数据的数据类型（相同结果为true，失败为false）：是一组以is_开头后面跟类型名字的函数：`is_XXX(变量名)`
       
**bool类型不能用`echo`来查看，可以使用 `var_dump`结构来查看**
      
```php
var_dump(变量1，变量2....)
```
        
还有一组函数可以用来获取以及设定数据（变量）的类型
        
`gettype(变量名)`：获取类型，得到的是该类型对应的字符串      
`settype(变量名,类型)`：设定数据类型：与强制转换不同
1. 强制转换（类型）变量名，是对数据值复制的内容进行处理（不会处理实际存储的内容）
2. settype会直接改变数据本身
        
代码示例：     
       
```php
<?php


/*
 * Create by PhpStorm
 * Author: Yan
 * Date: 2019/8/8
 * Time: 15:06
 * Features: 数据类型
 */
	// 数据类型
	// 创建数据
	$a='abc1.1.1';
	$b='1.1.1.abc';

	// 自动转换
	echo $a+$b;    //算术运算，系统先转换成数值类型（整型和浮点型），然后运算

	//强制转换
	echo '<br/>',(float)$a,(float)$b;

	// 判断数据类型
	echo '<hr/>';
	var_dump(is_int($a));        //false
	var_dump(is_string($a));     //true

	echo '<hr/>';
	echo gettype($a);

	// 设置类型
	echo '<hr/>';
	var_dump(settype($b,'int'));
	echo gettype($b),$b;
?>
```
       
## 整数类型
>整数类型：保存整数数值（范围限制），4个字节存储数据，最大就是32位：42亿多。但是在PHP中默认是有符号类型（区分正负数）
        
在PHP中提供了四种整型的定义方式：十进制定义，二进制定义，八进制定义，十六进制定义。
       
```php
$a=120;   //十进制
$b=0b110;   //二进制
$c=0120;     //八进制
$d=0x120;    //十六进制
```
        
代码示例：     
       
```php
<?php


/*
 * Create by PhpStorm
 * Author: Yan
 * Date: 2019/8/8
 * Time: 19:58
 * Features: 简单数据类型：整型、浮点型和布尔型
 */


	// 定义四种整形数据
	$a1=110;
	$a2=0b110;
	$a3=0110;
	$a4=0x110;

    echo $a1,'~',$a2,'~',$a3,'~',$a4,'<hr/>';    //默认的PHP输出数值都会自动转换成十进制输出
?>
```
      
- 十进制：逢十进一，能够出现的数字是0-9；
- 二进制：逢二进一，能够出现的数字是0-1；
- 八进制：逢八进一，能够出现的数字是0-7；
- 十六进制：逢十六进一，能够出现的数字是0-9以及a-f，a表示10，依次类推。
        
**进制转换**：手动转换
       
十进制转二进制：除2倒取余。       
十进制转二进制：取出最大的2的N次方，直到结果为0。     
二进制到十进制之间的转换：从右侧开始，将对应的第几位作为2的指数，然后将所有的结果相加。     
         
**PHP中不需要用户这么复杂的去计算，提供了很多的函数进行转换**

- `decbin()`:十进制转二进制
- `decoct()`:十进制转八进制
- `dechex()`:十进制转十六进制
           
代码示例：     
      
```php
<?php
	// 利用进制函数运算
    var_dump(decbin(107));
?> 
```
        
## 浮点类型
>浮点型：小数类型以及超过整型所能存储范围的整数（不保证精度），精度范围大概在15个有效数字左右。
       
浮点型定义有两种方式：
```
$f=1.23;
$f=1.23e10;    //科学计数法，其中e表示底10，1.23x10^10
```
       
代码示例：     
      
```php
<?php
	// 浮点数
	$f1=1.23;
	$f2=1.23e10;
	$f3=PHP_INT_MAX+1;   //整型超过自身存储的大小之后会用浮点型存储。
	echo '<hr/>';
	var_dump($f1,$f2,$f3);
?>
```

简单说明浮点数为什么同样的字节数存储数据，但是却能表示更大的数据呢？
       
```
00000000 00000000 00000000 00000000 ->11111111 11111111 11111111 11111111(整型最大值：所有位都是有效数据)

浮点数:**中的七位算的结果都是10的指数，后面三个字节存储表示具体数值
00000000 00000000 00000000 00000000 ->1*1111111* 11111111 11111111 11111111
```
       
**尽量不要用浮点数做精确判断：浮点数保存的数据不够精确，而且在计算机中 凡是小数基本存的都不准确。**
       
代码示例：     
       
```php
<?php
	//浮点数判断
	$f4=0.7;
	$f5=2.1;
	$f6=$f5/3;
	echo '<hr/>';
	var_dump($f4==$f6);
?>
```
        
## 布尔类型
>布尔类型：两个值true和false，通常是用于判断比较
     
代码示例：    
      
```php
<?php
	// 布尔类型
	echo '<hr/>';
	$b1=true;
	$b2=false;
    var_dump($b1,$b2);
?>
```
       
在进行某些数据判断的时候，需要特别注意类型转换
- `empty()`:判断数据的值是否为空`“”`，不是`NULL`，如果为空返回true，不为空返回false
- `isset()`:判断数据存储的变量本身是否存在，存在变量返回true，不存在返回false
        
![](https://live.staticflickr.com/65535/48486081426_2e19c56fa6_b.jpg)
         
# 运算符
>运算符：operator,是一种将数据进行运算的特殊符号，在PHP中一共有十种运算符之多。
       
## 赋值运算符
赋值运算 ：符号是“`=`”,表示将右边的结果（可以是变量、数据、常量和其他匀速出来的结果），保存道内存的某个位置，然后将位置的内存地址赋值给左侧的变量（常量）。
       
## 算术运算符
算术运算：基本算术操作
     
- `+`:执行数据累加
- `-`:数据相减
- `*`:键盘上没有乘法符号，使用`*`代替，两个数相乘
- `/`:正斜杠代替，表示两个数相除
- `%`:取余（模）运算，两个数（整数）相除，保留余数
      
在进行除法运算或者取余运算的时候，对应的被除数（第二个数）不能为0。
       
代码示例：     
       
```php
<?php


/*
 * Create by PhpStorm
 * Author: Yan
 * Date: 2019/8/9
 * Time: 13:54
 * Features: 运算符
 */

	// 运算符

	// 算术运算符
	$a=$b=10;     //连贯赋值运算：两个不同变量
	$c=0;

	var_dump($a/0);	   //错误，被除数不能为0
?>
```

## 比较运算符
比较运算：比较两个数据的大小，或者两个内容是否相同。返回的结果都是 布尔类型：满足返回true，不满足返回false。
          
- `>`:左边大于右边，返回结果 true
- `>=`:左边大于或者等于右边
- `<`:左边小于右边
- `<=`:左边小于或者等于右边
- `==`:左边的与右边的相同（大小相同）
- `!=`:左边的与右边的不同（大小不同）
- `===`:全等于，左边与右边相同：大小以及数据的类型都要相同
- `!==`:不全等于，只要大小或者类型不同
      
代码示例：    
     
```php
<?php
	//比较运算符
	$a='123'; //字符串
	$b=123;    //整型

	//判断相等
	var_dump($a==$b);
	echo '<hr/>';
	// 全等判断
	var_dump($a===$b);
?>
```
       
## 逻辑运算符
>逻辑运算：针对不同的结果进行匹配，满足条件返回true，不满足返回false
      
- `&&`:逻辑与，左边的条件与右边的条件同时成立（两边的结果都为true）
- `||`:逻辑或，左边的条件或者右边的条件只要 有一个 满足即可
- `!`:逻辑非，对已有条件进行取反，本身为true，取反结果就是false
            
代码示例：     
     
```php
<?php

	// 逻辑运算符
	echo '<hr/>';
	$a = 'weekend';
	$b = 'goods';

	// 逻辑与
	var_dump($a == 'weekend' && $b == 'good');

	echo '<hr/>';

	// 逻辑或
	var_dump($a == 'weekend' || $b == 'good');

	echo '<hr/>';

	// 逻辑非
	var_dump($b=='good');
	var_dump(!($b=='good'));
?>
```
       
**逻辑非和逻辑或又称为短路运算：如果第一个表达式结果已经满足条件了，那么就不会运行逻辑运算符后的表达式：在书写代码的时候，尽量将出现概率最高的（能够直接判断出结果）的表达式放到第一位。**
           
## 连接运算符
>连接运算：是PHP中将多个字符串拼接的一种符号。
     
- `.`:将两个字符串拼接到一起
- `.=`:符合运算，将左边的内容与右边的内容连接起来，然后重新赋值给左边变量，如`A.=b ----->  A=A.b`
           
代码示例：    
     
```php
<?php

	// 连接运算符
	$a='hello';
	$b=123;

	echo $a.$b;   //将a变量和b变量连接起来

	echo '<hr/>';

	$a.=$b;     // $a=$a.$b
	echo $a;
?>
```
              
## 错误抑制符
>在PHP中有一些错误可以提前预知 ，但是这些错误可能无法避免，但是又比希望报错给用户看，可以使用错误抑制符处理。
      
- `@`:在可能出错的表达式前面使用@符号即可。
      
错误抑制符通常在生产环境（上线 ）会用到，在开发的时候不会用：系统本身 最好没有任何错误。
        
代码示例：    
      
```php
<?php

	// 错误抑制符
	$a = 10;
	$b = 0;

	$a / $b;
	@($a / $b);
?>
```
      
## 三目运算符
>三目运算：有三个表达式参与的运算（简单的分支结构缩写）
      
语法格式：    
       
```
表达式1?表达式2:表达式3;
```
         
运算：如果表达式1成立，那么执行表达式2，否则执行表达式3；
       
**注意：如果表达式本身比较复杂，建议使用括号包起来**
       
代码示例：    
       
```php
<?php

	//三木运算符
	$a = 10;

	$b = $a > 10 ? 100 : 0;
	echo $b;
?>
```
         
三木运算可以进行符合三木运算：三木运算中的表达式2和3都可以是另外一个三目运算。

```   
表达式1?(表达式2?表达式4:表达式5):(表达式3?表达式6:表达式7);
```
             
## 自操作运算符
>自操作：自己操作自己的运算符
      
- `++`:在原来的值上+1
- `--`:在原来的值上-1
         
在PHP中自操作符是可以放到变量前或者后：前置自操作和后自操作。

**后置自操作（`a++`）：先把自己所保存的值留下来，然后改变自己，自己给别人的值是原来的值。**
     
**前置自操作(`++a`)：先把自己改变，然后把改变后的值给别人。**
       
代码示例：     
      
```php
<?php

	// 自操作符
	$a=$b=1;
	$a++;   //独立操作，不参与其他运算
	++$b;   //独立操作，不参与其他运算
	echo $a,$b;

	echo '<hr/>';

	echo $a++,++$b;   //$a和$b不只是独立运算，还参与了输出操作
?>
```
        
衍生符号：类似自操作。
      
- `+=`:左边的结果与右边的结果相加，然后赋值给左边
- `-=`:左边的减去右边的结果，然后赋值给左边
- `*=`:乘法操作
- `/=`:除法操作
- `%=`:模操作
      
**注意：右边是一个整体，如`$a+=$b;  =====>   $a=$a+($b);`**
        
代码示例：     
      
```php
<?php
	$a = 10;
	$b = 5;
	$a += $b;       //$a=$a+$b=15;
	$a-=$b-1;       //$a=$a-($b-1)
	echo $a,'<br/>',$b;
?>
```
       
**如果进行除法或者取余运算，那么要考虑右边表达式的结果是否为0（为0出错）。**
         
## 计算机码
>计算机码：计算机在实际存储数据的时候，采用的编码规则（二进制规则）
>计算机码：原码、反码和补码，数值本身最左边一位是用来充当符号位：正数为0，负数为1
      
- 原码：数据本身从二进制转换成二进制得到的结果
	- 正数：左边符号位为0（正数的原码、反码、补码就是原码本身）
	- 负数：左边符号位为1
- 反码：针对负数，符号位不变，其他位取反
- 补码：针对负数，反码+1
        
系统中存在两个0：+0和-0     
+0：00000000
-0：10000000   原码
取反 11111111
补码 00000000
        
## 位运算符
>位运算：取出计算机中最小的单位（位bit）进行计算
      
- `&`:按位与，两个位都为1，结果为1，否则为0
- `|`:按位或，两个有一个为1，结果为1
       
代码示例：     
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/9
	 * Time: 22:22
	 * Features: 位运算
	 */

	// 位运算
	$a = 5;
	$b = -5;

	/*
	 * 5原码：00000101
	 *
	 *
	 * -5原码：10000101
	 * 取反：11111010    反码：符号位不变，其他位取反
	 * 求补：11111011   补码：反码+1
	 */

	// 按位与
	var_dump($a & $b);
 	/*
 	 * 取出系统存储的结果进行与操作
 	 * 5  00000101
 	 * -5 11111011
 	 * &  00000001   //最终结果
 	 * 转换：判断符号位，0表示正数，1表示负数（补码）
 	 */
 
?>
```
        
**注意**
**1. 系统进行任何位运算的时候都是使用的补码**
**2. 运算结束之后都必须转换成原码才是最终要显示的数据**
        
- `~`:按位非，一个位如果为1则变成0，否则反之
      
代码示例：    
     
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/9
	 * Time: 22:22
	 * Features: 位运算
	 */

	// 位运算
	$a = 5;
	$b = -5;

	/*
	 * 5原码：00000101
	 *
	 *
	 * -5原码：10000101
	 * 取反：11111010    反码：符号位不变，其他位取反
	 * 求补：11111011   补码：反码+1
	 */

	echo '<hr/>';
	// 按位非
	var_dump(~$b);
	/*
	 * -5 11111011    补码
	 * 取反   00000100
	 * 原码   00000100
	 */
?>
```
       
- `^`:按位异或，两个相同则为0，不同则为1
- `<<`:按位左移，整个位（32位），向左移动一位，右边补0
- `>>`:按位右移，整个位（32位）向右移动一位，左边补符号位对应内容（正数补0，负数补1）
      
代码示例：    
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/9
	 * Time: 22:22
	 * Features: 位运算
	 */

	// 位运算
	$a = 5;
	$b = -5;

	/*
	 * 5原码：00000101
	 *
	 *
	 * -5原码：10000101
	 * 取反：11111010    反码：符号位不变，其他位取反
	 * 求补：11111011   补码：反码+1
	 */

	echo '<hr/>';
	// 按位右移
	var_dump($b >> 1);
	var_dump($b >> 2);
	/*
	 * -5   11111011    补码
	 * >>2    11111110    //运算结果：补码
	 * -1     11111101       //反码
	 * 取反    1000010      //原码：-2
	 */
?>
```
        
**按位左移：乘以2的操作**      
**按位右移：除以2的操作（不完全正确）：整数除2会出现小数**     
         
## 运算符优先级
>运算符优先级：在多种运算符同时存在的时候，如何结合运算。
     
![](https://live.staticflickr.com/65535/48496217207_41006ba77b_b.jpg )
      
# 流程控制
>流程控制：代码执行的方向。
     
## 控制分类
- 顺序结构：代码从上往下，顺序执行。（代码执行的最基本结构）
- 分支结构：给定一个条件，同时有多种可执行代码（块），然后会根据条件执行某一段代码。
- 循环结构：在某个条件控制范围内，指定的代码（块）可以重复执行。
        
## 顺序结构
>顺序结构：最基本结构，所有代码默认是从上往下依次执行
        
## 分支结构
>在PHP中 ，分支结构主要有两种：if分支和switch分支
       
### if分支
>if：如果的意思，给定一个条件，同时为该条件设置多种（两种 ）情况，然后通过条件判断来实现具体的执行段。
           
基本语法：if分支PHP也是提供多种方式来实现。
     
- 最简if：只有一段代码，但是可以选择是否执行。
      
```
if(条件表达式){
	//满足条件所要执行的内容;    //顺序结构
}
```
       
- 基础if：有两面性，满足条件或者不满足条件都有对应的执行代码。
      
```
if(条件表达式){
	//满足条件后执行的代码段
}else{
	//不满足条件执行的代码段
}
```
        
- 复杂if结构：在判断条件之后，通常就有两种结果：满足或者不满足，在不满足之后还可以再次进行条件判断。
        
```
if(条件表示式1){
	//满足条件表达式1的代码段
}elseif(条件表达式2){
	//不满足表达式1条件，但是满足表达式2的代码
}...//可以使用多个elseif来进行再次条件筛选
else{
	//全部不满足要执行的代码
}
```
        
**注意：**
- 如果条件特别多才会采用复合if形式
- 如果条件比较单一（同一条件），会采用elseif复合方式
- 如果判断条件不一致，建议使用嵌套语法（不宜有太多层嵌套：影响代码美观）
       
**if分支，适用于所有的条件判断（分支结构）。**
        
代码示例：     
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/10
	 * Time: 23:09
	 * Features: if分支
	 */

	// 分支结构：if分支

	//最简if
	$day = 'weekend';

	// 如果是星期天就出去玩
	if ($day == 'sunday') {
		echo 'go out';
	}


	// 基本if判断
	// 如果是星期天就出去玩，否则上班
	if ($day == 'sunday') {
		echo 'go out play';
	} else {
		// 不满足条件
		echo 'work';
	}


	// 复合if结构
	// 如果是星期天就出去玩，否则不能，但是如果是星期六，那么可以在家玩
	echo '<hr/>';
	$day = 'saturday';
	if ($day == 'sunday') {
		echo 'go out';
	} else {
		// 包含全部不满足情况
		// 重新进行判断
		if ($day == 'saturday') {
			echo 'play at home';
		} else {
			echo 'work';
		}
	}

	echo '<hr/>';
	if ($day == 'sunday') {
		echo 'go out';
	} elseif ($day == 'saturday') {
		echo 'play at home';
	} else {
		echo 'work';
	}
?>
```
        
### switch分支
>switch分支：有一组情形存在，同过一条件，通常有多个值，但是每一个值都会有对应不同的代码执行。
       
switch判断方式：是将条件放到分支结构内部判断
      
switch基本语法：     
      
```
switch(条件表达式){
	// 所有条件判断：逐个进行
	case 值1:       //当前条件表达式的结果与值1相等（==）
		要执行的代码段;
		break;     //在switch中，如果条件匹配成功，那么系统就不会再次匹配条件，会自动顺序执行向下的所有代码（case代码除外），需要中断执行：break表示中断switch（结束）
	case 值2:
		要执行的代码段;
		break;
	....
	//可以使用类似else的语法：都不匹配
	default:
		//匹配失败的代码
		break;
}
```
       
代码示例：   
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/10
	 * Time: 23:30
	 * Features: switch 分支
	 */

	//switch分支
	// 根据日期做不同的事情
	$day=1;

	//从1到7做不同的事情
	switch ($day){
		//$day条件一定是个具体的值
		case 1:    //$day==1
			echo '1';
			break;
		case 2:
			echo '2';
			break;
		case 3:
			echo '3';
			break;
		case 4:
			echo '4';
			break;
		case 5:
			echo '5';
			break;
		default:
			echo 'error';
			break;
	}
?>
```
      
**if和switch的选择**
      
1. if能做所有的分支结构事情
2. switch处理的是条件比较多，同时比较单一，而且是固定值匹配的分支结构
       
## 循环结构
>循环结构：代码段在一定的控制下，可以多次执行。
      
在PHP中循环结构有以下几种：     
      
- for循环：通过条件、起始和终止判断执行
- while循环：通过判断条件终止
- do-while循环：跟while差不多
- foreach循环：专门针对数组
        
### for循环
for循环基本语法
      
```
for(条件表达式1;条件表达式2;条件表达式3){
	// 条件表达式1：定义初始化条件，可以有多种赋值语句存在，使用逗号分隔即可
	// 条件表达式2：边界判定，限定循环执行的次数
	// 条件表达式3：用来执行条件变化
	// 循环体
}
```
      
**for循环执行原理：**
     
1. 执行条件表达式1：定义初始化条件（执行依次）。
2. 执行条件表达式2：判断条件（N次）。
2.1. 满足条件：执行循环体。
2.2. 不满足条件：循环结束。
3. 执行循环体：（N次）。
4. 执行条件表达式3：循环变量变化（N次）。
5. 执行条件表达式2：判断条件（N次）。
6. 重复执行3-4-2步骤：直到第2步不满足条件结束循环。
         
for循环中条件表达式1的多变量定义：    
       
代码示例：     
     
```php
<?php

	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/11
	 * Time: 15:07
	 * Features: for循环
	 */

	// 循环结构：for循环

	// 从1到10输出：初始为1，结果为10
	for ($i = 1; $i <= 10; $i++) {
		// 输出
		echo $i,'<br/>';
	}
	// 最后：$i=11
	echo $i;

	<?php


	echo '<hr>';

	// 从1到10输出（10通常是动态得到的）
	for ($i = 1, $end = 10; $i <= $end; $i++) {
		// 输出
		echo $i, '<br/>';
	}

 
?>
```
        
for循环特殊使用：for循环中对应的括号（条件）可以一个都没有---》(死循环)。**一定要避免出现**
        
代码示例：    
      
```php
<?php
	// 无条件for循环
	for (;;){
		echo 'hello world','<br/>';
	}
?>
```
       
### while循环
while循环基本语法：    
      
```
条件初始化
while(条件表达式){
	// 条件表达式就是判断边界条件
	循环体;     //循环条件的变化
}
```
      
**for与while的选择：**
1. 如果是基于固定已知条件（数值而且有规律的变化），使用for循环
2. while可以做灵活的条件判定（while用的比较多）
       
代码示例：    
     
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/11
	 * Time: 15:30
	 * Features: while循环
	 */

	// while循环

	//定义条件
	$i=1;

	// 循环判定执行
	while ($i<=10){
		//循环体
		echo $i++,'<br/>';

		// 循环条件变更
		// $i++;
	}
?>
```
        
### do-while循环
>do-while：看着很像while，while首先进行条件判定然后执行循环体，有可能出现第一次就条件不满足，那么就会直接失败（循环体一次都不执行）。do-while就是先干了再说（执行循环体），后判断条件。（至少会执行一次循环体）
       
do-while基本语法：    
      
```
do{
	// 循环体
}while(条件表达式);
```
        
代码示例：     
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/11
	 * Time: 15:37
	 * Features: do-while循环
	 */

	// do-while循环结构

	// 输出1到10之间的偶数（条件判定加入）
	// 定义基础条件
	$i = 1;

	// 循环判定
	do {
		// 执行输出
		if ($i % 2 != 1){
			// 是偶数
			echo $i,'<br/>';   //条件变更
		}
		//条件变更
		$i++;
	}while($i<=10);
?>
```
       
### 循环控制
- 循环控制：在循环内部对循环本身进行控制
- 中断控制：重新开始循环，循环体中还有其他内容，也再执行
	- continue层级；    //默认是1（循环可以多层嵌套）
      
- 终止控制：循环直接结束
	- break层级；   //默认是1
	     
代码示例：     
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/11
	 * Time: 15:50
	 * Features: 循环控制
	 */

	// 循环控制

	// 需求：输出1到100之间5的倍数

	$i=1;

	while ($i<=100){
		// 判断:是否是5的倍数
		if ($i%5!=0){
			// 说明当前$i不是5的倍数

			//重新循环
			$i++;

			//重新循环
			// continue;   //系统重新跳到循环开始处

			//终止循环
			break;
		}

		// 输出数值
		echo $i++,'<br/>';
	}
	echo $i;
?>
```
      
**因为循环经常性会碰到嵌套（循环中间包含循环），如果再循环内部有些条件下，明确可以直到当前循环（或者说外部循环）不需要继续执行了，那么就是可以使用循环控制来实现：其中内部循环也可以控制到外部，就是通过使用层级参数。**

```      
continue 2;   //当前自己循环后面内部不再执行，同时外部循环如果还有循环体也不再执行，重新来过；
break2;     //当前自己循环结束，同时外部也结束（如果还有外部影响，继续执行）
```
      
## 流程控制替代语法
>流程控制替代语法：分支和循环结构的替代语法
      
PHP本身是嵌入到HTML中的脚本语言，需要再HTML中书写一些关于判断或者循环的结构语法，必须符合PHP标签规范，需要HTML与PHP进行混搭，如果使用原始的PHP代码那么会非常不美观。
       
需求：打印一个九九乘法表，使用表格展示。
        

       
在PHP书写到HTML中的这些大括号{}非常不美观，所以PHP提供了一种替代机制，让其可以不用书写大括号：   
       
```
for(;;){ }     ---->for(;;):  endfor
```
        
代码示例：    
      
```php
<table border=1>
	<?php for ($i = 1; $i < 10; $i++) { ?>
		<tr>
			<?php for ($j = 1; $j <= $i; $j++) { ?>
				<td>
					<?php echo $i . '*' . $j . '=' . $i * $j; ?>
				</td>
			<?php } ?>
		</tr>
	<?php } ?>
</table>



<table border=1>
	<?php for ($i = 1; $i < 10; $i++) :?>
		<tr>
			<?php for ($j = 1; $j <= $i; $j++) : ?>
				<td>
					<?php echo $i . '*' . $j . '=' . $i * $j; ?>
				</td>
			<?php endfor; ?>
		</tr>
	<?php endfor ?>
</table>
```
       
PHP中具体有哪些替代语法呢？PHP应该在HTML中只做数据输出，输出通常伴有条件判断和循环操作，因此PHP提供了对应分支结构和循环结构的替代方法：全部都是对应的一个模式：
           
- 左大括号`{`使用`冒号`代替；
- 右大括号`}`使用`end+对应的其实标记`替代；
- if:`if():  endif;`
- switch:`switch():  endswitch;`
- for:`fot():  endfor`
- while:`while():  endwhile`
- foreach:`foreach():  endforeach`
       
# 文件包含
>文件包含：在一个PHP脚本中，去将另外一个文件（PHP）包含进来，去合作完成一件事情。
      
## 文件包含的作用
文件包含的意义：
     
1. 要么使用被包含文件中的内容，实现代码的共享（重用）：向上包含（索要）
	- 向上包含：在当前脚本要用某个代码之前包含别的文件
2. 要么自己有东西可以给别的文件使用，实现代码的共享（重用）：向下包含（给予）
	- 向下包含：在自己有某个东西的时候，需要别的脚本来显示（自己代码写完之后包含其他文件）
      
最大的作用：分工协作，每个脚本做的事情不一样，因此可以使用写作方式，让多个脚本共同完成一件事情。
       
## 文件包含四种形式
在PHP中问之间的包含有四种形式（两大形式）
- include:包含文件
- include_once:系统会自动判断文件包含过程中，是否已经包含过（一个文件最多被包含一次）
- require:与include相同
- require_once:以include_once相同
         
包含基本语法：
       
```
include '文件名字';
include('文件名字');     //文件名字：路径问题
```
       
代码示例：    
      
**include1.php**
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/13
	 * Time: 20:36
	 * Features: 文件包含
	 */

	//被包含文件

	//定义数据
	$a=1;
	define('PI',3.14);
?>
```
       
**include2.php**
        
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/13
	 * Time: 20:37
	 * Features: 文件包含
	 */

	//包含文件：使用数据

	//包含文件
	include 'include1.php';   //包含当前文件include2.php所在文件夹下的include1.php
	echo $a,PI;
?>
```
      
以上方式：是先包含文件，后使用文件中的内容（向上包含）。
        
向下包含：先准备内容，然后包含另外的文件，在另外的文件中，使用当前的内容。
        
代码示例：    
       
**include3.php**
        
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/13
	 * Time: 20:46
	 * Features: 文件包含
	 */
	//定义数据
	$a = 10;
	const PI = 3.14;


	//包含文件：为了显示以上数据
	include_once 'include4.php';
?>
```
       
**include4.php**
       
```php
<table>
	<tr>
		<td><?php echo $a; ?></td>
		<td><?php echo PI; ?></td>
	</tr>
</table>
```
       
## 文件加载原理
PHP代码的执行流程：    
1. 读取代码文件（PHP程序）
2. 编译：将PHP代码转换成字节码（生成opcode）
3. zendengine来解析opcode，按照字节码去进行逻辑运算
4. 转换成对应的HTML代码
         
>文件加载原理：
>1. 在文件加载（include或者require）的时候，系统会自动地将被包含文件中的代码相当于嵌入到当前文件中。 
>2. 加载位置：在哪加载，对应的文件中的代码嵌入的位置就是对应的include位置。
>3. 在PHP中被包含的文件是单独进行编译的
       
PHP文件在编译的过程中如果出现了语法错误，那么会失败（不会执行）：但是如果被包含文件有错误的时候，系统会执行到包含include这条语句的时候才会报错。
        
## include和require区别
- include和include_once的区别：
      
include系统会碰到一次，执行一次；如果对同一文件进行多次加载，那么系统会执行多次；
include_once：系统碰到多次，也只会执行一次。
      
- require和include的区别：
       
本质都是包含文件，唯一的区别在于包含不到文件的时候，报错的形式不一样。
     
include的错误级别比较轻：不会阻止代码执行。      
require要求较高：如果包含出错代码不再执行（require后面的代码）
       
# 文件加载路径
文件在加载的时候需要指定文件路径才能保证PHP正确的找到对应的文件。
      
文件的加载路径包含两大类：
      
- 绝对路径
	- 从磁盘的根目录开始（本地绝对路径 ）
		- Windows  ：盘符C：/路径/PHP文件
		- Linux：/路径/PHP文件
	- 从网站根目录开始（网络绝对路径）
		- /：相对于网站主机名字对应的路径
		- localhost/index.php->E:/server/apache/htdocs/index.php
- 相对路径:从当前文件所在目录开始的路径
	- .|./：当前文件夹
	- ../：上级目录（当前文件夹的上一层文件夹）
	    
绝对路径和相对路径的加载区别：
1. 绝对路径相对效率偏低，但是相对安全（路径不会出问题）
2. 相对路径相对效率高些，但是容易出错（相对路径会发生改变）
       
# 文件嵌套包含
>文件嵌套包含 ：一个文件包含另外一个文件，同时被包含的文件又包含了另外一个文件。
       
代码示例：    
      
**include3.php**
        
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/13
	 * Time: 20:46
	 * Features: 文件包含
	 */
	//定义数据
	$a = 10;
	const PI = 3.14;


	//包含文件：为了显示以上数据
	include_once 'include4.php';
?>
```
       
**include4.php**
      
```php
<table>
	<tr>
		<td><?php echo $a; ?></td>
		<td><?php echo PI; ?></td>
	</tr>
</table>
```
        
**include6.php**
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/14
	 * Time: 14:58
	 * Features: 文件嵌套包含
	 */

	// 文件嵌套包含

	// 包含include3.php   文件本身包含了include4.php
	include '../../chap08/sec02/include3.php';
?>
```
       
嵌套包含的时候就很容易出现相对路径出错的问题：相对路径会因为文件的包含而改变（./和../）：Windows下面，每一个文件夹下都有.和..的文件夹。
       
# 函数
## 函数的基本概念
>函数：function，是一种语法结构，将实现某一个功能的代码块（多行代码）封装到一个结构中，从而实现代码的重复利用（复用）。

## 函数定义语法
函数有几个对应的关键点：function关键字、函数名、参数（形参和实参）、函数体和返回值。
         
基本语法如下：      
       
```
function 函数名(参数){
	// 参数体
	//返回值：return结果
}

```
       
定义函数的目的：是为了实现代码的重复利用，一个功能一个函数（简单明了）。
             
函数的使用：通过访问`函数的名字+()`,如果函数在定义的过程中有参数，那么在调用的时候就必须传入对应的参数。函数是一种结构不会自动运行，必须通过调用才会执行。
       
代码示例：    
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/14
	 * Time: 15:31
	 * Features: 函数
	 */

	// 函数

	// 定义函数
	function display()
	{
		// 函数体
		echo 'hello world';   //没有返回值
	}

	//调用函数
	display();
?>
```
       
函数实在代码执行阶段，碰到函数名字的时候才会调用，不是在编译阶段。       
         
函数的调用特点：只要系统在内存中能够找到对应的函数，就可以执行（函数的调用可以在函数定义之前）。
          
函数执行的内存分析：    
1. 读取代码进入到代码段（编译：将代码变成字节码存储到内存）
2. 根据代码逐行执行
        
以上原因：编译和执行是分开的（先编译后执行）
           
## 函数命名规范
>命名规范：由字母、数字和下划线组成，但是不能以数字开头。
          
函数作为一种常用的结构，一般遵循以下原则：函数通常名字代表着函数的功能，而有些功能会比较复杂，可能一个单词不足以表达，需要多个组合。
1. 驼峰法：除了左边第一个单词外，后面所有的单词首字母都大写。
2. 下划线法：单词之间通过下划线连接，单词都是小写。
       
函数名字：在一个脚本周期中，不允许出现同名函数（通常在一个系统开发中都不会使用同名函数）。
       
## 参数详解
函数的参数分为两种：形参和实参
        
### 形参
形参：形式参数，不具有实际意义的参数，是在函数定义使用的参数。
    
### 实参
实参：实际参数，具有实际数据意义的参数，是在函数调用时使用的参数。
        
形参是实参的载体：实参在调用时通常是需要传入到函数内部参与计算（运算），那么需要在函数内部去找到实际数据所在的位置才能找到数据本身：选哟实际调用的时候，将数据以实参的形式传递给形参：给形参赋值，从而使得函数内部可以用到外部数据。
        
代码示例：     
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/14
	 * Time: 16:23
	 * Features: 函数参数
	 */

	// 函数参数

	// 定义函数
	function add($arg1, $arg2)
	{     //形参可以有多个，使用逗号分隔即可
		//函数体：可以直接使用形参运算
		echo $arg1 + $arg2;
	}

	// 调用函数
	$num1 = 10;
	add($num1, 20);   //传入得实参，可以是变量或者其他有值地表达式（变量、常量、运算符计算结果）
?>
```
       
**注意**      
1. 在PHP中允许实参多余形参（个数）：函数内部不用而已
2. 在PHP中理论上形参个数没有限制（实际开发不会太多）
3. 实参不能少于形参个数
         
### 默认值
>默认值：default value，指的是形参的默认值，在函数定义的时候，就给形参进行一个初始赋值：如果实际调用传入的参数（实参）没有提供，那么形参就会使用定义时的值来进入函数内部参与运算。
      
通常默认值是用在一些，一定会有某个数据参与，但是不可能通常是某个我们知道的值。
           
代码示例：     
        
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/14
	 * Time: 16:23
	 * Features: 函数参数
	 */

	// 函数参数

	// 定义函数
	function add($arg1, $arg2)
	{     //形参可以有多个，使用逗号分隔即可
		//函数体：可以直接使用形参运算
		echo $arg1 + $arg2;
	}

	// 调用函数
	$num1 = 10;
	add($num1, 20);   //传入得实参，可以是变量或者其他有值地表达式（变量、常量、运算符计算结果）

	// 函数的默认值
	function jian($num1 = 0, $num2 = 0)    //当前$num1是形参，在编译时不执行，即便执行也是在jian函数内部，不会与外部的$num1变量冲突
	{
		echo $num1 - $num2;
	}

	// 调用：默认值如果存在，可以不用传入
	jian($num1);
	echo $num1;
?>
```
       
**注意事项**      
1. 默认值的定义是放在最右边的（多个），不能左边形参有默认值，但是右边没有
        
函数外部定义的变量名字与函数定义的形参名字冲突（同名）是没有任何关联关系的，如果多个函数使用同样的形参名字也不冲突。
      
### 引用传值
实参在调用时会将值赋值给形参，那么实际上使用的方式就是一种简单的值传递：将实参（如果是变量或者常量或者其他表达式）的结果（值）取出来赋值给形参：形参参与外部实际传入的参数本身没有任何关联关系：只是结果一样。
     
有的时候，希望在函数内部拿到的外部数据，能够在函数内部改变，那么就需要明确告知函数（定义时），函数才会调用的时候去主动获取外部数据的内存地址。以上这种定义形式参数的方式叫做引用传值。
        
基本语法：
       
```
function 函数名(形参1，形参2){
	//函数体
}
```
       
在调用的时候，必须给引用传值的参数位置传入实际参数，而且参数本身必须是变量。（变量才有指向的数据的内存地址）
      
代码示例：     
      
```php
<?php
	// 引用传值
	function display($a, &$b)
	{
		//修改形参的值
		$a = $a * $a;
		$b = $b * $b;
		echo '<hr>', $a, '<br/>', $b, '<br/>';
	}

	//定义变量
	$a = 10;
	$b = 5;

	//调用函数
	display($a, $b);
	echo '<hr>', $a, '<br/>', $b, '<br/>';
	//错误调用：引用传值直接传入数据本身而不是变量
	// display(10, 5);
?>
```
     
**注意事项**：在传入实参的时候，必须传入变量。
        
## 函数体
>函数体：函数内部（大括号{}里面的）的所有代码都称之为函数体。          
>函数体：基本上所有的代码都可以实现
>1. 定义变量 
>2. 定义常量
>3. 使用流程控制（分支、循环）
>4. 可以调用函数
         
## 函数返回值
>返回值：return，指的是将函数实现的结果，通过return关键字，返回给函数外部（函数调用处）：在PHP中所有的函数都有返回值。（如果没有明确return使用，那么系统默认返回NULL）
               
返回值作用：将计算结果返回给调用处。
        
代码示例：     
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/15
	 * Time: 14:36
	 * Features: 函数返回值
	 */

	// 函数返回值

	// 定义函数

	function display()
	{
		//输出
		echo __FUNCTION__;   //输出当前函数名字
	}

	var_dump(display());

	// 加法运算
	function add($num1, $num2)
	{
		return $num1 + $num2;    //返回结果

		//输出
		echo $num1;
	}

	$res = add(10, 20);     //外部定义变量接收函数运行结果
	echo $res;
?>
```
       
**注意**：函数的返回值可以是任意数据类型。
         
return关键字：      
1. return在函数内部存在的价值：返回当前函数的结果（当前函数运行结束）。
2. return还可以在文件中直接使用（不在函数里面）：代表文件将结果return后面跟的内容转交给包含当前文件的位置。（通常在系统配置文件中使用较多），在文件中也代表终止文件后面的代码“return之后的内容不会执行了。
      
## 作用域
>作用域：变量（常量）能够被访问的区域
>1. 变量可以在普通代码中定义
>2. 变量也可以在函数内部定义
         
在PHP中作用域严格来说分为两种：但是PHP内部还定义一些在严格意义之外的一种，所以总共算三种：        
1. 全局变量：就是用户普通定义的变量（函数外部定义）
	- 所属全局空间：在PHP中只允许在全局空间使用：理论上函数内部不可访问
	- 脚本周期：直到脚本运行结束（最后一行代码执行完）
2. 局部变量：就是在函数内部定义的变量
	- 所属当前函数空间：在PHP中只允许在当前函数自己内部使用
	- 函数周期：函数执行结束（函数是在栈区中开辟独立内存空间运行）
3. 超全局变量：系统定义的变量（预定义变量： `$_SERVER`、`$_POST`等）
	- 所属超全局空间：没有访问限制（函数内外都可以访问）
       
**超全局变量会将全局变量自动纳入到`$GLOBALS`没有作用域限制，所以能够帮助局部变量去访问全局变量：但是必须使用数组方式。**
        
**如果想函数内部使用外部变量：除了`$GLOBALS`之外，通过参数传值（如果要统一战线还可以使用引用传值）。**

在PHP中，其实还有一种方式，能够实现全局访问局部，同时局部也可以访问全局：global关键字。

global关键字：是一种在函数里面定义变量的一种方式。
1. 如果使用global定义的变量名外部存在（全局变量），那么系统在函数内部定义的变量直接指向外部全局变量所指向的内存空间（同一个变量）；
2. 如果使用global定义的变量名在外部不存在（全局变量），系统会自动在全局空间（外部）定义一个与局部变量同名的全局变量

本质的形式：在函数的内部和外部，对一个同名变量（全局和局部）使用同一块内存地址保存数据，从而实现共同拥有。

基本语法：     
       
```
global 变量名;      //不能赋值
变量名=值;    //修改
```
        
代码示例：     
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/15
	 * Time: 16:02
	 * Features: 作用域
	 */

	// PHP中作用域

	// 默认的代码空间:全局空间
	$global = 'global area';     //最终会被系统纳入到超全局空间中:$GLOBALS[]=global area

	//局部变量(函数内部定义)
	function display()
	{
		//所有的形参都可以理解为局部变量
		$inner = __FUNCTION__;   //局部变量

		//访问全局变量
		echo $global;      //不能访问
		echo '<hr>';

		// 访问全局变量
		// var_dump($GLOBALS);
		echo $GLOBALS['global'];
		echo '<hr>';

		//定义变量:使用全局变量
		global $global;    //全局空间存在
		echo $global;
		echo '<hr>';

		//定义变量:全局不存在
		global $local;
		$local = 'inner';
	}

	// 调用函数
	display();

	//全局空间访问局部变量
	echo $inner;          //不能访问
	echo '<hr>';

	//访问"局部"变量
	echo $local;
	echo '<hr>';
?>
```
        
虽然以上方式可以实现局部与全局的互访，但是通常不会这么使用。一般如果会存在特殊使用，也会使用参数的形式来访问（还可以使用常量：define定义的）。
        
## 静态变量
>静态变量：static，实在函数内部定义的崇拜能量，使用static关键字修饰，用来实现跨函数共享数据的变量：函数玉兴结束所有局部变量都会清空，如果重新运行函数，所有的局部变量又会重新初始化。
        
基本语法：    
      
```
function 函数名(){
	//定义变量
	static $变量名=值;   //通常会在定义的时候就直接赋值
}
```
      
静态变量的作用是为了跨函数共享数据（同一个函数被多次调用）。
      
静态变量的原理：系统在进行编译的时候就会对static这一行进行初始化：为静态变量赋值，函数在调用的时候，会自动跳过static关键字这一行。
      
静态变量的使用：    
1. 为了统计：当前函数被调用的次数
2. 为了统筹函数多次调用得到的不同结果（递归思想）
       
代码示例：    
     
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/15
	 * Time: 22:14
	 * Features: 静态变量
	 */

	// 静态变量
	// 定义函数
	function display()
	{
		//定义变量
		$local = 1;    //局部变量

		//定义静态变量
		static $count = 1;   //静态变量

		echo $local++, $count++, '<br/>';
	}

	//调用
	display();
	display();
	display();
	display();
?>
```
       
## 可变函数
>可变函数：当前有一个变量所保存的值，刚好是一个函数的名字，那么就可以使用变量+()来充当函数名使用。
       
代码示例：   
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/15
	 * Time: 22:28
	 * Features: 可变函数
	 */

	// 可变函数

	// 定义函数
	function display()
	{
		echo __LINE__, __FUNCTION__;
	}

	//定义变量
	$func = 'display';

	//可变函数
	$func();
?>
```
      
可变函数在系统使用的过程中还是比较多的，尤其是使用很多系统函数的时候：需要用户在外部定义一个自定义函数，但是是需要传入到系统函数内部使用。
       
代码示例：    
      
```php
<?php


	// 定义系统函数（假设）
	function sys_function($arg1, $arg2)
	{
		// 给指定的函数（第一个参数），求对应的第二个参数值得4次方
		//为实际用户输入的数值进行处理
		$arg2 = $arg2 + 10;

		return $arg1($arg2);

	}

	//定义一个用户函数：求一个数的四次方
	function user_function($num)
	{
		//将一个用户定义的函数传入给另外一个函数（函数名）去使用的过程，称之为回调过程，而被传入的函数称之为回调函数
		return $num * $num * $num * $num;
	}

	// 求10的4次方
	echo sys_function('user_function',10);
?>
```
        
# 匿名函数
## 基本概念
>匿名函数：没有名字的函数
       
基本语法：   
     
```
变量名=function(){
	函数体
};
```
        
代码示例：     
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/15
	 * Time: 23:03
	 * Features: 匿名函数
	 */

	// 匿名函数

	// 定义基本匿名函数
	$func = function () {
		//函数体
		echo 'hello world';
	};

	// 调用匿名函数：可变函数
	$func();
?>
```
      
变量保存匿名函数，本质得到的是一个对象（closure）。
       
代码示例：    
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/15
	 * Time: 23:03
	 * Features: 匿名函数
	 */

	// 匿名函数

	// 定义基本匿名函数
	$func = function () {
		//函数体
		echo 'hello world';
	};

	// 调用匿名函数：可变函数
	$func();

	// 查看变量内容
	var_dump($func);
?>
```
         
## 闭包
>闭包：closure，一词来源于以下两者的结合：要执行的代码块（由于自由变量被包含在代码块中，这些自由变量以及他们引用的对象没有被释放）和为自由变量提供绑定的计算环境（作用域）。
       
简单理解：函数内部有一些局部变量（要执行的代码块）在函数执行之后没有被释放，是因为在函数内部还有对应的函数在引用（函数的内部函数：匿名函数）。
        
代码示例：    
        
```php
<?php
	// 闭包函数
	function display()
	{
		// 定义变量：局部变量
		$name = __FUNCTION__;

		// 定义匿名函数
		$innerfunction = function () use ($name) {   //use就是将外部变量（局部）保留给内部使用（闭包）
			//函数内部的函数
			echo $name;
		};

		// 调用函数
		$innerfunction();
	}

	display();
?>
```
      
证明：函数的局部变量在函数使用完之后没有被释放？
1. 使用内部匿名函数
2. 匿名函数使用局部变量：use
3. 匿名函数被返回给外部使用
       
代码示例：     
       
```php
<?php

	// 闭包函数
	function display()
	{
		// 定义变量：局部变量
		$name = __FUNCTION__;

		// 定义匿名函数
		$innerfunction = function () use ($name) {   //use就是将外部变量（局部）保留给内部使用（闭包）
			//函数内部的函数
			// echo $name;
		};

		// 调用函数
		$innerfunction();
	}

	display();

	echo '<hr>';

	function display1()
	{
		// 定义变量：局部变量
		$name = __FUNCTION__;

		// 定义匿名函数
		$innerfunction = function () use ($name) {   //use就是将外部变量（局部）保留给内部使用（闭包）
			//函数内部的函数
			echo $name;
		};

		// 返回内部匿名函数
		return $innerfunction;
	}

	$closure = display1();

	//到66行位置：display1函数运行结束：理论上局部变量$name应该已经被释放
	$closure();
?>
```
       
# 伪类型
>伪类型：假类型，实际上在PHP中不存在的类型。但是通过伪类型可以帮助程序员去更好的查看操作手册从而方便学习。
      
伪类型主要有两种：在三大类八小类之外。
- `mixed`：混合的，可以是多种给PHP中的数据类型
- `number`：数值的，可以是任意数值类型（整型和浮点型）
      
# 常用系统函数
## 有关输出的函数
- `print()`:类似于echo输出提供的内容，本质是一种结构（不是函数）,返回1，可以不需要使用括号。
- `print_r()`:类似于var_dump，但是比var_dump简单，不会输出数据的类型，只会输出值（数组打印使用比较多）。
       
代码示例：     
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/13
	 * Time: 15:02
	 * Features: 系统函数
	 */

	// 系统函数

	//输出相关
	echo print ('hello world<br/>');
	print 'hello world<br/>';

	$a='hello world<br/>';
	print_r($a);
?>
```
        
## 有关时间的函数
`date()`:按照指定格式对应的时间戳（从1970年格林威治时间开始计算的秒数），如果没有指定特定的时间戳，那么就是默认解释当前时间戳。
`time()`:获取当前时间对应的时间戳
`microtime()`:获取微秒级别的时间
`strtotime()`:按照规定格式的字符串转换成时间戳。
       
代码示例：     
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/13
	 * Time: 15:02
	 * Features: 系统函数
	 */

	// 系统函数

	// 时间函数
	echo date('Y 年 m 月 d 日 H:i:s', 12345678), '<hr/>';
	echo time(), '<hr/>';
	echo microtime(), '<hr/>';

	echo strtotime("now"), "\n";
	echo strtotime("10 September 2000"), "\n";
	echo strtotime("+1 day"), "\n";
	echo strtotime("+1 week"), "\n";
	echo strtotime("+1 week 2 days 4 hours 2 seconds"), "\n";
	echo strtotime("next Thursday"), "\n";
	echo strtotime("last Monday"), "\n";
?>
```
          
## 有关数学的函数
`max()`:指定参数中最大的值
`min()`:比较两个数中较小的值
`rand()`:得到一个随机数，指定区间的随机整数
`mt_rand`:与rand一样，只是底层结构不一样，效率比rand高（建议使用）
`round()`:四舍五入
`cell()`:向上取整
`floor()`:向下取整
`pow()`:求指定数字的指定指数次结果
`abs()`:绝对值
`sqrt()`:求平方根
         
代码示例：     
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/16
	 * Time: 13:30
	 * Features: 有关数学的函数
	 */


	echo max(1, 3, 5, 6, 7);  // 7
	echo max(array(2, 4, 5)); // 5

	// When 'hello' is cast as integer it will be 0. Both the parameters are equally
	// long, so the order they are given in determines the result
	echo max(0, 'hello');     // 0
	echo max('hello', 0);     // hello

	echo max('42', 3); // '42'

	// Here 0 > -1, so 'hello' is the return value.
	echo max(-1, 'hello');    // hello

	// With multiple arrays of different lengths, max returns the longest
	$val = max(array(2, 2, 2), array(1, 1, 1, 1)); // array(1, 1, 1, 1)

	// 对多个数组，max 从左向右比较。
	// 因此在本例中：2 == 2，但 4 < 5
	$val = max(array(2, 4, 8), array(2, 5, 7)); // array(2, 5, 7)

	// 如果同时给出数组和非数组作为参数，则总是将数组视为
	// 最大值返回
	$val = max('string', array(2, 5, 7), 42);   // array(2, 5, 7)

	echo '<hr>';

	echo min(2, 3, 1, 6, 7);  // 1
	echo min(array(2, 4, 5)); // 2

	echo min(0, 'hello');     // 0
	echo min('hello', 0);     // hello
	echo min('hello', -1);    // -1

	// 对多个数组，min 从左向右比较。
	// 因此在本例中：2 == 2，但 4 < 5
	$val = min(array(2, 4, 8), array(2, 5, 1)); // array(2, 4, 8)

	// 如果同时给出数组和非数组作为参数，则不可能返回数组，因为
	// 数组被视为最大的
	$val = min('string', array(2, 5, 7), 42);   // string

	echo '<hr>';

	echo rand() . "\n";
	echo rand() . "\n";

	echo rand(5, 15);

	echo '<hr>';
	echo mt_rand() . "\n";
	echo mt_rand() . "\n";

	echo mt_rand(5, 15);

	echo '<hr>';
	echo round(3.4);         // 3
	echo round(3.5);         // 4
	echo round(3.6);         // 4
	echo round(3.6, 0);      // 4
	echo round(1.95583, 2);  // 1.96
	echo round(1241757, -3); // 1242000
	echo round(5.045, 2);    // 5.05
	echo round(5.055, 2);    // 5.06

	echo '<hr>';
	echo ceil(4.3);    // 5
	echo ceil(9.999);  // 10
	echo ceil(-3.14);  // -3

	echo '<hr>';
	echo floor(4.3);   // 4
	echo floor(9.999); // 9
	echo floor(-3.14); // -4

	echo '<hr>';
	var_dump(pow(2, 8)); // int(256)
	echo pow(-1, 20); // 1
	echo pow(0, 0); // 1

	echo pow(-1, 5.5); // PHP >4.0.6  NAN
	echo pow(-1, 5.5); // PHP <=4.0.6 1.#IND

	echo '<hr>';
	$abs = abs(-4.2); // $abs = 4.2; (double/float)
	$abs2 = abs(5);   // $abs2 = 5; (integer)
	$abs3 = abs(-5);  // $abs3 = 5; (integer)
	echo $abs, $abs2, $abs3;

	echo '<hr>';
	// Precision depends on your precision directive
	echo sqrt(9); // 3
	echo sqrt(10); // 3.16227766 ...
?>
```
        
## 有关函数的函数
`function_exists()`:判断指定的函数名字是否在内存中存在（帮助用户不去使用一个不存在的函数，让代码安全性更高）
`func_get_arg()`:在自定义函数中去获取指定数值对应的参数
`func_get_args()`:在自定义函数中获取所有的参数（数组）
`func_num_args()`:获取当前自定义函数的参数数量
         
代码示例：     
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/16
	 * Time: 13:38
	 * Features: 有关函数的函数
	 */

	//函数相关的函数
	echo '<pre>';
	function test($a, $b)
	{
		//获取指定参数
		var_dump(func_get_arg(1));

		//获取所有参数
		var_dump(func_get_args());

		//获取参数数量
		var_dump(func_num_args());
	}

	//调用函数
	function_exists('test') && test(1, '2', 3, 4);
?>
```
         
# 错误处理
>错误处理：指的是系统（或者用户）在对某些代码执行的时候，发现有错误，就会通过错误处理的形式告知程序员。
        
## 错误分类
1. 语法错误：用户书写的代码不符合PHP的语法规范，语法错误会导致代码在编译过程中不通过，所以代码不会执行（Parse error）
2. 运行时错误：代码编译通过，但是代码在执行的过程中会出现一些条件不满足导致的错误（runtime error）
3. 逻辑错误：程序员在写代码的时候不规范，出现了一些逻辑性的错误，导致代码正常执行，但是得不到想要的结果
         
## 错误代号
所有看到的错误代码在PHP中都被定义成了系统常量（可以直接使用）
1. 系统错误：
- `E_PARSE`：编译错误，代码不会执行
- `E_ERROT`：fatal error，致命错误，会导致代码不能正确继续执行（出错的位置断掉）
- `E_WARNING`：warning，警告错误，不会影响代码执行，但是可能得到意想不到的结果
- `E_NOTICE`：notice，通知错误，不会影响代码执行
2. 用户错误：
- `E_USER_ERROR`
- `E_USER_WARNING`
- `E_USER_NOTICE`
用户在使用自定义错误触发的时候，会使用到的错误代号（系统不会用到）
3. 其他：
- `E_ALL`
代替着所有从错误（通常在进行错误控制的时候使用比较多），建议在开发过程中（开发环境）使用
       
所有以E开头的错误常量（代号）其实都是由一个字节存储，然后每一种错误占据一个对应的位，如果想进行一些错误的控制，可以使用位运算进行操作。
         
排除通知级别notice:`E_ALL & ~E_NOTICE`
         
只要警告和通知：`E_WARNING｜E_NOTICE`
        
## 错误触发
- 程序运行时触发：系统自动根据错误发生后，对比对应的错误信息，输出给用户：主要针对代码的语法错误和运行时错误。
- 人为触发：知道某些逻辑可能会出错，从而使用对应的判断代码来触发相应的错误提示
        
代码示例：     
        
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/16
	 * Time: 14:13
	 * Features: 错误处理
	 */

	// 错误处理

	// 处理脚本让浏览器按照指定字符集解析的方法
	header('Content-type:text/html;charset=utf-8');


	//书写代码
	// $a = 100
	$a = 100;
	echo $a;

	// 除法运算
	$b = 0;
	if ($b == 0) {
		// 人为触发错误
		trigger_error('除数不能为0');   //默认notice，会继续执行
		trigger_error('除数不能为0',E_USER_ERROR);   //默认error，代码不会执行
	}
	echo $a / $b;
	echo 'hello';
?>
```
       
## 错误显示设置
>错误显示设置：哪些错误该显示，以及如何显示
      
在PHP中，其实有两种方式来设置当前脚本的错误处理
1. PHP的配置文件：全局配置：php.ini
- `display-errors`:是否显示错误
- `errod_reporting`:显示什么级别的错误
       
2. 可以在运行的PHP脚本中去设置：在脚本中定义的配置项级别比配置文件高（通常在开发当中都会在代码中去进行控制和配置）
- `error-reporting`：设置对应的错误显示级别
         
```
ini_set('配置文件中的配置项','配置值')
ini_set('error_reporting',E_ALL)
ini_set('display_errors',1)
```
         
## 错误日志设置
在实际生产环境中，不会直接让错误赤裸裸的展示给用户：
1. 不友好
2. 不安全：错误会暴露网站很多信息（路径、文件名）
      
所以在生产环境中，一般不会显示错误（错误也比较少），但是不可能避免会出现错误（测试的时候不会发现所有问题），这个时候不希望看到，但是有希望捕捉到可以让后台程序员去修改：需要保存到日志文件中，需要在PHP配置文件中或者代码中（ini_set）设置对应`error_log`配置项。
      
- 开启日志功能：`log_errors=On`
- 指定路径:`error_log=XXXXX`
       
## 自定义错误处理
最简单的错误处理：`trigger_errors()`函数，但是该函数不会阻止系统报错
      
PHP系统提供了一种用户处理错误的机制：用户自定义错误处理函数，然后将该函数增加到系统错误处理的句柄中，然后系统会在碰到错误之后，使用用户定义的错误函数。
        
1. 如何将用户自定义的函数放到系统中？`set-error_handler()`
2. 自定义错误处理函数，系统有要求
      
![](https://live.staticflickr.com/65535/48549360497_7c608fd854_b.jpg)
       
代码实现：
1. 自定义错误处理函数：注意参数
2. 注册自定义函数：修改错误处理机制
        
代码示例：     
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/16
	 * Time: 14:51
	 * Features: 自定义错误处理机制
	 */

	// 自定义错误处理机制

	// 自定义函数
	/*
	 * @param1 $errno,是系统提供的错误代码：E_ALL，E_NOTICE...
	 */
	function myerrors($errno, $errstr, $errorfile, $errorline)
	{
		// 判断：当前会碰到错误有哪些
		if (!(error_reporting() & $errno)) {   //error_reporting没有参数代表获取当前系统错误处理对应的级别
			return false;
		}
		// 开始判断错误类型
		switch ($errno) {
			case E_ERROR:
			case E_USER_ERROR:
				echo 'fatal error in file ' . $errorfile . 'on line' . $errorline . '<br/>';
				echo 'error info:' . $errstr;
				break;
			case E_WARNING:
			case E_USER_WARNING:
				echo 'Warning error in file ' . $errorfile . 'on line' . $errorline . '<br/>';
				echo 'error info:' . $errstr;
				break;
			case E_NOTICE:
			case E_USER_NOTICE:
				echo 'Notice error in file ' . $errorfile . 'on line' . $errorline . '<br/>';
				echo 'error info:' . $errstr;
				break;
		}
		return true;
	}

	// 报错
	echo $a;

	// 修改错误机制
	set_error_handler('myerrors');
	echo $a;
?>
```
        
当前属于简单自定义模式，如果要复杂，可以在某些影响代码功能的错误发生后，让用户跳转到某个指定界面
       
# 字符串类型
## 字符串定义语法
1. 单引号字符串：使用单引号包裹
2. 双引号字符串：使用双引号包裹
       
引号方式：比较适合那些比较短（不超过一行）或者没有结构要求的字符串，如果有结构要求，或者内容超过一行，可以使用以下两种结构定义
       
3. nowdoc字符串：没有单引号的单引号字符串
4. heredoc字符串：没有双引号的双引号字符串

heredoc和nowdoc比引号还是区别多一点，主要体现在源代码上。

代码示例：     

```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/16
	 * Time: 21:48
	 * Features: 字符串
	 */

	// 引号定义
	$str1 = 'hello';
	$str2 = "hello";
	var_dump($str1, $str2);

	echo '<hr>';

	// 结构化定义
	// heredoc结构
	$str3 = <<<EOD
		hello
				world
EOD;
	// nowdoc结构
	$str4 = <<<'EOD'
		hello
				world
EOD;
	var_dump($str3, $str4);
	echo '<hr>';


 
```
        
## 字符串转义
>转义的含义：在计算机通用协议中，有一些特定的方式定义的字母，系统会特定处理：通常这种方式都是使用反斜杠+字母（单词）的特性
>PHP在识别转义字符的时候也是使用同样的模式：反斜杠+字母。
         
在PHP中系统常用Definitely转义符号：
- `\'`:在单引号字符串中显示单引号
- `\"`:在双引号字符串中显示双引号
- `\r`:代表回车（理论上时回到当前行的首位置）
- `\n`:代表新一行
- `\t`:类型tab键，输出4个空格
- `\$`:在PHP中使用$符号作为变量符号，因此需要特定识别
        
**单引号与双引号的区别**：
1. 其中单引号中能够识别：`\'`;而双引号中就不能识别`\'`。
2. 双引号中因为能够识别`$`符号，所以双引号中可以解析变量，而单引号不可以。
      
双引号中变量识别的规则
1. 变量本身系统能够与后面的内容区分：应该保证变量的独立性，不要让系统难以区分。
2. 使用变量专业标识符（区分），给变量加上一组大括号{}。
      
结构化定义字符串变量的规则：
1. 结构化定义字符串对应的边界符有条件
1.1 上边界符后面不能跟任何内容
1.2 下边界符必须定格：最左边
1.3 下边界符同样后面只能跟分号，不能跟任何内容
2. 结构化定义字符串的内部（边界符之间）的所有内容都是字符串本身
       
代码示例：    
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/16
	 * Time: 22:03
	 * Features: 转义符号
	 */

	// 定义字符串识别转义符号
	$str1 = 'abc\r\ndef\t\'\"\$fg';
	$str2 = "abc\r\ndef\t\'\"\$fg";
	echo $str1, '<br>', $str2;
	echo '<hr>';

	$a = 'hello';
	//变量识别
	$str3 = 'abc  $a  dfg';
	$str4 = "abc  $a  dfg";
	$str5 = "abc  $adfg";
	$str6 = "abc{$a}dfg";
	echo $str3, '<br>', $str4, '<br>', $str5, '<br>', $str6;

	echo '<hr>';

	$str7 = <<<EOD
	//js
	<script>
		alert('$str3');
	</script>
EOD;
	echo $str7;
?>
```
         
## 字符串长度问题
1. 基本函数strlen()：得到字符串的长度（字节为单位）
2. 多字节字符串的长度问题：包含中文的长度
3. 多字节字符串扩展模块：mbstring扩展；php.ini文件中开启mbstring。
       
mbstring扩展针对的是一些关于字符统计：strlen只是针对标准交换码ASCII，mbstring会针对不同的字符集。
       
代码示例：     
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/16
	 * Time: 22:27
	 * Features: 字符串长度
	 */
	// 字符串长度

	// 定义字符串
	$str1 = 'aknsfjknkfsjadnf';
	$str2 = '你好123';
	echo strlen($str1), '<br/>', strlen($str2);

	echo '<hr>';
	// 使用mbstring扩展
	echo mb_strlen($str1), '<br/>', mb_strlen($str2), '<br/>', mb_strlen($str2, 'utf-8');
?>
```
        
## 字符串相关函数
1. 转换函数：
- `implode()`:将数组中的元素按照某个规则连接成一个字符串
- `explode()`:将字符串按照某种格式进行分割，变成数组
- `str_split()`:按照指定长度拆分字符串得到数组
2. 截取函数：
- `trim()`:本身默认是用来去除两边的空格（中间不行），但是也可以指定要去除的内容，是按照指定的内容循环去除两边有的内容：直到碰到一个不是目标字符串为止
- `itrim()`:去除左边的
- `rtrim()`:去除右边的
3. 截取函数：
- `substr()`:指定位置开始截取字符串，可以截取指定长度（不指定到最后）
- `strstr()`:从指定位置开始截取到最后
4. 大小转换函数：
- `strolower()`:全部小写
- `strtoupper()`:全部大写
- `ucfirst()`:首字母大写
5. 查找函数：
- `strpos()`:判断字符在目标字符串中出现的位置（首次）
- `strrpos()`:判断字符在目标字符串中最后出现的位置
6. 替换函数：
- `str_replace()`:将目标字符串中部分字符串进行替换
7. 格式化函数：
- `printf()`:格式化输出数据
- `sprintf()`:格式化输出数据
8. 其他：
- `str_repeat()`:重复某个字符串N次
- `str_shuffle()`:随机打乱字符串	
        
# 数组
## 数组的概念
>数组：array，数据的组合，指将一组数据（多个）存储到一个指定的容器中国，用变量指向该容器，然后可以通过变量一次性得到该容器中的所有数据。
       
## 数组定义语法
在PHP中系统提供了多种定义数组的方式：
1. 使用array关键字：最常用的
       
```
$变量=array[元素1,元素2,元素3...];
```
     
2. 可以使用中括号来包裹数据
       
```
$变量=[元素1,元素2...];
```
        
3. 隐形定义数组：给变量增加一个中括号，系统会自动变成数组
        
```
$变量[]=值1;     //如果不提供下标也可以i，系统会自动生成（数字：从0开始）
$变量[下标]=值;  //中括号里面的内容称之为小标key，该下标可以是字母（单词）或者数字，与变量名的规则相似
```
      
代码示例：     
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/17
	 * Time: 13:39
	 * Features: 数组
	 */
	// 数组

	// 定义数组
	$arr1 = array('1', 2, 'hello');
	var_dump($arr1);
	echo '<hr>';

	// 定义数组：[]
	$arr2 = ['1', 2, 'hello'];
	var_dump($arr2);
	echo '<hr>';

	// 隐形数组
	$arr3[] = 1;
	$arr4[10] = 1;
	$arr4[] = '1';
	$arr5['key'] = 'key';
	var_dump($arr3);
	echo '<hr>';
	var_dump($arr4);    //注意$arr4的下标
	echo '<hr>';
	var_dump($arr5);
?>
```
       
## PHP数组特点
1. 可以整数下标或者字符串下标
	- 如果数组下标都为整数：索引数组
	- 如果数组下标都为字符串：关联数组
2. 不同下标可以混合存在：混合数组
3. 数组元素的顺序以放入顺序为准，跟下标无关
4. 数字下标的自增长特性：从0开始自动增长，如果终极按手动出现较大的，那么后面的自增长元素从最大的值+1开始
5. 特殊值下标的自动转换
6. PHP中数组元素没有类型限制
7. PHP中数组元素没有长度限制
       
补充：PHP中的数组是很大的数据，所以存储位置是堆区，为当前数组分配一块连续的内存。
         
代码示例：    
       
```php
<?php
	//特殊下标转换
	$arr6[false] = false;
	$arr6[true] = true;
	$arr6[NULL] = NULL;
	var_dump($arr6);
	echo '<hr>';
?>
```
        
## 多维数组
>多维数组：数组里面的元素又是数组
        
### 二维数组
>二维数组：数组中所有的元素都是一维数组
       
代码示例：    
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/17
	 * Time: 下午 2:17
	 * Features: 多维数组
	 */

	// 多维数组
	// 定义二维数组
	$info = array(
		array('name' => 'Jim', 'age' => 30),
		array('name' => 'Jim1', 'age' => 20),
		array('name' => 'Jim2', 'age' => 10)      //最后一个元素，后面可以跟逗号不影响（不建议）
	);
	echo '<pre>';
	print_r($info);
?>
```
       
### 多维数组
>在第二维的数组元素中可以继续是数组，在PHP中没有维度限制（PHP本质没有二维数组）。**但是不建议使用超过三维以上数组，会增加访问复杂度，降低访问效率。**
         
### 异形数组（不规则数组）
>异形数组：数组中的元素不规则，有普通基本变量也有数组。在实际开发中，并不常用，尽量让数组元素规则化（便于进行访问）
        
## 数组遍历
### 遍历的基本含义
>数组遍历：普通数组数据的访问都是通过数组元素的下标来实现访问，如果说数组中所有的数据都需要一次输出出来，就需要我们使用到一些简化的规则来实现自动获取下标以及输出数组元素。
       
### foreach遍历语法
基本语法：      
       
```
foreach($数组变量 as [$下标=>]$值){
	//通过$下标访问元素的下标，通过$值访问元素的值
}
```
         
通常如果是关联数组（字母下标），就需要下标，如果是数字下标就直接访问值。
        
在进行数据存储定义的时候，通常二维数组不会两个维度的key下标都为数字，一般是一维为数组（无意义），二维为字符串（数据库表字段），所以在进行遍历的时候，通常是只需要针对一维进行遍历，取得二维数组元素，然后二维数组元素通过下标去访问。
           
代码示例：    
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/17
	 * Time: 下午 11:11
	 * Features: 数组遍历：foreach
	 */

	// 数组遍历：foreach

	// 定义数组
	$arr = array(1, 2, 3, 4, 5, 6, 7, 8, 9, 0);

	// foreach循环
	foreach ($arr as $v) {
		//$v随意命名
		echo $v, '<br/>';
	}

	// foreach循环
	foreach ($arr as $k => $v) {
		//$v随意命名
		echo 'key:', $k, '==value:', $v, '<br/>';
	}

	$arr = array(
		0 => array('name' => 'Tome', 'age' => 30),
		1 => array('name' => 'Tome1', 'age' => 20),
		2 => array('name' => 'Tome2', 'age' => 10)
	);
	// 通过foreach遍历一维元素
	foreach ($arr as $value) {
		// 1.可以继续遍历：增加foreach遍历$value
		// 2.可以使用下标访问
		echo 'name is:', $value['name'], 'and age is:', $value['age'], '<br/>';
	}
?>
```
        
### foreach遍历原理
>foreach遍历原理：本质是数组的内部有一颗指针，默认是指向数组元素的第一个元素，foreach就是利用指针去获取数据，同时移动指针。
>1.  foreach会重置指针：让指针指向第一个元素
>2. 进入foreach循环：通过指针取得当前第一个元素，然后将下标去除放到对应的下标变量中（如果存在），将值取出来放到对应的值变量中；（指针下移）
>3. 进入到循环内部（循环体），开始执行
>4. 重复2和3，直到2的时候遇到指针取不到内容（指针指向数组最后）
       
## for循环遍历数组
for循环：基于已知边界条件（起始和结束）然后又条件的变化（规律）
        
因此：for循环遍历数组有对应条件
1. 获取数组长度：count(数组)得到数组元素的长度
2. 要求数组元素的下标是规律的数字
        
代码示例：    
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/17
	 * Time: 下午 11:31
	 * Features: for循环遍历数组
	 */
	// for循环遍历数组
	//数组特点：索引数组，下标规律
	$arr = array(1, 2, 3, 4, 5, 6, 7, 8, 9);
	for ($i = 0, $len = count($arr); $i < $len; $i++) {
		echo 'key is:', $i, 'and value is:', $arr[$i], '<br/>';
	}
?>
```
        
## while配合each和list遍历数组
while实在外部定义边界条件，如果要实现可以和for循环。
         
each函数的使用：each能够从一个数组中国获取当前数组指针所指向的元素的下标和值，拿到之后将数组指针下移，同时将拿到的元素下标和值以一个四个元素的数组返回：
- 0下标：取得元素的下标值
- 1下标：取得元素的值
- key下标：取得元素的下标值
- value下标：取得元素的值
        
如果each取不到结果（数组指针移动到最后），返回false。
      
代码示例：     
        
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/17
	 * Time: 下午 11:39
	 * Features: while配合each和list遍历数组
	 */

	// while配合each和list遍历数组
	$arr = array(1, 'name' => 'Tom', 3, 'age' => 30);
	echo '<pre>';
	// each函数指针操作
	print_r(each($arr));
	print_r(each($arr));
?>
```
       
list函数使用：list是一种结构，不止一种函数（没有返回值），是list提供一堆变量去从一个数组中取得元素值，然后依次存放到对应的变量当中（批量为变量赋值：值来源于数组）：list必须从索引数组中去获取数据，而且必须从0开始。
       
**错误操作：变量多于数组元素，没有指定从0到指定变量的下标的数组元素**
      
list与each配合特别好：each一定有两个元素就是0和1下标元素
      
```
list(变量1,变量2)=each(数组);   //是一种赋值运算，但是可以的到false结果（each取不到正确的结果），整个表达式为false
```
        
代码示例：    
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/17
	 * Time: 下午 11:39
	 * Features: while配合each和list遍历数组
	 */

	// while配合each和list遍历数组

	// while循环
	$arr = array(1, 'name' => 'Tom', 3, 'age' => 30);

	while (list($key, $value) = each($arr)) {
		//list搭配each
		// list($key, $value) = each($arr);
		//输出
		echo 'key is:' . $key . 'value is :' . $value . '<br/>';
	}
?>
```
       
## 数组的相关函数
1. 排序函数：对数组元素进行排序，都是按照ASCII码进行比较，可以进行英文比较。
- `sort()`:顺序排序(下标重排)
- `rsort()`:逆序排序
- `asort()`:顺序排序（下标保留）
- `arsort()`:逆序排序
- `ksort()`:顺序排序
- `krsort()`:逆序排序：按照键名（下标）
- `shuffle()`:随机打乱数组元素，数组下标会重排。
          
代码示例：    
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/18
	 * Time: 下午 9:46
	 * Features: 数组排序
	 */

	//排序函数
	$arr = array(3, 1, 5, 2, 0);
	echo '<pre>';

	sort($arr);
	print_r($arr);
	echo '<hr>';

	$arr1 = array(3, 1, 5, 2, 0);
	asort($arr1);
	print_r($arr1);

	echo '<hr>';
	$arr3 = array(3, 1, 5, 2, 0);
	krsort($arr3);
	print_r($arr3);

	echo '<hr>';
	$arr4 = array(3, 1, 5, 2, 0);
	shuffle($arr4);
	print_r($arr4);
	shuffle($arr4);
	print_r($arr4);
?>
```
       
2. 指针函数
- `reset()`:重置指针，将数组指针回到首位
- `end()`:重置指针，将数组指针指导到最后一个元素
- `next()`:指针下移，取得下一个元素的值
- `prev()`:指针上移，取得上一个元素的值
- `current()`:获取当前指针对应的元素值
- `key()`:获取当前指针对应的下标值
            
代码示例：    
     
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/18
	 * Time: 下午 9:46
	 * Features: 指针函数
	 */

	//指针函数
	$arr = array(3, 1, 5, 2, 0);
	echo '<pre>';

	echo current($arr), '<br/>';
	echo key($arr), '<br/>';

	echo next($arr), next($arr), '<br/>';
	echo prev($arr), '<br/>';

	echo end($arr), '<br/>';
	echo reset($arr), '<br/>';
?>
```
       
**注意事项**：next和prev会移动指针，有可能导致指针移动到最前或者最后（离开数组），导致数组不能使用，通过next和prev不能回到正确的指针位置。只能通过end或者reset进行指针重置。
       
3. 其他函数
- `count()`:统计数组中元素的数量
- `array_push()`:从数组中加入一个元素（数组后面）
- `array_pop()`:从数组中移除一个元素（数组后面）
- `array_shift()`:从数组中去除一个元素（数组前面）
- `array_unshift()`:从数组中加入一个元素（数组前面）
- `array_reverse()`:数组元素反过来
- `in_array()`:判断一个元素在数组中是否存在
- `array_keys()`:获取一个数组的所有下标，返回一个索引数组
- `array_values()`:获取一个数组的所有值，返回一个索引数组
      
PHP模拟数据结构：
- 栈：压栈，先进后出（FILO）
- 队列：插队，先进先出（FIFO）
       
代码示例：    
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/18
	 * Time: 下午 9:46
	 * Features: 其他函数
	 */

	//其他函数

	// 模拟数据结构：栈和队列
	$arr = array();

	//栈：先压栈后出栈：都是从一端出来
	// 前面：array_shift和array_unshift
	// 后面：array_push和array_pop
	// 压栈
	array_push($arr, 3);
	array_push($arr, 2);
	array_push($arr, 1);
	print_r($arr);

	// 出栈
	echo array_pop($arr), array_pop($arr), array_pop($arr), '<br/>';


	// 队列：先排队，先出来，一端进，另外一端出
	//后进前出:array_push和array_shift
	//前进后出:array_unshift和arrap_pop
	$arr = array();

	// 入队
	array_unshift($arr, 3);
	array_unshift($arr, 2);
	array_unshift($arr, 1);
	print_r($arr);
	// 出队
	echo array_pop($arr), array_pop($arr), array_pop($arr), '<br/>';

	$arr = array(1, 2, 3, 6, 5);
	print_r(array_reverse($arr));

	var_dump(in_array(100, $arr));
	var_dump(in_array(1, $arr));

	print_r(array_keys($arr));
	print_r(array_values($arr));
?>
```
      
# 编程思想
>编程思想：如何利用数学模式，来解决对应的需求问题；然后利用代码实现对应的数据模型（逻辑）   
>算法：使用代码实现对应的数学模型，从而解决对应的业务问题。
        
## 递推算法
>递推算法是一种简单的算法，即通过已知条件，利用特定关系得出中间推论，直到得到结果的算法。递推算法分为顺推和逆推两种。
        
- 顺推：通过最简单的条件（已知），然后逐步推演结果。
       
- 逆推：通过结果找到规律，然后推到已知条件。
      
代码示例：     
        
**斐波那契数列**
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/20
	 * Time: 下午 8:06
	 * Features: 递推思想
	 */

	// 递推思想（算法）
	// 需求：规律 1 1 2 3 5
	// 求出指定位数对应的值

	

	function my_recursive($des)
	{
		//判断：如果为第一个或者第二个
		if ($des == 1 || $des == 2)
			return 1;
		// 开始计算
		$f[1] = 1;
		$f[2] = 1;    //如果想要第一个或者第二个结果，那么可以直接给出
		for ($i = 3; $i <= $des; $i++) {
			$f[$i] = $f[$i - 1] + $f[$i - 2];
		}
		//返回最后一个位置的结果
		return $f[$des];
	}

	echo my_recursive(15);
?>
```

## 递归算法
>递归算法是把问题转化为规模缩小了的同类问题的子问题。然后递归调用函数（或过程）来表示问题的解。
1. 简化问题：找到最有子问题（不能再小）
2. 函数自己调用自己

递归思想中：有两个非常重要的点
- 递归点：发现当前问题可以有解决当前问题的函数，去解决规模比当前小一点的问题来解决

- 递归出口：当问题解决的时候，已经到达（必须有）最优子问题，不能再次调用函数
如果一个函数递归调用自己而没有递归出口：就是死循环。
        
递归的本质：是函数调用函数：一个函数需要开辟一块内存空间，递归会出现同时调用N多个函数（自己）：递归的本质就是利用空间换时间。
      
代码示例：   
      
**斐波那契数列**
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/20
	 * Time: 下午 8:28
	 * Features: 递归思想
	 */

	// 递归思想

	// 递归一定有函数
	function recursion($n)
	{
		//递归出口
		if ($n == 1 || $n == 2)
			return 1;
		//递归点：求N的值，与求N-1得值一模一样，只是N-1的规模比N小
		return recursion($n - 1) + recursion($n - 2);
	}

	//调用
	echo recursion(15);
?>
```
      
## 数组排序算法
### 冒泡排序
>冒泡排序（Bubble Sort），是一种计算机科学领域的较简单的排序算法。
>它重复地走访过要排序地数列，一次比较两个元素，如果他们的顺序错误就把他们交换过来。
>走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。
       
冒泡排序地算法思路：
1. 比较相邻地元素。如果第一个比第二个大，就交换他们两个。
2. 对每一对元素做同样的工作，从开始第一对到结尾的最后一对。在这一点，最后的元素应该会是最大的数。
3. 针对所有的元素重复以上的步骤，除了最后一个。
4. 持续每次对越来越少的元素重复上面的步骤，直到没有任何一堆数字需要比较。
      
代码示例：
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/22
	 * Time: 下午 4:00
	 * Features: 冒泡排序
	 */

	// 冒泡排序

	$arr = array(1, 4, 2, 9, 7, 5, 8);
	//2. 想办法让下面可以每次找出最大值的代码重复执行
	for ($i = 0, $len = count($arr); $i < $len; $i++) {
		// 1. 想办法将最大的值放到最右边去
		for ($j = 0, $len = count($arr); $j < $len - 1 - $i; $j++) {
			//判断：两两相比
			if ($arr[$j] > $arr[$j + 1]) {
				//左边比右边大：交换
				$temp = $arr[$j];
				$arr[$j] = $arr[$j + 1];
				$arr[$j + 1] = $temp;
			}
		}
	}


	echo '<pre>';
	print_r($arr);
?>
```
      
### 选择排序
>选择排序（Selection sort）是一种简单直观的排序算法。它的工作原理是每一次从待排序的数据元素中选出最小（或最大）的一个元素，存放到序列的起始位置，直到全部待排序的数据元素拍完。选择排序是不稳定的排序方法（比如序列[5,5,3]第一次就将第一个[5]与[3]交换，导致第一个5挪动到第二个5后面）
       
选择排序的算法思路：
1. 假设第一个元素为最小元素，记下下标
2. 寻找右侧剩余的元素，如果有更小的，重新记下最新的下标
3. 如果有新的最小的，交换两个元素。
4. 往右重复以上步骤，直到元素本身是最后一个。
       
代码示例：    
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/22
	 * Time: 下午 4:25
	 * Features: 选择排序
	 */

	// 选择排序

	$arr = array(1, 5, 2, 9, 6, 3, 4);

	// 1. 确定要交换多少次：依次只能找到一个最小的，需要找数组长度对应的次数
	for ($i = 0, $len = count($arr); $i < $len; $i++) {
		// 2. 假设当前第一个已经排好序
		$min = $i;    //当前第一个数是最小的
		//3. 拿该最小的去比较剩余的其他
		for ($j = $i + 1; $j < $len; $j++) {
			//4. 比较：比较当前元素与选定的最小的元素
			if ($arr[$j] < $arr[$min]) {
				//说明当前指定的$min不合适
				$min = $j;
			}
		}

		//5. 交换当前选定的值与实际最小的元素值
		if ($min != $i) {
			$temp = $arr[$i];
			$arr[$i] = $arr[$min];
			$arr[$min] = $temp;
		}
	}

	echo '<pre>';
	print_r($arr);
?>
```
       
### 插入排序
>插入排序（Insert sort），插入排序的基本操作就是将一个数据插入到已经排好序的有序数据中，从而得到一个新的、个数加一的有序数据，算法适用于少量数据的排序，是稳定的排序方法。插入算法把排序的数组分成两部分：第一部分包含了这个数组的所有元素，但将最后一个元素除外（让数组多一个空间才有插入的位置），而第二部分就只包含这一i个元素（即待插入元素）。在第一部分排序完成后，再将这个最后元素插入到已排好序的第一部分中。
       
插入排序的基本思想是：每步将一个待排序的记录，按其关键码值得大小插入前面已经排序的文件中适当位置上，直到全部插入完为止。
        
插入排序的算法思路： 
1. 设置监视哨r[0]，将待插入记录的值赋值给r[0]。
2. 设置开始查找的位置。
3. 在数组中进行搜索，搜索中将第j个记录后移，直至r[0].key>=r[j].key为止；
4. 将r[0]插入r[j+1]的位置上。
       
代码示例：     
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/23
	 * Time: 下午 1:32
	 * Features: 插入排序
	 */
	// 插入排序
	$arr = array(4, 2, 6, 8, 9, 5);

	//1. 确定要插入多少回（假设一个数组一次性插入到对的位置，同时第一个位置是假设对的）
	for ($i = 1, $len = count($arr); $i < $len; $i++) {
		// 2. 取出当前要插入的元素的值
		$temp = $arr[$i];

		//标记：默认说明当前要插入的数组的位置是对的
		$change = false;
		//3. 让该数据与前面已经排好序的数组元素重复比较（挨个比较），直到的位置（）交换
		for ($j = $i - 1; $j >= 0; $j--) {
			// 4. 比较
			if ($arr[$j] > $temp) {
				//说明当前要插入的元素，比前面的已经排好序的元素的值要小：交换位置
				$arr[$j + 1] = $arr[$j];
				//说明前面顺序的数组元素有不合适的位置
				$change = true;
			} else {
				//说明当前待插入元素，比前面的元素要打：说明位置正确
				break;
			}
		}

		//判断位置需要变动
		if ($change) {
			//有数据移动，占错位置了
			$arr[$j + 1] = $temp;
		}
	}

	echo '<pre>';
	print_r($arr);
?>
```
       
### 快速排序
>快速排序（Quicksort）是对冒泡排序的一种改进。通过一趟排序将要排序的数据分割成独立的两部分，其中一部分的所有数据都比另外一部分的所有数据都要小，然后再按此方法对这两部分数据分别进行快速排序，整个排序过程可以递归进行，以此达到整个数据编程有序序列。（递归）
           
设要排序的数组是A[0]......A[N-1]，首先任意选取一个数据（通常选用数组的第一个数）作为关键数据，然后将所有比它小的数据放到他前面，所有比它大的数都放到它后面，这个过程称为一趟快速排序。值得注意的是，快速排序不是一种稳定的排序算法，也就是说，多个相同的值的相对位置也许会在算法结束时产生变动。

快速排序的算法是：
1. 从数组中选出一个元素（通常第一个），作为参照对象。
2. 定义两个数组，将目标数组中剩余的元素与参照元素挨个比较：小的放到一个数组，大的放到另外一个数组。
3. 第二步执行完之后，前后的数组顺序不确定，但是确定了自己的位置。
4. 将得到的小数组按照第1到第3步重复操作（子问题）。
5. 回溯最小数组（一个元素）。
      
代码示例：      
        
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/23
	 * Time: 下午 4:20
	 * Features: 快速排序
	 */

	// 快速排序
	$arr = array(5, 6, 3, 4, 9, 2, 7, 8);

	//快速排序
	function quickSort($array)
	{
		if (!isset($array[1]))
			return $array;
		$mid = $array[0]; //获取一个用于分割的关键字，一般是首个元素
		$leftArray = array();
		$rightArray = array();

		foreach ($array as $v) {
			if ($v > $mid)
				$rightArray[] = $v;  //把比$mid大的数放到一个数组里
			if ($v < $mid)
				$leftArray[] = $v;   //把比$mid小的数放到另一个数组里
		}

		$leftArray = quickSort($leftArray); //把比较小的数组再一次进行分割
		$leftArray[] = $mid;        //把分割的元素加到小的数组后面，不能忘了它哦

		$rightArray = quickSort($rightArray);  //把比较大的数组再一次进行分割
		return array_merge($leftArray, $rightArray);  //组合两个结果
	}

	echo '<pre>';
	print_r(quickSort($arr));
?>
```
        
### 归并排序
>归并排序（MERGE-SORT）是建立在归并操作上的一种有效的排序算法，该算法是采用分治法（Divide and Conquer）的一个非常典型的应用。将已有序的子序列合并，得到完全有序的序列；即显示每个子序列有序，再使子序列段间有序。若将两个有序表合并成一个有序表，称为二路归并。
       
二路归并实现：
        
代码示例：    
        
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/23
	 * Time: 下午 10:15
	 * Features: 归并排序
	 */
	// 归并排序

	// 二路归并
	$arr1 = array(1, 3, 5);
	$arr2 = array(2, 4, 6);

	//取出一个空数组用于归并空间
	$arr3 = array();
	while (count($arr1) && count($arr2)) {
		//只要$arr1和$arr2里面还有元素，就进行循环
		//取出每个数组的第一个元素：进行比较
		$arr3[] = $arr1[0] < $arr2[0] ? array_shift($arr1) : array_shift($arr2);
	}
	//合并结果
	print_r(array_merge($arr3, $arr1, $arr2));
?>
```
           
归并排序的算法是： 
1. 将数组拆分成两个数组
2. 重复步骤1将数组拆分成最小单元
3. 申请空间，使其大小为两个已经排序序列之和，该空间用来存放合并后的序列
4. 设定两个指针，最初位置分别为两个已经排序序列的起始位置
5. 比较两个指针所指向的元素，选择相对小的元素放入到合并空间，并移动指针到下一位置
6. 重复步骤3直到某一指针超出序列尾
7. 将另一序列剩下的所有元素直接复制到合并序列尾
        
代码示例：     
      
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/23
	 * Time: 下午 10:15
	 * Features: 归并排序
	 */
	// 归并排序
	$arr = array(4, 7, 2, 1, 5, 9, 3);

	//归并排序
	function merge_sort($arr)
	{
		//递归出口
		$len = count($arr);
		if ($len <= 1)
			return $arr;

		//拆分
		$middle = floor($len / 2);
		$left = array_slice($arr, 0, $middle);
		$right = array_slice($arr, $middle);

		//递归点：$left和$right都没有排好序：而且可能是多个元素的数组
		$left = merge_sort($left);
		$right = merge_sort($right);

		//假设左边和右边都已经排好序：二路归并
		//取出一个空数组用于归并空间
		$arr3 = array();
		while (count($left) && count($right)) {
			//只要$arr1和$arr2里面还有元素，就进行循环
			//取出每个数组的第一个元素：进行比较
			$arr3[] = $left[0] < $right[0] ? array_shift($left) : array_shift($right);
		}
		//合并结果
		return array_merge($arr3, $left, $right);
	}

	print_r(merge_sort($arr));
?>
```
        
### 查找算法
#### 查找算法含义
>查找是在大量的信息中寻找一个特定的信息元素，在计算机应用中，查找是常用的基本运算。查找算法是指实现查找过程对应的代码结。就是中大型数组中去快速定位想要的元素。
        
#### 顺序查找算法
>顺序查找也称为线性查找，从数据结构线性表的一段开始，顺序扫描，依次将扫描到的结点关键字与给定值k相比较，若相等则表示查找成功；若扫描结束仍没有找到关键字等于k的节点，表示查找失败。
        
代码示例：     
       
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/23
	 * Time: 下午 10:52
	 * Features: 查找算法
	 */

	// 查找算法

	// 顺序查找

	$arr = array(1, 3, 6, 8, 23, 68, 100);

	// 顺序查找
	function check_order($arr, $num)
	{
		//全部匹配
		for ($i = 0, $len = count($arr); $i < $len; $i++) {
			//判断
			if ($arr[$i] == $num) {
				return $i;
			}
		}

		return false;
	}

	var_dump(check_order($arr, 7));
?>
```
       
#### 二分查找算法
>二分查找要求线性表中的节点按关键字值升序或降序排列，用给定值k先与中间节点的关键字比较，中间结点把线形表分为两个子表，若相等则查找成功；若不想等，再根据k与该中间节点关键字的比较结果确定下一步查找那个子表，这样递归进行，直到查找到或查找结束发现表中没有这样的结点。 
        
二分查找算法思路：     
1. 计算数组长度
2. 确定左右两边的指针位置
3. 找到中间位置
4. 匹配
5. 然后根据大小重定边界
        
代码示例：     
        
```php
<?php


	/*
	 * Create by PhpStorm
	 * Author: Yan
	 * Date: 2019/8/23
	 * Time: 下午 10:52
	 * Features: 查找算法
	 */

	// 查找算法

	$arr = array(1, 3, 6, 8, 7, 7, 23, 68, 100);

	//二分查找算法
	function check_break($arr, $res)
	{
		//1. 得到数组边界
		$right = count($arr);
		$left = 0;
		// 2. 循环匹配
		while ($left <= $right) {
			//3. 得到中间位置
			$middle = floor(($right + $left) / 2);

			//匹配数据
			if ($arr[$middle] == $res) {
				return $middle + 1;
			}

			//5. 没有找到
			if ($arr[$middle] < $res) {
				//值在右边
				$left = $middle + 1;
			} else {
				//值在左边
				$right = $middle - 1;
			}

		}
		return false;
	}

	var_dump(check_break($arr, 0));
?>
```
        
# 待续