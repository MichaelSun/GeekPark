## GeekPark 代码规范  

这里是 [GeekPark] & [ITvalue] 前端开发团队遵循和约定的代码书写规范，意在控提高人代码的规范性和可维护性。

### 规范内容  
1. CSS reset 文件：[base.css]  
所有代码都基于这个文件。重设浏览器，解决依赖引起的耦合问题。

2. 规范：[CSS 规范] / <del>[样式库构建规范]</del>  
此规范为参考规范，不是硬性要求，部分硬性约定见下一条\[书写约定\]，统一团队编码规范和风格。让所有代码都是有规可循的，并且能够得到沉淀，减少重复劳动。
 
3. 工具：[通用兼容解决方案库]  
常见浏览器兼容问题的解决方案，可以参考这里的库。

###书写约定  
####样式与内容分离

* 文件结构： 
    
    ---
     |---- images/                存放CSS文件中使用到的 image 图片  
     |---- js/                    调用js文件  
     |---- base.css               CSS reset 文件  
     |---- style.css              样式表 
     |---- index.html             内容文件  


* 重构步骤约定：
    1. index.html 全部样式附着于 class="xxx" **注：** _此时文件中不包含任何一个 id="xxx"_
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
    
* CSS 细化规范：   
    * CSS换行制表：使用 4 个空格，而非\[tab\]
       
    * 书写格式：
        * CSS名称+冒号+空格+属性 或者 名称+冒号+属性均可      
        如：.box1{float: left;} 和 .box{float:left} 均可
        * 如多个class一起，需要再第一个后的","号后加一个空格  
        如：.box1, .box2, .box3{float: left;}
        
    * CSS各熟悉的排列顺序：不做硬性要求  
    如：以下2种顺序均可    
    ><pre>.box{
        /\* 顺序1 \*/
        background: none repeat scroll 0 0 transparent;
        bottom: 11px;
        position: relative;
        width: 22px;
        z-index: 33;
    }  
    .box{
        /\* 顺序2 \*/
        z-index: 33;
        width: 22px;
        bottom: 11px;
        background: transparent none repeat scroll 0 0 ;
        position: relative;
    }</pre>
    
    * CSS格式化：非最小压缩格式化，采用逐行显示属性的格式  
    如：  
    <pre>.box{
        /\* 注意这里换行是用 4 空格 \*/
        z-index: 33;
        width: 22px;
        bottom: 11px;
        background: transparent none repeat scroll 0 0 ;
        position: relative;
    }</pre>
    可使用工具：[CSS Formate] 并选择处理，结果前三种均可使用
* XHTML 细化规范：
    * HTML换行缩进：采用 2 空格
    * 第一行统一使用：<!DOCTYPE html>
    * \<img\>标签默认缺省格式：\<img src="xxx.png" alt="缺省时文字" \/>
    * \<a\>标签缺省格式：\<a href="#" title="链接名称">xxx\</> 注：target="_blank" 根据需求决定  
    
* JS 细化规范：
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

[CSS Formate]: http://www.cssportal.com/format-css/ "格式化CSS，选择处理后的前三种"
