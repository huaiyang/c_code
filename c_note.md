# C语言学习笔记
-----------------

讲师：李慧芹


## C语言发展史 1:
1. 1960	原型A语言 -> ALGOL语言
1. 1963	CPL语言
1. 1967	BCPL
1. 1970 	B语言 -> 第一个Linux 版本 -> B语言+汇编
1. 1973 	C语言 -> 重编Linux版本

## C语言特点 2：
* 基础性语言
* 语法简洁，紧凑，方便，灵活
* 运算符，数据结构丰富
* 结构化，模块化编程
* 移植性好，执行效率高
* 允许直接对硬件操作，贴着硬件进行编程，如FPGA， DSP等

## C语言学习建议 3: 
* 概念的正确性
* 动手能力
* 阅读优秀的程序段，自己写+读优秀的程序段
* 大量练习，面试题

# C语言讲解思路 4：
* 基本概念
* 数据类型，运算符和表达式
* 输入输出专题
* 流程控制（顺序，选择，循环）
* 数组
* 指针
* 函数
* 构造类型
* 动态内存管理
* 调试工具和调试技巧（gdb,make）
* 常用的库函数

平台介绍： 64位的redhat6,vim,gcc(make)


``` c Hello world

#include <stdio.h>
#include <stdlib.h>
printf("Hellow World!/n") // "/n" 表示换行, 另外一个作用是刷新缓冲区
```
```shell hello.c:
C源文件-预处理-编译-汇编-链接-可执行文件
bill@Bill:~/data/c_code$ gcc -E hello.c > hello.i
bill@Bill:~/data/c_code$ gcc -S hello.i
bill@Bill:~/data/c_code$ ls
hello  hello.c  hello.i  hello.o  hello.s
bill@Bill:~/data/c_code$ rm -rf *
bill@Bill:~/data/c_code$ ls
hello.c
bill@Bill:~/data/c_code$ gcc -E hello.c > hello.i
bill@Bill:~/data/c_code$ ls
hello.c  hello.i
bill@Bill:~/data/c_code$ gcc -S hello.i
bill@Bill:~/data/c_code$ ls
hello.c  hello.i  hello.s
bill@Bill:~/data/c_code$ gcc -c hello.s
bill@Bill:~/data/c_code$ ls
hello.c  hello.i  hello.o  hello.s
bill@LAPTOP-PT0OMORD:~/data/c_code/c_code$ gcc hello.o -o hello
```
## 基本概念
1. 以helloworld为例对写程序的思路提出如下要求：
	* 头文件正确包含的重要性
	* 以函数为单位进行程序编写(只要是能独立出来的功能，就独立成小函数。)
	* 声明部分+实现部分
		全局的声明部分，函数的声明部分。
	* return 0; ->结束当前函数,给他的父进程看的
		exit 0; ->结束当前进程
	* 多用空格空行
	* 添加注释
1. C语言不识别二进制
   * 没有单位的数值是没有意义的
   * 计算机存储的二进制是补码形式
     * 正数的补码就是它二进制本身
     * 负数的补码是绝对值的二进制取反+1
       * 254(10) = 11111110(2) = 011 111 110 = 3 7 6 （8）= 1111 1110 = (F E)16
       * 254 -> unsigned int -> 32 
       * 254 什么都不带，默认是10进制， B11111110表示2进制，0376,以0开头表示8进制，0xFE表示16进制
2. 补码
	* 254 （11111110）unsigned int 32 = 24个零11111110
	* -254 -> 254 (11111110)
