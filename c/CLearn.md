## 内存
```txt
64位计算机 => 地址总线64 => 64字节寻址

高12位 => 系统内核使用
低48位 => 用户程序使用 => 用户程序寻址空间为 0x000000000000~0xffffffffffff 12位16进制

内存：
+++++++++++++
+  系统内核  
+++++++++++++
+   栈              ------------从高位分配 <= 从低位调用
+++++++++++++
+   自
+   由
+   分
+   配
+   区域
+++++++++++++
+   堆              ------------方法区
+++++++++++++
+  常量区            ------------static，global
+++++++++++++
+  代码区            ------------从低位分配, 地址与程序中分配顺序不同 <= 编译器优化
+++++++++++++

若打印地址 => "0x123456789ABC" => 12个16进制 => 48位字节 => 位于用户程序区
```

## 指针-内存
```txt
int *p
p++ => int4字节 => p++向后移动4字节
p+=3 => int4字节 => p+=3向后移动12字节
```
```txt
若定义char[]，然后输入str，若超出预设空间，会覆盖掉后面的地址空间
```

## 预处理
```txt
编译过程：
.c 预处理=> .i 编译=>.s 汇编=> .o 链接=> 可执行

预处理：.i仍是C语法
1.展开头文件
2.宏替换 
#define R 10
宏替换就是单纯的字符串替换，不考虑语法

宏参数替换 => #define N(n) n*10

预处理宏替换只是字符串替换，不会执行计算

宏替换的参数相当于泛型T，无参数类型要求
```

## typedef
```txt
typedef int xxx;
为类型换别名

可以为结构体定义别名

typedef struct stu{
}别名;
```

## 结构体
```txt
struct name{

定义结构体别名：
1. struct nama name_1;

2. struct name{
}name_1

3. struct {
}name_1


初始化
1. struct name name_1 = {"",""...}

2. 结构体数组
struct name name_2[2] = {{"",""},{"",....}}

结构体指针
struct name *p;
p = name_2;
此时p指向的是数组的第一个元素
```

## 公用体 联合体 union
```txt
union data{
成员1，
成员2，
成员3
}

同一时刻只能有一个union的成员，共享同一内存地址，取最后一次赋值的成员值

内存长度，为所占长度最长的那个元素的空间 <= 字节对齐，空间换时间，快速读取 => 字节对齐：偏移量+值+填充字节
```

## 动态数据结构
```txt
链表

struct links {
    int  
    int 
    struct links *next;
};

struct links a,b,c, *head;

// 赋值
...

// 链接
head = &a;
a.next = &b;

// 循环
struct links *p;
p = head;
while( p != null){
...
p = p->next;
}
```

### 动态链表
```txt
分配内存

#include <malloc.h>

struct links * p;

p = (struct links*)malloc(sizeof(struct links))

```

## 位运算
```txt
时间复杂度 == 加法

根据二进制位进行运算 => 补码，逐位逻辑运算

&
|
^
<<
>>

```

## 文件引入
```txt
#include "xxx.c" => 相当于把xxx.c全写进来

=> 头文件和函数分离：
#include xxx.o (机器码) => 引入编译后的文件 => 生成静态库，将不常改动的编译好

.h => 放入声明文件(类似于接口) 实际执行的文件在.c=>.o里面，   .h可以用来做说明

避免重复引入导致的冲突

```

## return
```txt
main的return 0 可以用来流程控制
只有运行成功 echo $main == 0 
若返回其他值，则说明程序运行失败 
```

## main参数
```txt
int main(int argv,char* args)
```

## for循环
```txt
int i;
for(i=0;i<n;i++)
旧版本gcc需要定义在外部
```


## 标准IO流
```txt
std

stdio.h
stdin.h
stdout.h
stderr.h

linux所有设备都是文件，都视为文件操作

printf是对fprintf的封装，默认为标准输入流（键盘）
scanf是对fscanf的封装，默认标准输出流

```

## 重定向
```txt
>>
<<
```

## 管道
```txt
| 管道符
```


















