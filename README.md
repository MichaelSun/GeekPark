# GeekPark 前端代码规范  
![GeekPark](http://www.geekpark.net/public/css/images/logo.png)
![ITvalue](http://2009.itvalue.com.cn/mod/iv/views/default/css/images/logo.gif)

这里是 [GeekPark] & [ITvalue] 前端开发团队遵循和约定的代码书写规范，意在提高代码的规范性和可维护性。

## 规范内容
----
1. CSS reset 文件：[base.css]  
所有代码都基于这个文件。重设浏览器，解决依赖引起的耦合问题。 
    * base.css 的作用:
        * CSS reset
    * 其他功能：
        * .fn-clear 清除浮动
        * .fn-hide/.fn-show 相当于display:block;/display:none;
        * .fn-left/.fn-right 相当于 float:left;/float:right;

2. 规范：
此规范为参考规范，不是硬性要求，部分硬性约定见下一条\[书写约定\]，统一团队编码规范和风格。让所有代码都是有规可循的，并且能够得到沉淀，减少重复劳动。
 
3. 工具：[通用兼容解决方案库]  
常见浏览器兼容问题的解决方案，可以参考这里的库，只参考思路即可。

## 书写规范
----
###样式与内容分离

* 文件结构： 
```
    ---
     |---- images/                存放CSS文件中使用到的 image 图片  
     |---- js/                    调用js文件  
     |---- base.css               CSS reset 文件  
     |---- style.css              样式表  
     |---- index.html             内容文件  
```
* 重构步骤约定：
    1. index.html 全部样式附着于 class="xxx" **注：** _此时文    件中不包含任何一个 id="xxx"_
    2. 为上一步书写 CSS style  
    **\[至此重构完成\]**
    3. 开始书写js交互文件，使用 ID 和 Class 定位被操作句柄
    4. 向 index.html 中需要的地方添加 id="xxx"  
    **\[至此交互效果完成\]**
    
* 命名规范：  
    * 文件及文件夹: 全部英文小写字母+数字或连接符"\- , \_ "，不可出现中文等字符。  
    如：../geekevent/css/style.css, jquery.1.x.x.js 
    * ID: [匈牙利命名法] & [小駝峰式命名法]  
    如：firstName, topBoxList, footerCopyright
    * Class: [减号连接符]  
    如：top-item, main-box, box-list-item-1
    
* 格式&编码：
    * 文本文件： .xxx UTF-8_\(无BOM\)_ 编码
    * 透明图片： .png _(PNG-24)_
    * 动态图片： .gif
    * 打包文件： .zip
    
###CSS 细化规范

* CSS 注释格式约定  
>
```
/*
@name: Drop Down Menu
@description: Style of top bar drop down menu.
@require: base.css
@author: Andy Huang(andyahung@geekpark.net)
*/
```
_其中，@require为可选项目_ 

* CSS换行制表：使用 4 个空格，而非\[tab\]
       
    * 书写格式：
        * CSS名称+冒号+属性  
        如：.box1{float:left;}
        * 如多个class一起，需要再第一个后的","号后加一个空格  
        如：.box1,.box2,.box3{font-family:Courier,'Courier New';}
        
    * CSS各熟悉的排列顺序：不做硬性要求  
    _如：以下2种顺序均可_
    >
```
.box{
    /* 顺序1 */
    background: none repeat scroll 0 0 transparent;
    bottom: 11px;
    position: relative;
    width: 22px;
    z-index: 33;
}
```
    >
```
.box{
    /* 顺序2 */
    z-index: 33;
    width: 22px;
    bottom: 11px;
    background: transparent none repeat scroll 0 0 ;
    position: relative;
}
```
  
    * 切记业界书写准则：HTML不要相互嵌套，CSS 推荐嵌套。  
    >
```
/* 推荐嵌套层级 */
.ui-icon-rarr{background:...}
.ui-icon-larr{background:...}
.ui-title{font-size:...}
.ui-nav .ui-list{...}
.ui-table .ui-list{...}
```
    >
```
/* 不推荐 */
.ui-icon-rarr{background:...}
.ui-icon-larr{background:...}
.ui-title{font-size:...}
.ui-list{}
.ui-nav{}
```
    * CSS格式化：最终网站上输出的CSS，每个选择器单行，最优压缩，保留注释  
    >
```
/* 注释内容 */
.box{z-index:33;width:22px;bottom:11px;background:transparent none repeat scroll 0 0 ;position: relative;}
.box2{z-index:44;width:55px;}
.box3,#box4{z-index:66;width:77px;}
```
    _可使用工具：[CSS Compressor] 并选择\[highest\]压缩_  
    
###XHTML 细化规范：

* HTML 注释格式约定  
    >
```
 <!--
@name: Drop Down Menu
@description: Style of top bar drop down menu.
@require: base.css
@author: Andy Huang(andyahung@geekpark.net)
-->
```
* HTML换行缩进：采用 2 空格

* 切记业界书写准则：HTML不要相互嵌套，CSS 推荐嵌套。  
    >
```
/* 推荐嵌套层级 */
  <ul class="ui-nav">
    <li class="ui-nav-item"> some text
        <ul class="ui-nav-item-child">
            <li> some text
                <ul class="ui-list">
                    <li class="ui-list-item"> some text</li>
                </ul...
        </ul>
    </li>
    <li...
</ul>
```
    >
```
/* 不推荐 */
  <ul class="ui-nav">
    <li class="ui-nav-item"> some text
        <ul class="ui-nav-item-child">
            <li> some text
                <ul class="ui-nav">
                    <li class="ui-nav-item"> some text </li>
                </ul...
        </ul>
    </li>
    <li...
</ul>
```

* 第一行统一使用：<!DOCTYPE html>
* \<img\>标签默认缺省格式：\<img src="xxx.png" alt="缺省时文字" />
* \<a\>标签缺省格式：\<a href="#" title="链接名称">xxx\</> 注：target="_blank" 根据需求决定  
* html块状内容注释规则：在结束时，添加 例如 
    <div id="#func">
        xxx
    </div>
    <!-- #func end -->  
* 所有编码均遵循xhtml标准, 且所有标签必须小写，必须闭合, 包括br (<br />), hr(<hr />)等; 属性值必须用双引号(或者 单引号 )
* 充分利用无兼容性问题的html自身标签, 比如span, em, strong , label,等等; 需要为html元素添加自定义属性的时候, 首先要考虑下有没有默认的已有的合适标签去设置, 如果没有, 可以使用须以”data-”为前缀来添加自定义属性，避免使用”data:”等其他命名方式
* 书写链接地址时, 必须避免重定向，例如：href=”http://geekpart.com/”, 即须在URL地址后面加上“/”； img 不能写src="" 会造成 重载入 参照：[src="" 问题]

* 在页面中尽量避免使用style属性,即style=”…“ ，除非插件生成的css，我们写避免此现象 如用hide 可用class代替

* 特殊符号使用: 尽可能使用代码替代: 比如< > 用 &gt;，&lt; 并统一在浏览器表现的形式问题 ，

* 开发过程中研究通用部分或以后实现, 以提高模块复用率, 避免重复开发，浪费时间;

* 书写所有人都可以看的懂的代码. 简洁易懂是一种美德.

###JS 细化规范：
* 文件编码统一为utf-8, 书写过程过, 每行代码结束必须有分号;
* 库引入: 原则上仅引入jQuery库,库和插件的命名规则为 库名称-版本号-是否为压缩.js ,若需引入插件,必须写明使用文档，方便其他人维护;语法验证 可选(jslint)
* jQuery变量要求首字符为 '$', 私有变量:首字符为'_'; 要求变量集中声明, 避免全局变量.
* 命名语义化, 尽可能利用英文单词或其缩写(驼峰式);
* 避免使用 eval()，setTimeOut使用调用函数，考虑重绘，回流 操作对页面影响  参看：[reflows，repaints].
* 
* 整理排版中，待发  

###Newletter制作规范：
* 整理排版中，待发



-- refer to [Alice] & [Bootstrap]  
    

[GeekPark]: http://geekpark.net/ "http://geekpark.net/"
[ITvalue]: http://www.itvalue.com.cn/

[Alice]: https://github.com/alipay/alice "Alice 支付宝前端样式解决方案"
[Bootstrap]: http://twitter.github.com/bootstrap/ "Bootstrap, from Twitter"
[base.css]: https://github.com/hzlzh/GeekPark/blob/master/base.css "CSS reset 文件"
[CSS 规范]: http://aliceui.com/css-spec/ "CSS 代码书写规范"
[样式库构建规范]: http://aliceui.com/alice-css-guide/ "该项不予参考"
[通用兼容解决方案库]: http://aliceui.com/alice-css/#solutions "该项不予参考"

[匈牙利命名法]: http://zh.wikipedia.org/wiki/%E5%8C%88%E7%89%99%E5%88%A9%E5%91%BD%E5%90%8D%E6%B3%95 "Wiki:匈牙利命名法"
[小駝峰式命名法]:http://zh.wikipedia.org/wiki/%E9%A7%9D%E5%B3%B0%E5%BC%8F%E5%A4%A7%E5%B0%8F%E5%AF%AB "小駝峰式命名法"
[CSS Compressor]: http://www.csscompressor.com/ "CSS 压缩"


[reflows，repaints]:http://www.zhangxinxu.com/wordpress/2010/01/%E5%9B%9E%E6%B5%81%E4%B8%8E%E9%87%8D%E7%BB%98%EF%BC%9Acss%E6%80%A7%E8%83%BD%E8%AE%A9javascript%E5%8F%98%E6%85%A2%EF%BC%9F/  "重绘,回流参考"

[src="" 问题]:http://hi.baidu.com/bdui/blog/item/9f6ed4af65c349cf7cd92a1f.html