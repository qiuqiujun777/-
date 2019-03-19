#css样式
##  1.内部样式
>     <style>p{color:red}</style>
+   测试使用,但是当前页面的样式只能在当前页面使用
##  2.引入样式
>     <like rel="stylesheet"href="style.css">
+   上线时候使用,可以在多个页面复用外部样式.
##  3.标签选择器 class选择器 id选择器
>     /*标签选择器*/
		h1{
			color: red;
		}
		/*class选择器*/
		.h2{
			color: blue;
		}
		/*id选择器*/
		#h3{
			color: orange;
		}
##  4.交集选择器 并集选择器 后代选择器
>     /*标签p 和.p1的交集*/
		p.p1{
			color: red;
		}
		.p2.danger{
			color: blue;
		}
		/*并集选择器 都被选中*/
		.p1,.p2{
			font-size: 30px;
		}
		/*后代选择器 空格*/
		.p3 a{
			color: red;
		}
##  5.通配符
>     通配符 选择所有标签*/
		*{
			/*background-color: pink;*/
		}
##  6.单位
+     px;像素单位
+     em;基于字体大小的倍数 比如:text-indent:2em;
+     %;百分比是相对于父类元素来定的;
##  7.颜色
+     rgba(0,0,0,.5) 最后是透明度,通常.5
##  8.常用属性
+     width  宽度
+     height  高度
+     color  颜色
+     background-color  背景颜色
+     text-align 内容水平对齐 left/center/right
+     text-indent  首行缩进 2px;
+     font-size  字体大小
+     font-style  italic斜体/normal正常
+     font-family  微软雅黑(Microsoft YaHei),宋体,黑体
+     font-weight  字体加粗700-900 "border/lighter/normal"
+     line-height  行高. 单位px/倍数/百分比,设置文字的行间距,单行文字垂直居中 行高=父类盒子高度
##  9.背景图片
+     background-color  背景颜色 
+     background-image  背景图片 url(xx/xx.jpg)   
+     background-repeat  平铺方式 repeat/no-repeat/repeat-x/repeat-y
+     background-position  图片位置 left/right/top/bottom/center
+     background-attachment  背景滚动 scroll/fixed(基于body的定位)
+     background:red url() no-repeat center center fixed;
##  10.标签表现形式
+     块状标签(独占一行,宽高有效,可以自动换行)dispaly:block,比如:div p h1~h6 form table hr br ul-li ol-li dl-dt/dd
+     行内块标签(可以同一行显示,宽高有效,不会自动换行)display:inline-block,比如:input select img button
+     行内标签(可以同一行显示,但是宽高无效,不会自动换行)display:inline,比如:a span strong del ins em i b
##   11.盒子模型
+     CSS处理网页时，它认为每个元素都包含在一个不可见的盒子里。包含content(内容区域)、 padding（内边距） 、 border（边框）、margin（盒子与盒子的距离）外边框
##   12.padding
+    padding-内边距
+     padding:10px 20px 30px 40px 这样会设置元素的上、右、下、左四个方向的内边距。 
+     padding:10px 20px 30px; 分别指定上、左右、下四个方向的内边距
+     padding:10px 20px; 分别指定上下、左右四个方向的内边距
+     padding:10px;同时指定上左右下四个方向的内边距
+     同时在css中还提供了padding-top,padding-left,padding-right,padding-bottom分别用来指定四个方向的内边距。
##   13.margin
+     margin-外边距,用法同padding
+     margin: xx auto(左右居中)
##   14.overflow:hidden
+     嵌套崩塌:两个盒子发生嵌套的时候，给子类设置maring会给父类造成一种崩塌现象，子类的margin-top没有效果，而直接作用到父类。
+     嵌套崩塌解决方案1:父类加overflow:hidden 2:父类设置极小的padding
##   15.补充
+     重叠:如果垂直两个块状元素同时设置了margin-bottom和margin-top,那么这两个值将会发生重叠,不会累加，哪个值大用哪个。
+     *margin-top/margin-bottom 对于行内元素无效。
##   影响盒子大小的因素
+	  继承的盒子在父类盒子宽度范围内,padding值不会影响该盒子大小.
##   16.display
+     我们可以通过修改display来修改元素的性质
+     :block 设置元素为块元素
+     :inline 设置元素为行内元素
+     :inline-block 设置元素为行内块元素
+     :none 隐藏元素
+     转换的必要性:比如可以把a标签转换为块状元素,进而实现一个按钮的样式
##   17.visibility
+     visibility和display不同,使用visibility隐藏一个元素,隐藏后其在文档中所占的位置会依然保持,不会被其他元素覆盖.
+     值:visible(可见的)
+       :hidden(隐藏的)
##   18.overflow
+     相关标签里面的内容超出了样式的宽度和高度时如何处理
+     可选值:visible默认值
+     scroll添加滚动条
+     auto根据需要添加滚动条
+     hidden隐藏超出盒子的内容
##   19.border边框
+     可以在元素周围创建边框,边框是元素可见框的最外部
+     可以使用border属性来设置盒子的边框
+     border:1px solid red分别指定了边框的宽度,样式,颜色.
+     样式border-style:none(没边框,默认)dotter(点线)dashed(虚线)solid(实线)double(双实线)
+     border-width,border-color,border-style
+     也可以使用border-top/left/right/bottom分别指定上左右下的边框,和padding一样,默认宽度和高度并包括边框的宽度
+     可以单独设置一条边框:border-right:20px solid blue
##   20.文档流
+     块状元素独占一行
+     行内元素在同一行上显示,如果排不下自动换行
+     自上而下的展示
##   21.浮动的表现形式
+      浮动指的是使元素脱离原来的文本流，在父元素中浮动起来。
+     块级元素和行内元素都可以浮动，当一个行内元素浮动以后将会自动变为一个块级元素.
+     当一个块级元素浮动以后，宽度会默认被内容撑开，所以当漂浮一个块级元素时我们都会为其指定一个宽度。
+     当一个元素浮动以后，其下方的元素会上移。元素中的内容将会围绕在元素的周围。
+     浮动会使元素完全脱离文本流，也就是不再在文档中在占用位置。
+     元素设置浮动以后，会一直向上漂浮直到遇到父元素的边界或者其他浮动元素。
+     元素浮动以后即完全脱离文档流，这时不会再影响父元素的高度。也就是浮动元素不会撑开父元素。
+     浮动元素默认会变为块元素，即使设置display:inline以后其依然是个块元素。
##   22.浮动的影响
+     如果子类元素设置了浮动，而父类元素没有设置高度，或者高度比子类元素小，那么子类元素脱离了文档流，就无法把父类盒子撑开。那么整个文档的结构将受到破坏。
##   23.清除浮动
+     clear:left/right/both 不允许当前元素的left/right/both有浮动元素.
+     在浮动元素的最后面追加一个空的div,设置clear:both即可清除浮动的影响
+     补充:1.display：inline-block 标签的换行符会被显示为空格  2.float:right  会改变标签的前后顺序。
##   23.定位
+     通过postion属性可以实现元素的定位。元素定位之后，需要通过设置left和top值对元素定位。
+     static 默认
##   24.相对定位(re)
+     relative 相对定位,相对元素本身的位置定位
+     当开启了相对定位以后，可以使用top、right、bottom、left四个属性对元素进行定位。
+     如果不设置元素的偏移量，元素位置不会发生改变。
+     相对定位不会使元素脱离文本流。元素在文本流中的位置不会改变。
+     相对定位不会改变元素原来的特性。
+     相对定位会使元素的层级提升，使元素可以覆盖文本流中的元素。
##   25.绝对定位(ab)
+     absolute 绝对定位指使元素相对于html元素或离他最近的祖先定位元素进行定位。
+     当开启了绝对定位以后，可以使用top、right、bottom、left四个属性对元素进行定位。
+     绝对定位会使元素完全脱离文本流。
+     绝对定位的块元素的宽度会被其内容撑开。
+     绝对定位会使行内元素变成块元素。
+     一般使用绝对定位时会同时为其父元素指定一个相对定位，以确保元素可以相对于父元素进行定位。
##   26.固定定位(fixed)
+     元素会被锁定在屏幕的某个位置上，当访问者滚动网页时，固定元素会在屏幕上保持不动
+     固定定位不占据原来的位置，会脱标
+     给元素设置固定定位之后，元素位置从浏览器左上角出发
+     可以将行内元素转换为行内块元素
##   27.z-index(权重)
+     当元素开启定位以后就可以设置z-index这个属性。默认是0.值越大，越靠上。
+     z-index可以指定一个整数作为参数，值越大元素显示的优先级越高，也就是z-index值较大的元素会显示在网页的最上层。
##   28.规避脱标流
+     一般布局采用标准流，如果布局实现不了用浮动。定位一般用于解决小范围的某个标签的位置。
+     能用标准流（没有脱标）解决就不用浮动
+     解决不了就考虑用浮动（页面布局类型，“不完全脱标”）
+     浮动解决不了用定位（小图标，完全脱标，不影响内容）
