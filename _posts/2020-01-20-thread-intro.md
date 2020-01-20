---
layout: post
title:  "多线程简介"
date:   2020-01-20 15:46:29
categories: Java 多线程
excerpt: 多线程简介
---

* content
{:toc}

# 为什么需要多线程？

> Thread - 线程
> cycle - 时钟周期

* 现代CPU超级快，1个3GHz的CPU，1个时钟周期是0.3纳秒，而内存寻址时间大约是10微秒左右，远比CPU慢，磁盘、网络更慢
* 现代CPU是多核的，理论上具有天然的并发能力，可以同时做很多件事情
* Java的执行模型是同步/阻塞（block）的（这种容易被人类理解），在计算机做非常耗时的操作时（比如和数据库通信），希望同时能做些别的事情
* 默认情况下只有一个线程

# 多线程简介

在Java中最简单的但没有效率的创建一个线程的方法是：`new Tread()`
```java
public class Test {
    public static void main(String[] args) {
        new Thread(new Runnable() {
            @Override
            public void run() {
                fn();
            }
        });
    }
    private static void fn() {
    }
}
```

`alt+enter`可以简化为：
```java
public class Test {
    public static void main(String[] args) {
        new Thread(Test::fn);
    }
    private static void fn() {
    }
}
```

但现在还没有开始工作
```java
public class Test {
    public static void main(String[] args) {
        new Thread(Test::fn).start();
    }
    private static void fn() {
    }
}
```
添加`start()`，才开始启动。（不是`run()`，`start()`才能并发执行）

> 每当用start开启一个新线程的时候，就多了一个方法栈，方法栈里可以正常的像主线程一样执行方法的调用
>
> 方法栈（局部变量）是线程私有的，除了他，比如静态变量/类变量这些都是被所有线程共享的

# 多线程（难）问题的来源

> 线程难的本质原因是
>
> 你要看着同一份代码
>
> 想象不同的人在疯狂的以乱序执行他

对一个单核的CPU来说，线程1占用CPU开始做事情，若CPU分给他的时间到了（CPU的时间是由操作系统决定的，操作系统会决定每个线程/进程能够占用自己多长时间），一旦这个时间到了，CPU就强制终止这个线程，开始执行线程2。

虽然我们在宏观上看到不同的线程，每个线程同时在做事情，但他们自己的事情可以随时被CPU打乱。

可以多次执行下面的代码看看打印的结果
```java
public class Test {
    private static int i = 0;
    public static void main(String[] args) {
        for(int i = 0; i < 1000; i++) {
            new Thread(Test::modifySharedVariable).start();
        }
    }
    private static void modifySharedVariable() {
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        i++;
        System.out.println(i);
    }
}
```
打印出来`i`的结果并不完全和我们想的一样，并不完全是`0-1000`。

> 对于上面代码中的`i++`，他并不是一个原子操作（在多线程领域中，我们称一个事情在某个时刻只能被一个线程操作，他就是原子操作）
>
>`i++`在执行的时候，其实执行了3句，分别是`取i的值`、`把i的值加1`、`把修改后的值写回i`，如果1000个线程在同时操作`i++`，有可能发生下面的事情：
>
> 线程1：拿到i=0，然后i加1，这时候CPU给他的时间到了（此时i的值还是0），下面就开始执行线程2了
>
> 线程2：拿到i=0，然后i加1，最后把修改后的值写回i（此时i的值是1了），这时候他的时间到了，下面又开始执行线程1
>
> 线程1：刚才线程1已经执行了`取i的值，把i的值加1`，现在需要把修改后的值写回i，这时候i的值还是1了
>
> 两个线程执行完了，但这时候i的值还是1。（按我想的应该是2了）

问题所在：多个线程在同时访问一个共享变量的时候，由于这个变量不是原子的，以致于他的过程是乱序的，有可能是正常的，有可能是不正常的。这就是几乎所有多线程问题的来源。

# 对于什么场合适合使用多线程？

多线程的适用场景：

对于IO密集型应用极其有用
* 网络IO（通常包括数据库）
* 文件IO

对于CPU密集型（CPU intense）应用稍有折扣，多线程带来的提升有限

多线程带来的性能提升是否是无穷无尽的呢？上限在哪？：单核CPU达到100%，多核CPU达到N*100%。

# 线程安全

你要享用多线程的便利，你就要承担多个人同时操作一个对象带来的问题。

线程不安全的表现有：

表现1：
* 数据错误
    * i++（这个可以看上面的代码）
    * if-then-do（这个来看下面这个代码）
    
执行下面代码，看和你想象的一样吗？
```java
public class Test {
    private static Map<Integer, Integer> map = new HashMap<>();
    public static void main(String[] args) {
        for (int i = 0; i < 1000; i++) {
            new Thread(Test::putIfAbsent).start();
        }
    }
    private static void putIfAbsent() {
        try {
            Thread.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        // 随机生成一个1到10之间的数字，如果他不在map中，就把他加入map
        int r = new Random().nextInt(10);
        if (!map.containsKey(r)) {
            map.put(r, r);
            System.out.println(r);
        }
    }
}
```

我执行了2次，第一次正常打印了10个数字，第二次显示的是：
```
0
4
8
7
0
4
3
9
5
6
2
1
```
打印出来2个`0`，2个`4`，其他数字都只有1个。

> 线程1：随机生成了数字0，检查map里有没有0，检查之后发现没有0，duang，这时候CPU时间到了，挂起，开始执行线程2
>
> 线程2：随机生成了数字0，检查map里有没有0，检查之后发现没有0，把0放入map，执行完，这时候又继续线程1
>
> 线程1：从duang之后开始，把0放入map
>
> 这时候你就发现map里有了2个0......

表现2：
* 死锁

```java
public class Test {
    // Java中任何的对象都可以当做锁
    private static final Object lock1 = new Object();
    private static final Object lock2 = new Object();
    public static void main(String[] args) {
        new Thread1().start();
        new Thread2().start();
    }
    static class Thread1 extends Thread{
        @Override
        public void run(){
            synchronized (lock1){
                try {
                    Thread.sleep(500);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                synchronized (lock2){
                    System.out.println("123");
                }
            }
        }
    }
    static class Thread2 extends Thread{
        @Override
        public void run(){
            synchronized (lock2){
                try {
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                synchronized (lock1){
                    System.out.println("456");
                }
            }
        }
    }
}
```

main方法开始执行，开启新线程Thread1和Thread2，这2个线程几乎同时发生（Thread的创建是很快的）

这时，JVM里有3条线程：main、Thread1、Thread2

同一时刻，只有一个线程能拿到一把锁

Thread1获得lock1，然后sleep 500ms

Thread2获得lock2，然后sleep 100ms，100ms之后，Thread2要获得lock1，但是现在lock1在Thread1拿着，那么Thread2需要等着

等到Thread1 sleep了500ms，Thread1要去获得lock2，但是现在lock2在Thread2拿着，那么Thread1也要等着

死锁了......