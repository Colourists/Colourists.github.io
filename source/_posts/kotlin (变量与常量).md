---
title: Kotlin变量与常量
top: false
date: 2019-07-03 16:44:10
tags: kotlin
category: android

---



# 变量与常量

和`java`不一样`kotlin`是变量名在前类型在后,有点不适应

**常量 (不可改变)**一旦赋值就不可改变,使用`val`关键字

```kotlin
val a: Int = 1
val b = 1   // 自动推断 Int 类型
val c: Int  // 没有提供初始值，必须声明类型
c = 1       // 延迟赋值
```

**变量(可以动态改变的)**使用`var`关键字

```kotlin
var x = 5 // 自动推断 Int 类型
x += 1
```

同时有一个额要注意的点是,类的属性是必须初始化的,不能延迟赋值除非将这个属性变为抽象的

![抽象的](https://raw.githubusercontent.com/Colourists/Cloud-picture/master/android/form/20190703171924.png)

![报错](C:\Users\Thinkpad\AppData\Roaming\Typora\typora-user-images\1562145624289.png)



大家可能会发现一个问题,在`java`中我们都会使用可见性修饰符去修饰属性,但是在`kotlin`却没有出现,那是因为`java`默认是`protected`但是`kotlin`默认是`publish`的

# 字符串

在`java`中如果我们想在`TextView`中输入设置我们就需要这样设置

```java
int i = 0;
text.setText(i+"");
```

在`Kotlin`中

```
var i: Int = 0;
text.text = "$i";
```



