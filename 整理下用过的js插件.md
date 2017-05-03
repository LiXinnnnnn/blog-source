---
title: 整理下用过的js插件
date: 2016-12-29 21:21:05
tags: js
categories : js
---
[Toc]
#### 前言
又是一个加班的夜晚，烦得慌。
忙里偷闲下用过的js插件吧。以后想用的时候就可以直接从这里拿了，也欢迎朋友们分享自己用过的插件。
![你的插件](/post_images/201612291.png)
#### cookie插件
一款管理cookie的插件——jquery.cookie.js。使用非常简单。
cdn: `<script src="http://cdn.bootcss.com/jquery-cookie/1.4.1/jquery.cookie.js"></script>`
官网：[http://plugins.jquery.com/cookie/](http://plugins.jquery.com/cookie/)
#### 表单验证插件
一款表单提交时验证的插件——jquery.validate.js，使用非常简单方便。其中内置了许多验证方法，也允许用户自定义方法，我现在一直再用。
cdn: `<script src="http://static.runoob.com/assets/jquery-validation-1.14.0/lib/jquery.js"></script>`
官网：[http://plugins.jquery.com/validate/](http://plugins.jquery.com/validate/)
#### 上传文件插件
一款上传文件的插件——uploadify.js。可以实现异步上传，使用实在是太简单，我都不想放例子。
``` javascript
$(function() {
    $("#file_upload_1").uploadify({
        height        : 30,
        swf           : '/uploadify/uploadify.swf', //直接用下载的，为上传文件的进度条
        uploader      : '/uploadify/uploadify.php',//接受文件的接口
        width         : 120
    });
});
```
下载地址： [http://www.uploadify.com/download/](http://www.uploadify.com/download/)
#### 在线编辑图片插件
一款可以编辑上传好的图片的插件——cropper.js。可以实现对上传上来的图片缩放，裁剪等等一系列操作，如果网站中有上传t头像这个功能，不妨用一下。比自己写要好得多。
官网： [https://fengyuanchen.github.io/cropper/](https://fengyuanchen.github.io/cropper/)
#### 图表插件
图表插件多的数不过来，我在这安利一款highcharts。
官网： [http://www.hcharts.cn/](http://www.hcharts.cn/)
#### 富文本编辑器
富文本编辑器很多人用的百度的，我用过的一款ckeditor也很不错的。对每个功能都可以自定义。
<script src="//cdn.ckeditor.com/4.6.1/basic/ckeditor.js"></script>
<textarea name="editor1" id="editor1" rows="10" cols="80">
This is my textarea to be replaced with CKEditor.
</textarea>
 <script> CKEDITOR.replace( 'editor1' );</script>




