## kotlin基础之Day03

# 泛型

```kotlin
open class Box<T>(var thing:T)//定义泛型的第一种方式，在创建对象时指定泛型
class AppleBox(thing:Apple):Box<Apple>(thing)//定义泛型的第二种方式，创建泛型类指定泛型
class fuc<fruit>(thing:feuit):Box<fruit>(thing)//定义泛型的第三种方式，父类定义有泛型，子类不知道具体类型，还可以再传递一个泛型给它
fun <T>oppn(thing:T){//定义泛型函数
    when(thing){
        is Int->println("int类型")
        is String->println("字符串类型")
        is Char->println("字符类型")
        ...
    }
}  
class FruitBox<FRUIT:Fruit>(thing:FRUIT):Box<FRUIT>(thing)//泛型上限,在定义时确定泛型,继承多个子类,指定泛型只有其子类和其父类本身
@泛型类类型不一样,无法获取到泛型类型,就是泛型擦除;
inline fun<reified T>parse(thing:T):String{
    return T::class.java.name//不能获取泛型类型JAVA需要通过反射获取泛型类型
}//解决泛型擦除问题:1在泛型前面加上reified,2在泛型函数前加上inline
@泛型类型投射,在使用时定义泛型
fun parse(list:ArrayList<out Fruit>){//指定只能传递Fruit或者其子类
}//out 相当于JAVA的? extends
fun parse(list:ArrayList<in Fruit>){//指定只能传递Fruit或者其父类
}//in 相当于JAVA的? super
@星号投射
fun parse (list:Arraylist<*>){//可以传递任意东西
}
```

## 中缀表达式

函数前面加上infix

调用条件:1必须是成员函数和扩展函数;

​                 2必须只有一个参数

​                 3不能是可变参数 

注意:中缀表达式调用this不能省略

```kotlin
class Person(var name: String, var age: Int) {
    infix fun sayHelloTo(person: String) {
        println("$name 给$person 打招呼")
    }
```

## 类委托和属性委托

```kotlin
@静态代理委托
//第一种类委托方式,把洗碗的能力委托给了大头儿子实现
class SmallHeadFather:WashPower by BigHeadSon()

//第二种类委托  具备洗碗能力都可以
class SmallHeadFather(washPower: WashPower):WashPower by washPower//通过by 类名调用方法实现委托
@属性委托
class WeiQunMama{
    //存钱罐  专门存儿子的压岁钱
    var 儿子的压岁钱 = 0
    var 自己的存钱罐 = 0
    //委托的压岁钱的get方法
    operator fun getValue(bigHeadSon: BigHeadSon, property: KProperty<*>): Int {
        return 儿子的压岁钱
    }
    //委托的压岁钱set方法
    operator fun setValue(bigHeadSon: BigHeadSon, property: KProperty<*>, i: Int) {
        儿子的压岁钱 += 20
        自己的存钱罐 += i-20
    }
}
class BigHeadSon{
    //压岁钱  围裙妈妈帮你保存
    var 压岁钱:Int  by WeiQunMama()//通过by 类名重写get,set方法
}
```



