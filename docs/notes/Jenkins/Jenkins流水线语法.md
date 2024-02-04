# 1. Jenkins 流水线语法
## 声明式流水线
声明式Pipleine是官方推荐的语法。所有的声明式Pipeline都必须包含一个 pipeline块中，比如：
```Jenkinsfile
pipeline {
    //run
}
```

在声明式Pipeline中的基本语句和表达式遵循Groovy的语法。但是有以下例外：
- 流水线顶层必须是一个块，特别是pipeline{}。
- 不需要分号作为分割符，是按照行分割的。
- 语句块只能由阶段、指令、步骤、赋值语句组成。例如: input被视为input()。
