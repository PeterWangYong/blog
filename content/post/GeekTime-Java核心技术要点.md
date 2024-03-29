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

Java的编译是指通过Javac将Java源码编译为 .class 文件里面的字节码。Java通过字节码和Java虚拟机(JVM)这种跨平台的抽象，屏蔽了操作系统和硬件的细节，实现“一次编译，到处执行”。

在运行时，JVM首先通过类加载器(Class-Loader)加载字节码，然后通过Java虚拟机(JVM)内置的解释器将字节码转换成最终的机器码执行。但常见的JVM还提供了JIT(Just-In-Time)编译器将热点字节码预先编译成机器码，这部分热点代码的执行属于编译执行，而不是解释执行（这点可以类比数据库和缓存，为了提高执行效率）。所以，主流的Java版本比如JDK8实际上是解释和编译混合的一种模式，即所谓的混合模式。

## String, StringBuffer, StringBuilder有什么区别？
String 是 Java 语言非常基础和重要的类，提供了构造和管理字符串的各种基本逻辑。它是典型的 Immutable 类，被声明成为 final class，所有属性也都是 final 的。也由于它的不可变性，类似拼接、裁剪字符串等动作，都会产生新的 String 对象。由于字符串操作的普遍性，所以相关操作的效率往往对应用性能有明显影响。

StringBuffer 是为解决上面提到拼接产生太多中间对象的问题而提供的一个类，我们可以用 append 或者 add 方法，把字符串添加到已有序列的末尾或者指定位置。StringBuffer 本质是一个线程安全的可修改字符序列，它保证了线程安全，也随之带来了额外的性能开销，所以除非有线程安全的需要，不然还是推荐使用它的后继者，也就是 StringBuilder。

StringBuilder 是 Java 1.5 中新增的，在能力上和 StringBuffer 没有本质区别，但是它去掉了线程安全的部分，有效减小了开销，是绝大部分情况下进行字符串拼接的首选。

