### 01. 时间和日期
* 时间和日期
``` js
let timestamp = Date.now(); //当前时间的时间戳（数值）
console.log(timestamp);
// ===========================================
let now = new Date();  // 当前时间的日期对象
let ms = now.getTime(); //转换为毫秒时间戳
let iso = now.toISOString(); //转换为标准格式的字符串
console.log("当前时间的日期对象:" + now);
console.log("毫秒时间戳:" + ms);
console.log("标准格式的字符串:" + iso);
```

---
* 九九乘法表
``` js
for(var i = 1; i <= 9; i++){
    for(var j = 1; j <= i; j++){
        var str = "";
        str += j + "*" + i + "=" + (i * j) + ' ';
    }
    console.log(str);
}
---
### 02. 3D相册

``` html
<!DOCTYPE HTML>
<html>
<head>
<meta charset="UTF-8">
<meta name="KeyWords" content="">
<meta name="Description" content="">
<title>3D相册</title>
<style>
/*去掉内外边距*/
*{
	margin:0px;
	padding: 0px;
}
body{
	background-color:black; /*整个后面大的背景*/
	overflow: hidden; /*取消滚动条*/
	}
#perspective{
	/*设置景深*/
	perspective:800px;
}
  /*设置盛放照片的div*/
#wrap{
	width:120px;
	height: 180px;
	/*border:1px solid yellow;*/  /*建议学习的同仁把这个恢复后再运行，方便理解代码，但是印象美观*/
    position: relative;
    margin:0px auto;
    /*创建3D场景*/
    transform-style:preserve-3d;
    /*让照片出现后上下呈一定角度*/
    transform: rotateX(-10deg) rotateY(0deg);
}
/*给图片添加样式和属性*/
#wrap img{
	position:absolute;
	width:100%;
	height: 100%;
	border-radius: 5px;
	/*给照片添加圆角和阴影*/
	box-shadow: 0 0 2px pink;
	transform: rotateY(0deg) translateZ(0px);
	/*倒影：朝向 偏移 遮盖 */ /* 线性渐变(从哪里开始) 开始时候的颜色 结束时候的颜色*/
	 -webkit-box-reflect:below 5px -webkit-linear-gradient(top,rgba(0,0,0,0) 10%,rgba(0,0,0,0.5) 60%);
	}
/*底座光环*/
#wrap p{
	width:1200px;
	height: 1200px;
	/*径向渐变 (从哪里开始) 扩散程度
	开始时候的颜色  结束时候的颜色*/
	background:-webkit-radial-gradient(center center,600px 600px,rgba(242,23,134,0.2), rgba(0,0,0,0));
	border-radius:100%;
	position: absolute;
	top:102%;
    left: 50%;
    margin-left:-600px;
    margin-top: -600px;
    transform: rotateX(90deg);
}
</style>
<script type="text/javascript">
window.onload = function(){
	var oWrap = document.getElementById("wrap");
	var oImg = oWrap.getElementsByTagName("img");
	var oImgLength = oImg.length;
	var Deg = 360/oImgLength; //获取度数
	var nowX;
	var nowY;
	var lastX;
	var lastY;
	var minuseX = 0;
	var minuseY = 0;
	var roX = -10;
	var roY = 0;
	var timer;

	//给img设置旋转度
	for(var i = 0; i < oImgLength; i++){
		oImg[i].style.transform = 'rotateY('+i*Deg+'deg)translateZ(350px)'

		oImg[i].style.transition = 'transform 1s '+(oImgLength-1-i)*0.1+'s';
	}

	mTop();
		window.onresize = mTop;
		function mTop(){
			var wH = document.documentElement.clientHeight;
			oWrap.style.marginTop = wH / 2 - 180 + 'px';
		}
	//  三个鼠标事件
    //  按下   按下后移动   提起

    //  第一个
	document.onmousedown = function(ev){
		var ev = ev||window.event;
		lastX = ev.clientX;
		lastY = ev.clientY;

		//鼠标移动
		this.onmousemove = function(ev){
			var ev = ev||window.event;
			clearInterval(timer);
		//拿到当前坐标的值：
			nowX = ev.clientX;
			nowY = ev.clientY;
		//获取差值
			minuseX = nowX -lastX;
			minuseY = nowY - lastY;
		//更新wrap的旋转角度，拖拽越快--> minus变化越大->
        //roY变化越大  旋转越快
			roX -= minuseY*0.1;
			roY += minuseX*0.2;
			console.log(roX);
			// console.log("当前点X坐标"+lastX)
            // console.log("当前点Y坐标"+lastY)

			oWrap.style.transform = 'rotateX('+roX+'deg) rotateY('+roY+'deg)';
			lastX = nowX;
			lastY = nowY;
		}
		// 第三个事件  提起
		this.onmouseup = function(){
			this.onmousemove = null;
			timer = setInterval(function(){
				minuseX *= 0.95; //让距离越来越小，乘以摩擦系数
				//让差值无限次乘以一个小数  值会无限接近零 但不会等于零
                //console.log(minuseX)
				minuseY *= 0.95;
				roY += minuseX*0.2;
				roX -= minuseY*0.1;
				oWrap.style.transform = 'rotateX('+roX+'deg)rotateY('+roY+'deg)';
				if(Math.abs(minuseX)<0.2 && Math.abs(minuseY)<0.1){
					clearInterval(timer);
				}

			},13)
		}
		return false; //取消鼠标默认事件
	}
}
</script>
</head>
<body>
<div id="perspective">
	<div id="wrap">
		<img src="img/1.jpg" alt="">
		<img src="img/2.jpg" alt="">
		<img src="img/3.jpg" alt="">
		<img src="img/4.jpg" alt="">
		<img src="img/5.jpg" alt="">
		<img src="img/6.jpg" alt="">
		<img src="img/7.jpg" alt="">
		<img src="img/8.jpg" alt="">
		<img src="img/9.jpg" alt="">
		<img src="img/10.jpg" alt="">
		<img src="img/11.jpg" alt="">
		<img src="img/12.jpg" alt="">
		<p></p>
	</div>
</div>
</body>
</html>
```
---
### 03. 26个小写字母
``` javascript
window.onload = function(){
    var oBody = document.body;
    var aInp = document.getElementsByTagName('input');
    var arr = str.split('');
    for(var i = 0; i < arr.length; i++){
        oBody.innerHTML += '<input type = "button" value = "0">';
    }
    for(var i = 0; i < aInp.length; i++){
        aInp[i].num = 0;
        aInp[i].onclick = function(){
            this.value = arr[this.num];
            this.num++;
            if(this.num === arr.length){
                this.num = 0;
            }
        }
    }
}

```
---
### 04. 定义表格
``` html
<!DOCTYPE>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>定义表格</title>
</head>
<body>
<table width="600" border="1">
  <caption>2025年软件工程班课程表</caption>
  <tr><td>节次</td><td>星期一</td><td>星期二</td><td>星期三</td><td>星期四</td><td>星期五</td></tr>
  <tr><td>第1-2节课</td><td>大学英语</td><td>Web前端开发</td><td>高等数学</td><td>数据结构实验</td><td>体育</td></tr>
  <tr><td>第3-4节课</td><td>大学物理</td><td>星期二</td><td>高等数学</td><td>数据结构</td><td>Web前端开发</td></tr>
</table>
</body>
</html>
```
---
### 05. 20000个彩色数字代码实现
``` html
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>20000个彩色数字代码实现</title>
    <style type="text/css">
        li {
            list-style: none;
            float: left;
            height: 100px;
        }
        input {
            width: 50px;
            height: 50px;
        }
    </style>
    <script>
        window.onload = function(){
            var oUl = document.getElementById('list');
            var aBtn = oUl.getElementsByTagName('input');
            var arr = ['red', 'yellow', 'green', 'olive', 'teal', 'purple'];
            var len = 20000;
            var str = '';
            for(var i = 0; i < len; i++){
                str += '<li><input type="button"></li>';
            }
            oUl.innerHTML = str;
            for(var i = 0; i < aBtn.length; i++){
                aBtn[i].index = i;
                aBtn[i].style.background = arr[i % arr.length];
                aBtn[i].value = i + ': ' + String.fromCharCode(i);

                aBtn[i].onmouseover = function(){
                    this.style.background = '#fff';
                }
                aBtn[i].onmouseout = function(){
                    this.style.background = arr[this.index % arr.length];
                }
            }
        }
    </script>
</head>
<body>
    <ul id="list">
        <input type="text">
    </ul>
</body>
</html>
```
---
### 06. 30000个彩色按钮，快速算法
``` html
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>30000个彩色按钮，快速算法</title>
    <style type="text/css">
        li {
            list-style: none;
            float: left;
            height: 100px;
            margin-right: 4px;
        }
        input {
            width: 50px;
            height: 50px;
        }
    </style>
    <script>
        window.onload = function(){
            var oUl = document.getElementById('list');
            var aBtn = oUl.getElementsByTagName('input');
            var arr = ['red', 'yellow', 'green', 'lime', 'navy', 'aqua', 'fuchsia', 'maroon', 'olive', 'teal', 'purple'];
            var len = 30000;
            var str = '';
            for(var i = 0; i < len; i++){
                str += '<li><input type="button" value="按钮"></li>';
            }

            // 采用这种计算，可以快速的进行运算，从而大大的提高浏览器的运行速度。
            oUl.innerHTML = str;
            for(var i = 0; i < aBtn.length; i++){
                aBtn[i].index = i;
                aBtn[i].style.background = arr[i % arr.length];

                aBtn[i].onmouseover = function(){
                    this.style.background = '#000';
                }
                aBtn[i].onmouseout = function(){
                    this.style.background = arr[this.index % arr.length];
                }
            }
        }
    </script>
</head>
<body>
    <ul id="list">
    </ul>
</body>
</html>
```
---
### 07. 节点
* 文本节点和元素节点
``` javascript
// IE6-8
// alert(oUl.childNodes.length);
for (var i = 0; i < oUl.childNodes.length; i++){
    // nodeTypes == 3    -> 文本节点
    // nodeTypes == 1    -> 元素节点
    // alert(oUl.childNodes[i].nodeType);
    if(oUl.childNodes[i].nodeType == 1){
        oUl.childNodes[i].style.background = 'red';
    }
}
```
* children
``` js
window.onload = function(){
    var oUl = document.getElementById("ul1");
    alert(oUl.children.length;)
}
```
---
### 08. concat join split
* join
``` js
window.onload = function (){
    var oP = document.getElementsByTagName('p')[0];
    var arr1 = [1, 2, 3];
    var arr2 = [4, 5, 6];
    var arr3 = [7, 8, 9];
    alert(arr1.concat(arr2, arr3));
    // ['1', '2', '3', '4', '5', '6', '7', '8', '9']

    alert((arr1.concat(arr2, arr3)).length);

    var str = '';
    str = arr1.concat(arr2, arr3).join(',');
    oP.innerHTML = str;
    // 1, 2, 3, 4, 5, 6, 7, 8, 9
}
```
* split
``` js
var str = 'abvcddssa';
alert(str.length);
alert(str.split('').join(',').length); //17
```
---
### 09. Div层叠的进化问题
* div 层叠
``` html
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>Div层叠的进化问题</title>
    <style type="text/css">
        body {
            margin: 0; /* margin 表示边距 */
        }
        div {
            width: 200px;
            height: 200px;
            position: absolute;
            top: 0;
            left: 0;
            font-size: 30px;
            text-align: center;
            color: #fff;
        }
    </style>
    <script>
        window.onload = function(){
            var oUl = document.getElementsByTagName('ul')[0];
            var aDiv = oUl.getElementsByTagName('div');
            var arrColor = ['red', 'yellow', 'green', 'lime', 'navy', 'aqua', 'fuchsia', 'maroon', 'olive', 'teal', 'purple'];
            var str = '';
            for(var i = 0; i < arrColor.length; i++){
                str += '<div></div>';
            }
            oUl.innerHTML = str;

            for(var i = 0; i < aDiv.length; i++){
                aDiv[i].index = i;
                aDiv[i].style.background = arrColor[i % arrColor.length];

                aDiv[i].onmouseover = function(){
                    this.style.background = '#ccc';
                }
                aDiv[i].onmouseout = function(){
                    this.style.background = arrColor[this.index % arrColor.length];
                }
            }

            for(var i = 0; i < aDiv.length; i++){
                aDiv[i].style.left = 10 + 50 * i + 'px';
                aDiv[i].style.top = 10 + 50 * i + 'px';
            }
        }
    </script>
</head>
<body>
    <ul></ul>
</body>
</html>
```

---
### 10. div的显示和隐藏与block的关系
``` html
<!doctype html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>div的显示和隐藏与block的关系</title>
    <style type="text/css">
        #div1 {
            width: 200px;
            height: 200px;
            background: #ccc;
        }
    </style>
    <script>
        window.onload = function (){
            var oBtn1 = document.getElementById('show_btn');
            var oBtn2 = document.getElementById('hide_btn');
            var oDiv1 = document.getElementById('div1');

            oBtn1.onclick = function (){
                oDiv1.style.display = 'block';
                oDiv1.style.background = 'yellow';
                oDiv1.style.width = '300px';
            }

            oBtn2.onclick = function () {
                oDiv1.style.display = 'none';
            }
        }
    </script>
</head>
<body>
    <input id = "show_btn" type="button" value="显示">
    <input id = "hide_btn" type="button" value="隐藏">
    <div id = "div1" style = "display:"></div>
</body>
</html>
```
### 11. div 与 span
``` html
<!doctype html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>div 与 span</title>
    <style type="text/css">
    div {
        background-color: black;
        color: white;
        height: 2em;
        margin: 2px; /* margin 表示边距 */
    }
    .inline_disp {
        display: inline; /* 改变div显示方式 */
    }
    .block_disp {
        display: block; /* 改变span显示方式 */
        height: 2em;
        background-color: rgb(200, 200, 200);
        margin: 2px;
    }
    </style>
</head>
<body>
    <div id = "d1">这是div1</div>
    <div id = "d1">这是div2</div>
    <span di = "s1">这是span1</span>
    <span di = "s2">这是span2</span>
    <div id = "d3" class = "inline_disp">这是div3</div>
    <div id = "d4" class = "inline_disp">这是div4</div>
    <span id = "s3" class = "block_disp">这是span3,在使用CSS排版的页面中div标记和span标记是两个常用的标记，利用这两个标记，加上CSS对其样式的控制，可以很方便地实现各种效果。</span>
    <span id = "s4" class = "block_disp">这是span4,在使用CSS排版的页面中div标记和span标记是两个常用的标记，利用这两个标记，加上CSS对其样式的控制，可以很方便地实现各种效果。</span>
</body>
</html>
```
---
### 12. 备注点
* document.getElementById
``` javascript
// document.getElementById('ul')中不能使用ul,而应该在<ul id = "lsit"></ul>中使用list等替代值
```

* join() 单字合并
``` html
<!doctype html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>join() 单字合并</title>
    <style type="text/css">
    div {
        width: 200px;
        height: 200px;
        border: 1px solid #333;
        background: #fff;
        padding: 20px;
        line-height: 40px;
        margin-bottom: 10px;
    }
    span {
        padding: 5px 15px;
        font-family: 微软雅黑;
    }
    </style>
</head>
<body>
    <div id = "div1">
    <!--
    <span style = "background: #ffc ">
    文
    </span>
    <span style = "background: #cc3 ">
    字
    </span>
    <span style = "background: #6fc">
    内
    </span>
    <span style = "background: #9c9">
    容
    </span>
    -->
    </div>
    <input type = "text">
    <input type = "button" value = "按钮">
    <script>
        var oDiv = document.getElementById("div1");
        var aInp = document.getElementsByTagName("input");
        var arrColor = ['#fcc', '#cc3', '#6fc', '#9c9'];

        aInp[1].onclick = function() {
            var str = aInp[0].value;
            var arr = str.split('');

            for(var i = 0; i < arr.length; i++) {
                arr[i] = '<span style = "background:'+ arrColor[i %     arrColor.length]+';">'+arr[i]+'</span>';
            }
            oDiv.innerHTML += arr.join('');
        }
    </script>
</body>
</html>
```

---
### 13. json

* json1

``` javascript
/*
var json = {name: 'leo', age: 32};
alert(json.name);  //leo

var arrUrl = ['images/01.png', 'images/02.png', 'images/03.png', 'images/04.png'];
var arrText = ['灵宠', '图片二', '图片三', '面具'];
var imgData = {
    url: ['images/01.png', 'images/02.png', 'images/03.png', 'images/04.png'],
    text: ['灵宠', '图片二', '图片三', '面具']
};
alert(imgData.url[2])  //images/03.png
*/

/*
var json2 = {name: 'miaov'};
alert(json2.name)  // miaov

var json2 = {'name': 'miaov'};
alert(json2['name']);
// json2.name = '妙味';
json2['name'] = '妙味';
alert(json2['name']); //妙味
*/

/*
var json3 = {abc: 123, xyz: ''};
var arr = [
    {'name': 'TM', 'age': 23},
    {'name': 'leo', 'age': 32},
];
alert(arr[0].name + '今年有' + arr[1]['age'])
*/

/*
var json4 = {'name':'miaov', 'age':'3', 'fun':'coding'};
for(var attr in json4) {
    alert(attr) // name age fun
    alert(json4[attr]); //miaov 3 coding
}
*/

/*
var json5 = {
    url: ['images/01.png', 'images/02.png', 'images/03.png', 'images/04.png'],
    text: ['灵宠', '图片二', '图片三', '面具']
}
for(var attr in json5){
    for (var i = 0; i < json5[attr].length; i++) {
        alert(json5[attr][i]);
    }
}
*/
```

---
### 14. html中的属性操作
* 1-js中html中的属性操作1,2

``` javascript
<!doctype html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>1-js中html中的属性操作1，2</title>
<!--
HTML属性操作：读 | 写
  属性名
  属性值
  属性读操作： 获取、找到
  元素.属性名
字符串链接
  属性的写操作： ("添加") 替换、修改
  元素.属性名 = 新的值
-->
<script>
window.onload = function (){
    var oBtn = document.getElementById('btn1')
    var oText = document.getElementById('text1')
    var oSelect = document.getElementById('select1');

    oBtn.onclick = function (){
        //alert(oBtn.type);
        //alert(oText.value);
        //alert(oSelect.value);

        //'淘宝' + '在' + '杭州' => '淘宝在杭州'
        alert(oText.value + '在' + oSelect.value)
    }
}
</script>
</head>
<body>
  <input id = "text1" type = "text">
  <select id ="select1">
    <option value = "北京">北京</option>
    <option value = "上海">上海</option>
    <option value = "杭州">杭州</option>
  </select>
  <input id = "btn1" type = "button" value = "按钮">
</body>
</html>
```
---
* 1-js中html中的属性操作3

``` html
<!doctype html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>1-js中html中的属性操作3</title>
    <script>
    window.onload = function (){
        var oBtn = document.getElementById('btn1')
        var oText = document.getElementById('text1')
        var oSelect = document.getElementById('select1');
        var oImg = document.getElementById('img1')

        oBtn.onclick = function (){
            //alert(oBtn.type);  button
            //alert(oText.value);  按钮
            //alert(oSelect.value); oSelect.value
              oImg.src = oText.value;

        }
    }
    </script>
    </head>
    <body>
      <input id = "text1" type = "text">
      <select id ="select1">
        <option value = "北京">北京</option>
        <option value = "上海">上海</option>
        <option value = "杭州">杭州</option>
      </select>
    <input id = "btn1" type = "button" value = "按钮">
    <img id = "img1" src = "img1.jpg" width = "300">
    </body>
    </html>
```

---
### 15. some snippets
* 设置图片的宽度和高度

``` html
<!doctype html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>设置图片的宽度和高度</title>
    <style>
        ul {
            list-style-type: none;
        }
        li {
            float: left;
            padding: 0 20px;
        }
    </style>
</head>
<body>
<center>
  <h2 align = "center">设置图片的宽度和高度</h2>
  <hr color = "#6600cc">
  <ul>
    <li><img src = "images/芙芙.png" alt="原图"></li>
    <li><img src = "images/芙芙.png" width="100px" alt="宽度为100px"></li>
    <li><img src = "images/芙芙.png" width="100px" height="50px" alt="宽75像素 高50像素"></li>
  </ul>
  <h3 align="center">设置图像的边框</h3>

  <hr color = "#6600cc">
  <ul>
    <li><img src = "images/芙芙.png" alt="边框宽度为0px"></li>
    <li><img src = "images/芙芙.png" width="100px" alt="边框宽度为5px" border="5px"></li>
    <li><img src = "images/芙芙.png" width="100px" height="50px" alt="边框宽度为10px" border="10px"></li>
  </ul>
</center>
</body>
```

* push unshift

``` javascript
var arr = [1, 2, 3];
console.log(arr.push('abc')); // 4
console.log(arr.length); // 3
for(let i = 0; i < arr.length; i++){
    console.log(arr[i]);
}

console.log(arr.unshift('hero'));  // 5
console.log(arr);  // hero, 1, 2, 3, abc
```

---

### 16. 时间
* 倒计时
  1. Date对象参数
      - 数字形式: new Date(2025,7,8,13,05,00);
      - 字符串形式: new Date('July 8,2025 13:05:00');
  1. 月份取值
      - January
      - February
      - March
      - April
      - May
      - June
      - July
      - August
      - September
      - October
      - November
      - December
  1. 时间转换公式
      - 天: Math.floor(t/86400)
      - 时: Math.floor(t%86400/3600)
      - 分: Math.floor(t%86400%3600/60)
      - 秒: Math.floor(t%60)
  1. 时间戳: getTime()
      - 返回从1970年1月1日0点0分0秒0毫秒

* 倒计时实例

``` javascript
// 现在的时间点 (在变)
// 未来的时间点 (不变)
var iNow = new Date();
var iNew = new Date(2100,7,8,13,20,00);

var t = Math.floor((iNew - iNow)/1000);
// 毫秒 -> 秒   Math.floor: 向下取整
alert(t);

var str = Math.floor(t/86400) + '天' + Math.floor(t%84600/3600) + '时' + Math.floor(t%86400%3600/60) + '分' + Math.floor(t%60) + '秒';

alert(str);

```
---

### 17. Jquery
* **Jquery 设计思想**

1. **选择网页元素**
  - CSS选择器
    * $(document) //选择整个文档对象
    * $('#myId') //选择ID为myId的网页元素
    * $('div.myClass')//选择class为myClass的div元素

  - Jquery特有的表达式
    * $('a:first') //选择网页中第一个a元素
    * $('tr:odd') //选择表格的奇数行
    * $('div:visible') //选择可见的div元素

  - 实例:
  ``` html
  <!doctype html>
  <head>
    <meta charset="utf-8">
    <title>jquery</title>
    <script src="https://code.jquery.com/jquery-3.7.1.js" integrity="sha256-eKhayi8LEQwp4NKxN+CfCh+3qOVUtJn3QNZ0TciWLP4=" crossorigin="anonymous"></script>
  </head>
  <body>
    <ul>
        <li>原神</li>
        <li>丝科克</li>
        <li>芙芙</li>
        <li>美露莘</li>
    </ul>
    <script>
        $('li:first').css('background','red');
        $('ul li:last-child').css('background','pink');
    </script>
  </body>
  </html>
  ```
---
2. **方法函数化**
  - 方法函数化
    * 原生的
      - window.onload
      - innerHTML
      - onclick

    * Jquery
      - $()
      - html()
      - click()

    * 实例

    ``` javascript
    /*
    window.onload = function () {
        var oDiv = document.getElementById("div1");
        oDiv.onclick = function () {
          alert(this.innerHTML);
        }
    }
    */

    $(function(){
        $('#div1').click(function(){
            alert( $(this).html() );
        })
    })

    ```
---
3. **原生与JQ**
  - 原生、JQ可以共存
    * $("#div1").html()
    * oDiv.innerHTML

  - 原生、JQ不能混用
    * $("div1").innerHTML
    - oDiv.html()

  - 实例
  ``` javascript
  $(function(){
    $('#div1').click(function()P{
      // alert( $(this).html() ); //jq
      // alert( this.innerHTML); //js
      alert( $(this).innerHTML ); // 错误
      alert( this.html() );  //错误

    })
  })

  ```
---
4. **改变结果集**
  - 强大的过滤器
    * $('div').has('p'); //选择包含p元素的div元素
    * $('div').not('.myClass'); //选择class不等于myClass的div元素
    * $('div').filter('.myClass'); //选择class等于myClass的div元素

  - 相邻元素查找
    * $('div').next('p'); // 选择div元素后面的第一个p元素
    * $('div').parent(); // 选择div元素的父元素
    * $('div').children(); // 选择div的所有子元素

  - 实例1

  ``` html
  <!doctype html>
  <head>
    <meta charset="utf-8">
    <title>改变结果集</title>
    <script src="https://code.jquery.com/jquery-3.7.1.js" integrity="sha256-eKhayi8LEQwp4NKxN+CfCh+3qOVUtJn3QNZ0TciWLP4=" crossorigin="anonymous"></script>
    <script>
        $(function(){
            $('div').has('p').css('background', 'pink');
        })
    </script>
  </head>
  <body>
    <div>
        原神
        <p>"原始之神"或"神之根源"</p>
    </div>
    <div>
        Genshin Impact
        <span></span>
    </div>
  </body>
  </html>
  ```

  - 实例2:

  ``` html
  <!doctype html>
  <head>
    <meta charset="utf-8">
    <title>改变结果集</title>
    <script src="https://code.jquery.com/jquery-3.7.1.js" integrity="sha256-eKhayi8LEQwp4NKxN+CfCh+3qOVUtJn3QNZ0TciWLP4=" crossorigin="anonymous"></script>
    <script>
        $(function(){
            $('div').next('p').css('background', 'pink');

        })
    </script>
  </head>
  <body>
    <div>书卷一梦</div>
    <p>李一桐</p>

    <div>智能Ai时代</div>
    <span>ChatGPT</span>
    <p>人工智能的时代的正式到来，以ChatGPT的横空出世为标志。</p>
  </body>
  </html>
  ```

---
5. **链式操作**
* 链式操作
  - $('div').find('h3').eq(2).html('Hello');
    * $('div') //找到div元素
    * .find('h3') //选择其中的h3元素
    * .eq(2) //选择第3个h3元素
    * .html('Hello'); //将它的内容改为Hello

  - jQuery还提供了.end()方法，使得结果集可以后退一步。

  - 实例

  ``` html
  <!doctype html>
  <head>
    <meta charset="utf-8">
    <title>改变结果集</title>
    <script src="https://code.jquery.com/jquery-3.7.1.js" integrity="sha256-eKhayi8LEQwp4NKxN+CfCh+3qOVUtJn3QNZ0TciWLP4=" crossorigin="anonymous"></script>
    <script>
        $(function(){
            $('div').find('p').eq(3).css('background', 'pink');
        })

        /*
        var oDiv = $('div');
        var aP = oDiv.find('p');
        var oP_3 = aH3.eq(2);
        oP_3.css('background', 'pink');

        $('div').find('p').eq(2).css('background', 'pink').end().eq(1).css('background', 'yellow');
        */

    </script>
  </head>
  <body>
    <div>
    <h3>回乡偶书 - 贺知章</h3>
      <p>少小离家老大回</p>
      <p>乡音无改鬓毛催</p>
      <p>儿童相见不相识</p>
      <p>笑问客从哪里来</p>
    </div>
  </body>
  </html>
  ```
---
6. **取值与赋值合体**
  - $('h1').html(); //html()没有参数，表示取出h1的值
  - $('h1').html('Hello'); //html()有参数Hello,表示对h1进行赋值

  - .val()
  - .attr()
  -.width()

  - 取值是一组中的第一个元素，赋值是所有的元素

  - 实例

  ``` html
  <!doctype html>
  <head>
    <meta charset="utf-8">
    <title>取值与赋值合体</title>
    <script src="https://code.jquery.com/jquery-3.7.1.js" integrity="sha256-eKhayi8LEQwp4NKxN+CfCh+3qOVUtJn3QNZ0TciWLP4=" crossorigin="anonymous"></script>
    <script>
    $(function(){
        //alert( $('p').html() ); //取值： 一组中的第一个元素
        // $('p').html('不知细叶谁裁出'); // 赋值： 一组中的所有元素。

        $('h3').html('咏柳 - 贺知章')
        $('p').html('碧玉妆成一树高'); // 赋值： 一组中的所有元素。
        $('p').eq(0).html('碧玉妆成一树高');
        $('p').eq(1).html('万条垂下绿丝绦');
        $('p').eq(2).html('不知细叶谁裁出');
        $('p').eq(3).html('二月春风似剪刀');

    })
    </script>
  </head>
  <body>
    <div>
    <h3>回乡偶书 - 贺知章</h3>
      <p>少小离家老大回</p>
      <p>乡音无改鬓毛催</p>
      <p>儿童相见不相识</p>
      <p>笑问客从哪里来</p>
    </div>
  </body>
  </html>
  ```
---
7. **元素移形换位**
  - 直接移动该元素
    * $('div').insertAfter($('p')); //把div元素移到p元素后面
    * $('div').appendTo($('p'));

  - 移动其他元素
    * $('p').after($('div')); //把p元素加到div元素前面
    * $('div').append($('p'));

  - 区别: 操作的元素不同

  ``` javascript
  $(function(){
    // $('div').insertAfter( $('p') );
    // $('p').after( $('div') );
    // $('div').insertAfter( $('p') ).css('background','red');

    $('p').after($('div')).css('background','red');
  })

  ```
---
8. **强大的创建**

``` javascript
   $('#ul1').append('<li>aaa</li>');

  // var oLi = $('<li>');
  // oLi.html('aaaa');
  // $('#ul1').append(oLi);

  // clone()
```
---
9. **工具方法**
  - 构造函数上的方法
    * $.each([],function(){})
    * $.trim($('div').attr('class'))

  - 原型上的方法
    * $('div').each(function(){})

  - 实例:
  ``` javascript
  /*
  $(function(){
    // $('li').css('background', 'pink');

    $('li').each(function(){ //第一个参数:索引； 第二个参数:所有获取的元素
      $(elements).html( index );
    });

  })
  */
  window.onload = function(){
    var aLi = document.getElementsByTagName(
        'li');

    $.each(aLi,function(index, elements){
      elements.innerHMTL = index;
    })

  }

  ```

---
### 18. return 注意事项


---
![alt text](https://upload-bbs.miyoushe.com/upload/2022/11/01/266607709/6cc988d046df34315681e50f9c9f299c_1259576169906078498.PNG?x-oss-process=image//resize,s_600/quality,q_80/auto-orient,0/interlace,1/format,png)