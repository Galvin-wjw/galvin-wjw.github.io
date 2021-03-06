---
layout:     post
title:      线性表（Linear List）
subtitle:   Linear List
date:       2019-02-21
author:     Galvin
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - Data Structure
--- 

#### Array
-  数组是一种线性表结构，以一组连续的内存空间存储相同的数据类型
- 下标以0开头是因为表示的是偏移量；base + i
- 动态扩容数组，是申请一块更大的连续空间，并且将原数据复制到新空间去

#### Linked List
* [LinkedList-Golang](https://github.com/Galvin-wjw/Golang-study/blob/master/Algorithm/linked-list.go)
* 链表通过指针将一片零散的内存块串联起来使用；连续空间不符合数组申请要求，会申请空间失败
* 链表随机访问需要根据指针遍历 O(n)
* 双向链表既有  prev 指针，也有next指针
* LRU（Least Recently Used）缓存淘汰算法
* 单链表反转：设置指针指向previos、current、current.next 节点

#### Stack
* 浏览器的前进后退，后进先出；数组或者链表实现
* 操作受限，只允许在一端操作数据
* 出栈时间复杂度O(1),入栈有可能空间不够，最差O(n)
* 栈在函数调用中的应用
    * 每进入一个函数，就会将临时变量作为一个栈帧入栈，当被调用函数执行完成，返回之后，将这个函数对应的栈帧出栈。
* 表达式求值
    * 一个栈存数字，另外一个存运算符
- 内存中的堆栈和数据结构堆栈不是一个概念，可以说内存中的堆栈是真实存在的物理区，数据结构中的堆栈是抽象的数据存储结构。
- 内存空间在逻辑上分为三部分：代码区、静态数据区和动态数据区，动态数据区又分为栈区和堆区。
    - 代码区：存储方法体的二进制代码。高级调度（作业调度）、中级调度（内存调度）、低级调度（进程调度）控制代码区执行代码的切换。
    - 静态数据区：存储全局变量、静态变量、常量，常量包括final修饰的常量和String常量。系统自动分配和回收。
    - 栈区：存储运行方法的形参、局部变量、返回值。由系统自动分配和回收。
    - 堆区：new一个对象的引用或地址存储在栈区，指向该对象存储在堆区中的真实数据。
- 为什么函数调用要用“栈”来保存临时变量呢？用其他数据结构不行吗？
    - 其实，我们不一定非要用栈来保存临时变量，只不过如果这个函数调用符合后进先出的特性，用栈这种数据结构来实现，是最顺理成章的选择。
    - 从调用函数进入被调用函数，对于数据来说，变化的是什么呢？是作用域。所以根本上，只要能保证每进入一个新的函数，都是一个新的作用域就可以。而要实现这个，用栈就非常方便。在进入被调用函数的时候，分配一段栈空间给这个函数的变量，在函数结束的时候，将栈顶复位，正好回到调用函数的作用域内。

#### Queue
* 先进先出，操作受限的线性表；数组或者链表实现
* head->队头；tail->队尾；队头出队，队尾入队
* tail=n（数组队列），整体移动数组tail-head长度到0位置
* 阻塞队列（生产者-消费者模型）
    * 为空，head取数据阻塞；直到有数据才能返回
    * 满，插入数据阻塞
* 线程安全的队列（并发队列）
    * 最简单直接的实现方式是直接在 enqueue()、dequeue() 方法上加锁，但是锁粒度大并发度会比较低，同一时刻仅允许一个存或者取操作。实际上，基于数组的循环队列，利用 CAS 原子操作，可以实现非常高效的并发队列。这也是循环队列比链式队列应用更加广泛的原因

