---
title: markdown语法简介
date: 2016-12-21 16:10:17
tags: markdown
categories : study
---
### 写在前面
自己的博客是使用md语法书写的，学习使用起来也非常的方便快捷。趁上班之余，把md的语法记录一下，方便自己和他人查看（估计没有他人）。至于博客是怎么搭建起来的，我就不专门写篇文章了，如果有朋友搭建博客有问题的可以留言或直接联系我。
***
### 标题
如果一段文字被定义为标题，只要在这段文字前加#号即可。总共六级标题，建议在井号后加一个空格，这是最标准的 Markdown 语法。
` ## 一级标题 `
`  ## 二级标题 `
`  ### 三级标题 ` 
![title](http://ww1.sinaimg.cn/large/6aee7dbbgw1effeaclhiyj20eh09cwez.jpg)
### 列表
列表的显示只需要在文字前加上 `-` 或 `*` 即可变为无序列表，有序列表则直接在文字前加`1.` ` 2.` ` 3.` 符号要和文字之间加上一个字符的空格。
![title](http://ww4.sinaimg.cn/large/6aee7dbbgw1effew5aftij20d80bz3yw.jpg)
### 引用
在文本前加入` > `这种尖括号（大于号）即可
>例如这样

![title](http://ww3.sinaimg.cn/large/6aee7dbbgw1effezhonxlj20e009c3yu.jpg)
### 图片与链接
插入链接与插入图片的语法很像，区别在一个 `!`号。
链接：`[链接显示的文字](链接地址)` ，相当于`<a href="链接地址">链接显示的文字</a>`
图片：`![图像的替换文本](图像地址)` ，相当于`<img src="图像地址"  alt="图像的替换文本" />`
图片地址可以写相对路径，文章发布时需要将图片一起上传。更好的做法是将图片上传的云上，使用时直接引用链接即可。
![title](http://ww2.sinaimg.cn/large/6aee7dbbgw1efffa67voyj20ix0ctq3n.jpg)
### 粗体与斜体
Markdown 的粗体和斜体也非常简单，用两个 `*` 包含一段文本就是粗体的语法，用一个 `*` 包含一段文本就是斜体的语法。
例如：**这是粗体**  *这是斜体*
`**这是粗体**  *这是斜体*`
### 表格
表格比较复杂，还不如使用html标签简单。
```| Tables        | Are           | Cool  |
 | ------------- |:-------------:| -----:|
 | col 3 is      | right-aligned | $1600 |
 | col 2 is      | centered      |   $12 |
 | zebra stripes | are neat      |    $1 |
```
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
 ### 代码
 如果你是个程序猿，需要在文章里优雅的引用代码框，在Markdown下实现也非常简单，只需要用两个 \` 把中间的代码包裹起来。缩进用`tab`键。一段代码用\`\`\`+语言名称进行标记。
 例如：
 \`\`\` java
public class HelloWorld(){
    private void print(String s){
        System.out.print(s);
    }
}
\`\`\`
``` java
public class HelloWorld(){
    private void print(String s){
        System.out.print(s);
    }
}
```
### 其他
分割线的语法只需要三个 `*` 号
转义字符\

 



