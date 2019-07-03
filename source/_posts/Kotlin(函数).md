---
title: Kotlin(函数)
top: false
date: 2019-07-03 17:56:30
tags: kotlin
category: android 
---

# Kotlin 的函数

## 简单实用

在`Kotlin`中定义函数的关键字是`fun`

```kotlin
fun sum(a: Int, b: Int): Int {
    return a + b
}
```

`Kotlin`的函数格式如下:

```kotlin
fun 函数名(参数名: 参数类型):返回值类型{
方法体
return 返回值
}
```

`Kotlin`中的函数没有返回值,`Unit`就和`java`中的`void`一样

```kotlin
fun printSum(a: Int, b: Int): Unit {

}
```

但是`Kotlin`中函数默认就是没有返回值的,所以`Unit`可以省略

```kotlin
fun printSum(a: Int, b: Int) {
   
}
```

**单一表达式含糊**表达式作为函数体,省略花括号,函数体在=后面,函数会自动推断返回值的类型

```Kotlin
fun sum(a: Int, b: Int) = a + b
//声明返回类型也行
fun double(x: Int): Int = x * 2
```





## 了解

### 重写和默认参数

在`Kotlin`中函数可以直接设置默认参数,默认值在类型后面直接使用=

```Kotlin
open class A {
    open fun foo(i: Int = 10) { ... }
}

class B : A() {
    override fun foo(i: Int) { ... } 
    // 因为继承自A的foo已经设置了默认值,所以B里的foo就不能再设置默认值了,他们会统一使用A的foo设置的默认值
}
```

[^1]: 如果函数里有多个参数,设置默认值的参数一定要放在后面

### 使用命名参数

当一个函数有大量参数时会非常实用,只输入需要改变的参数

```kotlin
//定义一个函数
fun get(j: Int, i: Int = 100, upperCaseFirstLetter: Boolean = true,
                 divideByCamelHumps: Boolean = false): Int {
        return i + j;
    }
```

这个函数中有默认值参数,也有没有默认值的参数我们可以这样调用

```Kotlin
var i1: Int = 5;
get(i1,upperCaseFirstLetter = false) // 只输入没有默认参数的和需要改变的参数upperCaseFirstLetter = false

get(i1)//全部使用默认的只输入没有默认的

```

## 可变参数`vararg`

函数的参数（通常是最后一个）可以用`vararg`修饰符标记:

```kOTLIN
 fun <T> asList(vararg ts: T): List<T> {
        val result = ArrayList<T>()
        for (t in ts) // ts is an Array
        result.add(t)
        return result
    }

val list = asList(1, 2, 3)

val list = asList(1, 2, 3,5,6)
```

允许输入不同位数的参数,在函数中，一个`T`类型的`vararg`参数被看成`T`的一个集合，即上面例子中的`ts`变量是`Array<out T>`类型的,

一个函数只能有一个参数被`vararg`标记,如果`vararg`参数不是最后一个的话，后面的参数的值可以使用命名参数语法传入，如果参数是函数类型，就需要在括号外传入lambda表达式

当我们调用一个`vararg`函数,我们可以一个一个的传入参数,也可以吧一个数组传入,使用`*`标记在参数前面加`*`

```KOTLIN

val a = arrayOf(1, 2, 3)
val list = asList(-1, 0, *a, 4)
```

