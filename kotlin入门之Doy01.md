# kotlin入门之Doy01

## kotlin基本数据类型

![](

| 数据类型 | 占用字节    | 取值范围                                |
| -------- | ----------- | --------------------------------------- |
| Boolean  | 1byte       | true或false                             |
| Byte     | 1byte=8bit  | -128~127                                |
| Char     | 2byte       |                                         |
| Short    | 2byte=16bit | -32768~32767                            |
| Int      | 4byte       | -2147483648~2147483647                  |
| Float    | 4byte       | 精确到小数点后6位                       |
| Long     | 8byte       | 9223372036854775807~9223372036854775807 |
| Double   | 8byte       | 精确到小数点后15到16位                  |

)

## 定义变量之智能类型推断

```kotlin
var//可变变量
val//不可变变量
var i:Int=10//标准版
val a=10//简写推断版 
var i=a.toInt()//类型之间的强制类型转换
```

## 字符串中的各种方法和二元,三元元组

```kotlin
    var string :String="/哈哈哈哈ghghjhfghfhjgjd"
    var replaceAfter = string.substringAfter("h")//第一个指定元素截取
    println(replaceAfter)
    var substringAfterLast = string.substringAfterLast("h")//最后一个指定元素截取
    println(substringAfterLast)
    var substringBefore = string.substringBefore("h")//指定第一个元素结束
    println(substringBefore)
    var substringBeforeLast = string.substringBeforeLast("j")//指定最后一个元素结束
    println(substringBeforeLast)
    println("""Hello""")//原样输出字符串
    var b1 = replaceAfter ==replaceAfter//值比较
    println(b1)
    var b2 = substringBefore === substringAfterLast//地址值比较
    println(b2)
    readLine()//输入方法
    val b:Int?=null//可空类型
   // val z:String =null!!//非空类型
    println(b?.toByte()?:1)//Elvis操作符,需明确初始值
    var c=Pair("sdsahdajkdhajkdhaj","shdjkadgahhdg")//二元元组
    var d=Triple("shadasgdhj",'y',31723613)//三元元组
    var e=c.first//第一个元素
    var f=c.second//第二个元素
    var w=d.third//第三个元素
    
```

## 函数

![1533730113101](D:\课件与软件\区块链\Typora\bin\1533730113101.png)  

## if判断语句

```kotlin
if(a>b)a-b else b-a//有且只有一条执行语句时精简版
if(a<b){
    a-b
}else{
    b-a
}
```

