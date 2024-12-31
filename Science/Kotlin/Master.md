## 命令行参数处理
```kotlin
fun main(args: Array<String>) {  
    val parser = ArgParser("预清洗数据集")  
    val bench by parser.option(ArgType.String, shortName = "b", description = "数据集名称", ).default("santos_small")  
}
```
