---
layout: post
title:  "PID算法"
date:   2015-10-29 00:06:05
categories: 自动控制
excerpt: 算法介绍
---

* content
{:toc}

## PID简介

PID控制是目前工程上应用最广的一种控制方法，它的优点在于结构简单，且不依赖被控对象模型，控制所需的信息量也很少，因而非常易于工程实现，同时通过参数的调整也可获得较好的控制效果。
PID的三个参数——P（Proportional，比例）、I（Integration，积分）、D（Differentiation，微分）对时域响应的影响：

* P---将误差信号放大或缩小，产生控制作用，以减小误差；
* I---将误差不断累积，最终实现消除误差；
* D---获取误差的微分信息，反映偏差的变化趋势（变化率），能在系统产生大的误差变化前产生控制作用，从而加快系统的响应，减小调节时间。

框图如下图所示：
![pidScheme](http://zw-tech.com/blog/css/pics/pid_4.jpg)  
PID控制的是误差信号e(t) = r(t)-c(t)。PID控制律写成如下形式：
![1](http://zw-tech.com/blog/css/pics/pid_1.gif)
或
![2](http://zw-tech.com/blog/css/pics/pid_8.gif)

---

## 数字形式

在计算机控制系统中采用的是数字PID，因为计算机控制实际上是采样控制，用一系列采样点kT表示连续时间t，用和式代表积分，用增量代替微分。数字PID有两种控制方式：位置式PID控制和增量式PID控制。

---

* 位置式PID控制:![3](http://zw-tech.com/blog/css/pics/pid_5.gif)
* 增量式PID控制：![4](http://zw-tech.com/blog/css/pics/pid_6.gif)

---

* 位置式PID控制的输出与整个过去的状态有关，用的是误差的累加值；增量式PID的输出只与当前拍和前两拍的误差有关，因此，位置式PID控制的累积误差相对更大。

* 增量式PID的输出的是控制量增量，并无积分作用，因此，这种方法适用于执行机构带积分部件的对象。如步进电机；而位置式PID适用于执行机构不带积分环节的对象，如电液伺服阀。

* 增量式PID输出的是控制量增量，若计算机出现故障，误动作影响较小，而执行机构本身有记忆功能，可仍保持原位，不会严重影响系统的工作，而位置式的输出直接对应对象的输出，因此对系统影响较大。

---

## 算法流程

* 增量式PID算法流程：![5](http://zw-tech.com/blog/css/pics/pid_7.jpg)

* 位置式PID算法流程：![6](http://zw-tech.com/blog/css/pics/pid_2.jpg)