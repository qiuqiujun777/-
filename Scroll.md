## 立即执行函数传参

```js
// 传值的三种写法

(function fn(name){
	console.log(name)
})("zhangsan");

(function fn(name){
	console.log(name)
}("zhangsan"));

var ff = function (name){
	console.log(name)
}("zhangsan");

// 传一个变量
var a = 10;

(function fn(){
	console.log(a);
})(a);
```


-----------------------------

## 缓动动画

> leader = leader + (target - leader) / 10;
> 起点 = 起点 + (终点 - 起点) / 10;


小点的点击事件

```js

for(var i = 0; i < dotts.length; i ++){
	dotts[i].onclick = function(i){
			return function (){
				n = i;
				dotClick(n);
				move(ulEle,n);
			}
	}(i)
}

```


缓动函数
```js

function move(ele,num){
	clearInterval(timer);
	var target = -num * w;
	timer = setInterval(function (){
		var start = ele.offsetLeft;
		if(start === target){
			clearInterval(timer);
			return;
		}
		var step = (target - start) / 10;
		if(Math.abs(step) < 1){
			step = step > 0 ? 1 : -1;
		}
		ele.style.left = start + step + "px";
	},17)
}

```

-----------------------------


## `Scroll` 家族

> 家族成员: `scrollWidth` , `scrollHeight` , `scrollTop` , `scrollLeft`

#### `scrollWidth` 和 `scrollHeight`

> 检测盒子的宽高  内容高度 + padding。（调用者：节点元素。属性。）
> 盒子内容的宽高。（如果有内容超出了，显示内容的高度）

#### `scrollTop` , `scrollLeft`
 
> 被浏览器遮挡的头部和左边部分。
> 可以获取或设置一个元素的内容垂直滚动的像素数。


