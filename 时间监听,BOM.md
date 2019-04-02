## 事件监听

`addEventListener` 是 W3C DOM 规范中提供的注册事件监听器的方法。IE < 11 不支持此方法

`attachEvent(event,listener)` 也是用来监听事件的，只能用于 IE 10 以下，IE 11 已经废弃此方法

它的优点包括：

1. 它允许给一个事件注册多个 listener。

2. 它提供了一种更精细的手段控制 listener 的触发阶段。（即可以选择捕获或者冒泡）。

3. 事件目标可以是一个文档上的元素 Element,Document和Window或者任何其他支持事件的对象 (比如 XMLHttpRequest)。

> 语法： `target.addEventListener(type,listener,useCapture]);`
> 
> target： 文档节点、document、window 或 XMLHttpRequest。
> 
> type： 字符串，事件名称，不含“on”，比如 “click”、“mouseover”、“keydown” 等。 
> 
> listener：执行函数。
> 
> useCapture ：是否使用捕捉，一般用 false。  IE 10 以下不支持捕获型事件
>
> 事件三阶段： 捕获阶段，处于目标阶段，冒泡阶段


## `removeEventListener` 移除绑定

1. 如果同一个监听事件分别为“事件捕获”和“事件冒泡”注册了一次，一共两次，这两次事件需要分别移除。两者不会互相干扰。

2. 解绑事件 必须是具名函数

--------------------------------------

## 定时器

1. `setTimeout()`	延迟执行

2. `setInterval() clearInterval()`	循环执行

```js
// 倒计时
var futureTime = new Date("2019-4-1 9:58:00").getTime(),
		hourTime = 60*60*1000,
		minTime = 60*1000;
		

var timer = setInterval(function (){
	var nowTime = new Date().getTime();
	if(nowTime >= futureTime - 1000){
		alert("boom");
		clearInterval(timer);		// 删除定时器 定时器必须有名字
	}
	var	countTime = futureTime - nowTime,	// 时间差
		hour = Math.floor(countTime/hourTime),
		minute = Math.floor((countTime % hourTime)/minTime),
		second = Math.floor((countTime % minTime) / 1000);
	
	var str = "还剩下" + hour + "时" + minute + "分" + second + "秒";
	box.innerText = str;
	
},1000)
```

 
---------------------------

## BOM

`ECMAScript` 是 `javascript` 的核心，但是如果要在 `web` 中使用 `javascript`，那么 `BOM` (浏览器对象模型)才是真正的核心。BOM提供了很多对象，用于访问浏览器的功能，这些功能与任何网页内容无关。

`BOM` 的核心对象是 `window` ，它表示浏览器的一个实例。在浏览器中， `window` 对象有双重角色，它既是通过 `javascript` 访问浏览器窗口的一个接口，又是 `ECMAScript` 规定的 `Global` 对象。所有全局作用域中声明的变量、函数都会变成 `window` 对象的属性和方法。

### 三大家族其一 `Offset` 家族

> 家族成员： `offsetWidth` `offsetHeight` `offsetLeft` `offsetTop` `offsetParent`

#### `offsetWidth`  `offsetHeight`  （检测盒子自身宽高）

> 这两个属性，他们绑定在了所有的节点元素上。获取之后，只要调用这两个属性，我们就能够获取元素节点的宽和高。

>` offset宽/高  =  盒子自身的宽/高(width/height) + padding +border`

#### `offsetLeft`  和  `offsetTop`  （检测距离父盒子有定位的左/上面的距离）

> 如果父级都没有定位则以 `body` 为准, `offsetLeft` 从父亲的 `padding` 开始算,父亲的 `border` 不算。
> 在父盒子有定位的情况下，`offsetLeft == style.left`(去掉 px)

#### `offsetTop/Left` 和 `style.top/left` 的区别：

1. 最大区别在于 `offsetTop/Left` 可以返回没有定位盒子的距离左侧的位置。而 `style.top/left` 不可以

2. `offsetTop/Left` 返回的是整数，而 `style.top/left` 返回的是字符串，除了数字外还带有单位：`px`

```js
<div class="d1" style="position:relative;width: 300px;height: 200px;background-color: green;"></div>
<script>
	var d1= document.getElementsByClassName('d1')[0];
	d1.onclick = function(){
		d1.style.width = '400.499999999999999px';
		console.log(d1.offsetWidth);	// 401
		console.log(d1.style.width);	// "400.5px"
		d1.style.top = "50.49999999999999px";
		console.log(d1.style.top)	// "50.5px"
		console.log(d1.offsetTop)	// 51
	}
</script>
```

3. `offsetTop/Left` 只读，而 `style.top/left` 可读写。（只读是获取值，可写是赋值）

4. `obj.style.xxx` 只能获取行内样式

#### `offsetParent`   （检测父系盒子中带有定位的父盒子节点）

> 1、返回改对象的父级 （带有定位）
> 
>&emsp;&ensp;如果当前元素的父级元素没有进行 CSS 定位(absolute,relative,fixed) `offsetParent` 为 `body`
>	
> 2、如果当前元素的父级元素中有 CSS 定位 `offsetParent` 取最近的那个父级元素。

### 动画和封装1

1. 动画的种类
	+ 闪现动画（被淘汰）
	+ ```js
		<div class="box" style="position:relative;width:200px;height:200px;background-color: red;"></div>
		<button>跳到400</button>
		<button>跳到800</button>
		<script type="text/javascript">
			var box = document.getElementsByClassName("box")[0];
			var btn = document.getElementsByTagName("button")[0];
			var btn1 = document.getElementsByTagName("button")[1];
			btn.onclick = function (){
				box.style.left = "400px";
			}
			btn1.onclick = function (){
				box.style.left = "800px";
			}
		</script>
	```
	+ 匀速动画（今天重点）
	+ 缓动动画（以后重点）

2. 动画原理
	+ 物体运动： 起点，终点，速度（距离/时间）
	+ 盒子的位置 = 盒子本身所在的位置 + 步长


