---
layout:     post
title:      "非常水的Java笔记"
subtitle:   
date:       2018-07-3
author:     "Ljan"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - Java
---

> This document is not completed and will be updated anytime.

lamda表达式 匿名的函数式接口实现，是一个匿名对象。不需要接口名，仅需要输入参数，方法体，返回值。lamda表达式的参数类型可以不指定，而由编译器根据上下文推导。方法引用就是用其他类中已经定义好的方法作为lamda表达式。方法引用的优点是不需要创建拥有这个方法的类的实例。

自定义一个类加载器的的作用：执行代码前自动验证数字签名；根据用户的提供的密码解码代码；根据用户需求动态加载类；根据应用需求把其他数据的字节码加载到应用中。（一个例子：直接加载源码，先编译再运行）

equals()比较的是对象的内容，也就是JVM堆内存中的内容，==比较的是地址，也就是栈内存中的内容。

使用容器的remove和使用迭代器的remove，在迭代的过程中不能使用容器的remove可以使用自己的。详情要关注迭代器的实现原理

如果finally块中有return语句的话，它将覆盖掉函数中其他return语句。 

排序二叉树的定义

初始化过程：1. 初始化父类中的静态成员变量和静态代码块 ；2. 初始化子类中的静态成员变量和静态代码块 ；3.初始化父类的普通成员变量和代码块，再执行父类的构造方法；4.初始化子类的普通成员变量和代码块，再执行子类的构造方法；

方法区在JVM中也是一个非常重要的区域，它与堆一样，是被 线程共享 的区域。 在方法区中，存储了每个类的信息（包括类的名称、方法信息、字段信息）、静态变量、常量以及编译器编译后的代码等。大多数 JVM 将内存区域划分为 Method Area（Non-Heap）（方法区） ,Heap（堆） , Program Counter Register（程序计数器） ,   VM Stack（虚拟机栈，也有翻译成JAVA 方法栈的）,Native Method Stack  （ 本地方法栈 ），其中Method Area 和  Heap 是线程共享的  ，VM Stack，Native Method Stack  和Program Counter Register  是非线程共享的。为什么分为 线程共享和非线程共享的呢?请继续往下看。 首先我们熟悉一下一个一般性的 Java 程序的工作过程。一个 Java 源程序文件，会被编译为字节码文件（以 class 为扩展名），每个java程序都需要运行在自己的JVM上，然后告知 JVM 程序的运行入口，再被 JVM 通过字节码解释器加载运行。那么程序开始运行后，都是如何涉及到各内存区域的呢？ 概括地说来，JVM初始运行的时候都会分配好 Method Area（方法区） 和Heap（堆） ，而JVM 每遇到一个线程，就为其分配一个 Program Counter Register（程序计数器） ,   VM Stack（虚拟机栈）和Native Method Stack  （本地方法栈）， 当线程终止时，三者（虚拟机栈，本地方法栈和程序计数器）所占用的内存空间也会被释放掉。这也是为什么我把内存区域分为线程共享和非线程共享的原因，非线程共享的那三个区域的生命周期与所属线程相同，而线程共享的区域与JAVA程序运行的生命周期相同，所以这也是系统垃圾回收的场所只发生在线程共享的区域（实际上对大部分虚拟机来说知发生在Heap上）的原因。

suspend() 和 resume() 方法：两个方法配套使用，suspend()使得线程进入阻塞状态，并且不会自动恢复，必须其对应的 resume() 被调用，才能使得线程重新进入可执行状态

方法的重写（override）两同两小一大原则：方法名相同，参数类型相同;子类返回类型小于等于父类方法返回类型，子类抛出异常小于等于父类方法抛出异常，子类访问权限大于等于父类方法访问权限。
