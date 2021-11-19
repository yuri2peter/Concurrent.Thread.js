# Concurrent.Thread.js

> 本库的代码与文档皆来源于网络，仅供备份。

Concurrent.Thread.js是一位日本人开发的，用来让javascript也进行多线程开发的包，可以让我们将耗时的任务利用前端来模拟多线程。

## 警告

该项目最后更新于2009年，其对于最新的js语言特性和nodsjs的适用性未知，且其内部实现相当的“魔法”，本人并不推荐在正式大型项目中使用。

但是原作者在本项目中突破语言限制实现“多线程”的天马行空的效果，还是值得一试并仔细研究的。

## Demo

在HTML5 WebWork没出现之前很多人都是用ConcurrentThread.js模拟多线程。 

> 通常，我们也会用setInterval和setTimeout来模拟多线程。

该实例展示了Concurrent.Thread.js最典型的使用场景，完整文件位于[doc/demo.html](./doc/demo.html)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>JavaScript多线程</title>
    <script type="text/javascript" src="http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
    <script type="text/javascript" src="Concurrent.Thread.js"></script>
    <style type="text/css">
    div {
        width: 100px;
        height: 100px;
        cursor: pointer;
        background: orange;
    }
    </style>
</head>

<body>
    <div id="test">
        测试点击
    </div>
    <script type="text/javascript">
    Concurrent.Thread.create(function() {
        $('#test').click(function() {
            alert(1);
        });
        /*下面有一段特别复杂的函数*/
        /*这段代码“神奇的”并不会阻塞主线程*/
        for (var i = 0; i < 10000; i++) {
            console.log(i);
        }
    });
    </script>
</body>

</html>
```

## 更多

- [进阶文档（推荐）](./doc/usage.md)
- [官方论文（En）](./doc/thesis-en.pdf)