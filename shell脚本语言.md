---
title: shell脚本语言
date: 2017-03-15 11:45:36
tags: shell
categories : linux
---
参考链接[http://c.biancheng.net/cpp/shell/|shell脚本教程]([http://c.biancheng.net/cpp/shell/|shell脚本教程])
# shell脚本语言学习 
## hello world 
新建.sh文件，并给文件授权x权限。打开文件并在文件中输入以下代码\\ 
```
 #!/bin/bash
 echo "Hello World !"
```
第一行表示用/bin/bash来编译执行此文件，第二行表示在窗口输出“hello world！”
## 基本语法 
shell语言的语法和c语言类似，所以学起来还是比较容易理解。
## 变量
```
 #!/bin/bash
 i=1
 echo $i
```
  - 变量定义用等于号，中间没有空格。
  - 变量以大小写字母开头。
  - 变量引用用${变量}，{}可省略，最好不要省略。
## 运算符 
  - 表达式和运算符之间要有空格，例如 2+2 是不对的，必须写成 2 + 2
  - 完整的表达式要被 ` ` 包含，注意这个字符不是常用的单引号，在 Esc 键下边
  - bash不支持简单的数学运算，但是可以通过其他命令来实现，例如 awk 和 expr，expr 最常用
```
 #!/bin/bash
 val=`expr 2 + 2`
 echo "Total value : $val"
```
[http://c.biancheng.net/cpp/view/2736.html|shell运算符](http://c.biancheng.net/cpp/view/2736.html|shell运算符)
## 常用数据类型 
### 字符串 
最好用双引号，里面可以直接引用变量。
```
 your_name="qinjx"
greeting="hello, "$your_name" !"
```
### 数组 
定义数组
```
    array_name=(value0 value1 value2 value3)
```
读取数组
```
    NAME[0]="Zara"
```
换取数组长度
```
length=${#array_name[*]}
```
## 常用语句
### 条件语句if 
  - if ... fi 语句；
  - if ... else ... fi 语句；
  - if ... elif ... else ... fi 语句。
```
 if [ expression ]
then
   Statement
fi
```
注意：所有的[]和里面的表达式都需要空格[ $a == $b ]
### 循环语句 
for循环
```
     for loop in 1 2 3 4 5
    do
        echo "The value is: $loop"
    done
```
while循环
```
     COUNTER=0
    while [ $COUNTER -lt 5 ]
    do
        COUNTER='expr $COUNTER+1'
        echo $COUNTER
    done    
```
until循环
```
a=0
until [ ! $a -lt 10 ]
do
   echo $a
   a=`expr $a + 1`
done
```
跳出循环break，continue。这两个关键字后面可以跟数字，表示跳出基层循环。
## 函数 
函数定义
```
Hello () {
   echo "hello"
   return 1
}
```
函数调用，直接写函数名字就行。函数返回值在调用该函数后通过 $? 来获得
```
Hello
ret=$?
```
函数参数
```
funWithParam(){
    echo "第一个参数 $1 !"
    echo "第二个参数 $2 !"
    echo "第十个参数 $10 !"
    echo "参数个数 $# !"  
    echo "传递给函数的所有参数 $* !"  # 传递给函数的所有参数
}
funWithParam 1 2 3 4 5 6 7 8 9 10
```
## 文件操作 
向文件中写 command > file ，command为命令，file为文件。
```
echo "1" > users
```
例子：定时删除多少天之前的文件
1、新建文件夹hello.sh并给予运行权限，并在其中输入以下代码
```
#！/bin/bash
dir=/app/webContent/ems-admin/logs/
find ${dir} -mtime +1 -type f|xargs rm -f
```
${dir}为路径
-mtime +1 是设置时间为1天前
-type f表示删除的是文件
"|"为管道，连接一个命令的标准输出和另一个命令的标准输入。
xargs可以通过管道传递参数，作用是将参数列表转换成小块分段传递给其他命令。
2、建立定时任务
使用命令crontab -e编辑定时任务。加上以下代码
```
*/1 * * * * /app/test/shellcode/hello.sh
```
每分钟运行一次hello.sh文件。