---
title: "GeekTime Java核心技术要点"
date: 2019-12-19T11:27:51+08:00
categories: [
    "java",
    "development",
]
tags: [
    "java",
    "geektime"
]
---

## Java的执行流程
通常把Java执行分为编译期和运行时。

Java的编译是指通过Javac将Java源码编译为".class"文件里面的字节码。Java通过字节码和Java虚拟机(JVM)这种跨平台的抽象，屏蔽了操作系统和硬件的细节，实现“一次编译，到处执行”。

在运行时，JVM首先通过类加载器(Class-Loader)加载字节码，然后通过Java虚拟机(JVM)内置的解释器将字节码转换成最终的机器码执行。但常见的JVM还提供了JIT(Just-In-Time)编译器将热点字节码预先编译成机器码，这部分热点代码的执行属于编译执行，而不是解释执行（这点可以类比数据库和缓存，为了提高执行效率）。所以，主流的Java版本比如JDK8实际上是解释和编译混合的一种模式，即所谓的混合模式。
