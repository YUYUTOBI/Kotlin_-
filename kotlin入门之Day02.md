# kotlin入门之Day02

## for循环和foreach循环以及区间的定义

```kotlin
//注意:foreach循环无法使用break和contine
//区间的反向方法100 downTo  1
//区间的反转方法IntRange.reversed()
fun main(args: Array<String>) {
    //区间的定义方式一(整型区间)
    val q=IntRange(1,100)
    //区间的定义方式二(长整型区间)
    val  e=1L.rangeTo(100L)
    //区间的定义方式三(字符区间)
    val f='A'..'Z'
    //普通for循环
    for (i in q) {
        println(i)
    }
    //普通for循环之角标
    for ((index,c) in e.withIndex()) {
        println("index=$index c=$c")
    }
    //增强for循环
    f.forEach {
        println(it)
    }
    //增强for循环之角标
    e.forEachIndexed { index, l ->
        println("index='$index l=$l ")
    }

}
```

## 数组

```kotlin
var arr= arrayOf(1,2,3,4,5,6) //定义数组
    arr.forEach {//遍历数组
        println(it)
    }
    println(arr[3])//数组的访问
      arr[3]= 8
    println(arr[3])//数组的修改
    arr.set(3,9)//调用方法修改指定角标下的值
    println(arr[3])
    var arr1= arrayOf("张三,李四,王五,刘六,小七,腊八")
    arr1.indexOf("张三")//查找第一个值的角标
    arr1.indexOfLast {
        it.equals("王五")//查找最后一个值的角标
    }
    arr1.indexOfFirst {
        it.startsWith("刘")//查找包含第一个值的角标
    }
    arr1.indexOfLast {
        it.startsWith("张")//查找包含最后一个值的角标
    }
```

## 尾递归

![1533736270307](D:\GitHub\Kotlin---Doy01\1533736270307.png)

## 运算符的重载

```kotlin
var name:String="张三"
private set//外部限制修改
var age:Int=18
set(value) {//自定义访问器
    if(value>18&&value<30){
        field=value//field去访问当前值
    }
}
override fun toString(): String {
    return "Girl(name='$name', age=$age)"
}//运算符的重载方法
operator fun plus(Girl:Girl):Int{//为了系统识别重载方法，前面需要加一个operator关键字
    return age+Girl.age
```

![1533736532693](D:\GitHub\Kotlin---Doy01\1533736532693.png)

## 类成员的访问设置

```kotlin
class ps{
    var  name="张三"
    private set//把name的set方法去掉限制访问，只能访问无法修改
  private var  age=20//私有该属性，既不能访问也不能修改
}
```

## 自定义类成员访问器

```kotlin
class person{
    var name="李四"
    var age=20
    set(value:Int){
        if(value>18&&value<30){
            field=value//设置访问条件，最后用field表示当前方法修饰访问，否者就会递归栈内存溢出
        }
    }
}
```

## 直接访问主构函数的两种方式

```kotlin
//方式一
class person(name:String,age:Int){//主构函数
    var name=""
    var age=20
    init{//通过调用init方法来设置访问，是根据JAVA来重写
        this.name=name
        this.age=age
    }
}
//方式二
class person(var name:String,var age:Int){//直接用var和val来修饰系统自动生成访问方法，这种方法使用广泛,只有主构造函数才能用var和val修饰
}
```

## 次构函数的定义和之间的调用以及次构函数的使用

```kotlin
class person(var name:String,var age:Int){//主构函数直接声明
    var phone=""//次构函数声明
    var QQ=""
    constructor(name:String,age:Int,phone:String):this(name,age)//次构函数的定义，用construction修饰，次函数必须继承主函数
    constructor(name:String,age:Int,phone:String,QQ:String)this(name,age,phone)//次构函数之间可以直接继承主函数也可以间接继承主函数
    this.phone=phone
    this.QQ=QQ//次构函数必须声明变量来存储值，否则无法使用
}//init方法优先于次构执行
```

## 面向对象之封装以及继承

封装：隐藏内部实现的细节，只保留功能接口,用private修饰封装

继承时需要继承什么就在父类上用open修饰，在有具体成员下使用,子类要加（）使用

```kotlin
open class fu{//继承声明
   open var name="小头爸爸"
   open var age=40
   open fun hello(){
        println("hello")
    }   
}
class zi:fu(){//继承父类
    override var name:String="大头儿子"
    override var age:Int=20
    override fun hello(){
        println("hahaha")
    }
}
```

## 构造函数继承

```kotlin
open class fu(var name:String,var age:Int){//主构造函数声明参数和继承声明
    open fun hello(){//继承方法
        printin("hello")
    }
}
class zi(name:String,age:Int):fu(name,age)//子类继承必须重写参数来继承，然后回调给父类
```

## 抽象类和接口

抽象类是实物的本质，只能单继承，用abstract修饰

接口是实物的能力，可以多实现，用interface修饰

接口中成员不能直接赋值，方法可以直接实现，继承类可以重写