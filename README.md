Impress.js使用教程
==================

简介
----

Impress.js是一款基于css3转换和过渡、工作于现代浏览器(Google Chrome或Safari (或 Firefox 10 或 IE10))、并受prezi.com的理念启发的演示工具。如果你已经厌烦了使用PowerPoint制作PPT，那么impress.js是一个非常好的选择，用它做的PPT更加直观，效果也非常的不错。

Impress.js 是一个非常棒的用来创建在线演示的javascript库，但在其实际的项目网页中却没有说明文档。这篇指导将会帮你开始并创建一个简单的幻灯片演示，但完成后请记住它，用它做的不只局限于此，唯一的限制是你的创造力！

目前impress.js在最新的chrome/chromium、Safari 5.1 和Firefox 10上表现效果最佳，不兼容早期版本的Firefox或Internet Explorer。。在Opera中不能运行，因为他不支持CSS 3D转换。

配置
----

首要的事情是你要创建一个新的网页，我的是index.html并且里面配置了基本的head和body元素。

    <!doctype html>
    <html>
        <head>
            <title>Impress Tutorial</title>
            <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        </head>
        <body>

        </body>
    </html>

在body元素结束前引入impress.js文件，这是Impress包引入到你的项目中。

    <script type=”text/javascript” src=”impress.js”></script>

接下来我们将创建一个wrapper包含幻灯片，这里用一个简单的id为 ‘impress’<div>元素。

    <div id="impress">
    </div>

创建幻灯片
---------

现在你可以看到创建一个新的幻灯片是多少的容易了。每个幻灯片是一个<div>元素 (在wrapper内) 其class名称叫做’step’。

    <div class="step">
        My first slide
    </div>

虽然是创建一个简单的幻灯片，但你开始向你的幻灯片添加数据属性时还是很有趣的。数据属性表示它不是活动幻灯片时你的幻灯片的属性，您可以使用下面的数据属性：

    data-x = 幻灯片的x坐标
    data-y = 幻灯片的y坐标
    data-scale = 通过指定一个值来进行缩放，data-scale为5则将会在你幻灯片原始尺寸基础放大5倍
    data-rotate = 通过一个数字度数来确定旋转你的幻灯片
    data-rotate-x = 为3D用，这个数字度数是它应该相对x轴旋转多少度。（前倾/后仰）
    data-rotate-y = 为3D用，这个数字度数是它应该相对y轴旋转多少度。 （左摆/右摆）
    data-rotate-z = 为3D用，这个数字度数是它应该相对z轴旋转多少度。

动作中的数据属性
---------------

下面的幻灯片设置将指导你完成每个动作的数据属性。

让我们从一个初始的幻灯片开始，这个幻灯片已将它自己的x和y数据属性设置为0，所以会出现在页面的中间。

    <div class="step" data-x="0" data-y="0">
        This is my first slide
    </div>

第二个幻灯片的x值为500，但y值为0，这意味着当它活动的时候它将会出现在穿过x轴(向左滑动)500px的地方。

    <div class="step" data-x="500" data-y="0">
        This is slide 2
    </div>

简单吧？下一个幻灯片将同第2个幻灯片同样的x位置开始，但其y位置为-400，这将会是从顶部400px处滑入。

    <div class="step" data-x="500" data-y="-400">
        This is slide 3
    </div>

幻灯片4使用缩放值来显示一个幻灯片如何放大缩小。它的scale值为0.5，意味着它应该是一半的尺寸。当它变成活动的演示时将通过必需的倍数调节所有幻灯片的缩放尺寸。在这个示例中它的意思就是这个幻灯片应该正常显示（比例为1），它将需要被放大2倍 (0.5*2 = 1)，所有的其他幻灯片也将被放大至2倍而变成2倍大小。

    <div class="step" data-x="500" data-y="-800" data-scale="0.5">
        This is slide 4
    </div>

旋转属性允许你旋转一个幻灯片到当前视图，幻灯片5被设置旋转50度。

    <div class="step" data-x="0" data-y="-800" data-rotate="90">
        This is slide 5 and it rotates in.
    </div>

最后，为3D转换，你可为每个维度的轴指定旋转属性(x,y,z)。

x轴是横轴，意思是你可使事物倾斜(正值)或向后(负值)，y轴是竖轴，所以你可使事物向左摇摆(负值)或向右(正值)，z轴是纵轴，这将是旋转的东西向上（负值）和向下（正值）。

组合
----

现在你了解了所有你需要给幻灯片展示添加动画效果的的数据属性，你可以以你的想象力用不可思议的和令人惊奇的方式合并这些效果来创建你自己的幻灯片展示风格。

    <div class="step" data-x="-2600" data-y="-800" data-rotate-x="30" data-rotate-y="-60" data-rotate-z="90" data-scale="4">
    This is slide 7 and it has a 3D transition AND a scale.
    </div>

不支持的浏览器
--------------

Impress自动检测浏览器支持与否，并且如果不支持则自动向wrapper“<div>”添加一个样式名称为“impress-not-supported”的样式，使用一些css我们可以在浏览器上向人们显示不支持Impress的信息。

在开始的<div id="impress">添加下面的内容：

    <div class="no-support-message">
        Your browser doesn't support impress.js.  Try Chrome or Safari.
    </div>

然后，创建一个样式表单或引入一个已经存在的样式表单：

    .no-support-message { display:none; }
    .impress-not-supported .no-support-message { display:block; };

默认是隐藏消息的，但如果浏览器不支持时当前样式就会变成impress-not-supported。

玩得开心!
---------

本教程介绍使用Impress.js创建自己的在线演示文稿的基本资料。整个例子您可在GitHub上下载和演示。

原文地址：http://www.cubewebsites.com/blog/guides/how-to-use-impress-js/
译文地址：http://www.woiweb.net/impress-js-tutorial/
