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
* 3D相册实例

``` html
<!DOCTYPE html>
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
<!DOCTYPE html>
<html>
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
<!DOCTYPE html>
<html>
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
<!DOCTYPE html>
<html>
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
<!DOCTYPE html>
<html>
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
<!DOCTYPE html>
<html>
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
<!DOCTYPE html>
<html>
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
  <!DOCTYPE html>
  <html>
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
  <!DOCTYPE html>
  <html>
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
  <!DOCTYPE html>
  <html>
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
  <!DOCTYPE html>
  <html>
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
  <!DOCTYPE html>
  <html>
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
  $(function(){
    // $('li').css('background', 'pink');

    $('li').each(function(){ //第一个参数:索引； 第二个参数:所有获取的元素
      $(elements).html( index );
    });
  })

  window.onload = function(){
    var aLi = document.getElementsByTagName(
        'li');

    $.each(aLi,function(index, elements){
      elements.innerHMTL = index;
    })

  }
  ```

---
### 18. 函数
* **return**
  - 实例1: 报错，说明网页环境有特殊限制。尝试在 空标签页 (about:blank) 中新建 Snippet 执行，或在无痕窗口测试。

  ``` javascript
  function fn1(n){
      const arr = [];
      for (let i = 1; i <= n; i++){
          arr.push(i);
      }
      return arr;
  }

  console.log(fn1(5));  // [1, 2, 3, 4, 5]
  console.log(fn1(7));  // [1, 2, 3, 4, 5, 6, 7]

  console.log(fn4 ());
  function fn4 (){
      return;  //默认返回值为未定义
  }

  console.log(fn5());
  function fn5 () {
      return 123; //弹出123，后面的521不出现.
    alert(521); //alert(521)在return后面故此无法弹  出。
  }
  alert(520); //alert(520)在函数外面，和return无关。

  /*
  return的注意事项：
  1. 函数名 + 括号： fn1 () ==> return 后面的值；
  2. 所有函数默认值返回值： 未定义
a) 解析：在 JavaScript 中，每个函数在默认情况下都会返回一个特殊值 undefined（未定义），除非你显式地使  用 return 语句指定其他返回值。
b) 当函数内部没有 return 语句时，JavaScript 引擎会  自动在函数末尾添加 return undefined
c) undefined 是 JavaScript 原始类型之一，表示"无值"  的状态，与 null（空值）不同。
  3. return后面任何代码都不执行。
  */

  ```
* **箭头函数**
  - 遍历数组

  ``` javascript
  [1, 2, 3].forEach(item => {
      console.log(item)
  })
  ```

  - 遍历数组进行幂运算

  ``` javascript
  [1, 2, 3, 4, 5, 6, 7, 8, 9].forEach(n =>{
      console.log(n ** 3); //或者
      console.log(Math.pow(n, 3));
  })

  // 优先使用下面的方法
  const logCube = n => console.log(n ** 3);
  [1, 2, 3].forEach(logCube);

  // 注意运算符优先级
  console.log(n ** 3); //等价于
  console.log(n * n * n)

  ```
---
* script标签的注意事项
  - 实例

  ``` html
  <!DOCTYPE html>
  <html>
  <head>
    <meta http-equiv = "Content-Type" content = "text/html"; charset = "utf-8">
    <title>script标签的注意事项</title>
    <script>
    //alert(detectNum('123aaa456')); // 检测 '123aaa456'中是否包含数字

    window.onload = function () {
        var aInp = document.getElementsByTagName('input');

        aInp[1].onclick = function () {
            var val = aInp[0].value;
            if (detectNum(val)){
                alert('恭喜,' + val + '全是数字')
            }else{
                alert('输入有误');
            }
        }

        function detectNum(str) {
            var n = 0;
            for (var i = 0; i < str.length; i++) {
                n = str.charCodeAt(i);
                if(n < 48 || n > 57) return false;
            }
                  return true;
        }
    }

    // script标签在head标签里面时，要用window.onload函数包裹。在body里面则不需要。
    </script>
  </head>
  <body>
    <input type="text">
    <input type="button" value="按钮">
  </body>
  <html>
  ```

* **shake 左摇右摆|过时代码**
  - shake

  ``` javascript
  // getStyle
  function getStyle(obj, attr) {
      return obj.currentStyle ?  obj.currentStyle[attr] : getComputedStyle(obj, false)[attr];
  }

  function shake(obj, attr, endFn) {
    var pos = parseInt(getStyle(obj, attr));
    var arr = [];
    var num = 0;
    var timer = null;

    for (var i = 20; i > 0; i -= 2) {
        arr.push(i, -i);
    }
    arr.push(0);
    //alert(arr);

    clearInterval(obj.shake);
    obj.shake = setInterval(function(){
        obj.style[attr] = pos + arr[num] + 'px';
        num++;
        if(num === arr.length) {
            clearInterval(obj.shake);
            endFn && endFn();
        }
    },50)
  }

  function fnshake() {
    var _this = this;
    shake(_this, 'left', function(){
        shake(_this,'top');
    })
  }
// 技术的终极目标不是制造焦虑，而是拓展人类可能性边界。
  ```

* **sort排序问题的应用**
  - sort
  - 实例

  ``` javascript
  var arr = ['c', 'd', 'a', 'e'];
  arr.sort();
  console.log(arr);

  var arr2 = [4, 3, 2, 23, 43, 57, 908, 32, 39, 47, 83, 65];
  arr2.sort(function(a, b){
    return a - b;
  })
  console.log(arr2); //正序

  arr2.sort(function(a, b){
    return b - a;
  })
  console.log(arr2); //倒序

  var arrWidth = ['345px', '23px', '10px', '1000px'];
  /*
  arrWidth.sort(function(a, b){
    return parseInt(a, 10) - pareseInt(b, 10);
  })
  */
  // 排序逻辑优化(箭头函数简化)

  arrWidth.sort((a, b) => parseInt(a, 10) - parseInt(b, 10))
  console.log(arrWidth);
  /*
    方案1：Number() 转换
arrWidth.sort((a, b) => Number(a.slice(0, -2)) - Number(b.slice(0, -2)));

    方案2：一元运算符（更简洁）
arrWidth.sort((a, b) => +a.slice(0, -2) - +b.slice(0, -2));
  */
  ```
* **splice**
  - splice() 是 JavaScript 中数组（Array）的一个非常强大的方法，用来 添加、删除、或替换数组中的元素。它会修改原数组，并返回被删除的元素组成的新数组。
  - 基本语法

  ``` js
  array.splice(start, deleteCount, item1, item2, ...)
  ```
  - 参数说明
  | 参数                  | 说明                        |
| ------------------- | ------------------------- |
| `start`             | 必需。开始更改的索引（从 0 开始）        |
| `deleteCount`       | 可选。要删除的元素个数               |
| `item1, item2, ...` | 可选。要添加的新元素（插入位置为 `start`） |

  - 示例讲解：
    1. 删除元素

    ``` javascript

    let arr = [1, 2, 3, 4, 5];
    let removed = arr.splice(2, 2); // 从索引2开始，删除2个元素
    console.log(arr);     // [1, 2, 5]
    console.log(removed); // [3, 4]
    ```

    * 解析
    | 表达式                | 结果          | 说明             |
| ------------------ | ----------- | -------------- |
| `arr.splice(2, 2)` | `[3, 4]`    | 删除索引 2 开始的两个元素 |
| `arr`（操作后）         | `[1, 2, 5]` | 原数组中被删除了两个元素   |
| `removed`          | `[3, 4]`    | 保存被删除的两个元素     |

    ---
    2. 添加元素

    ``` javascript
    let arr = [1, 2, 5];
    arr.splice(2, 0, 3, 4); // 从索引2开始，不删除，插入3和4
    console.log(arr); // [1, 2, 3, 4, 5]
    ```

    3. 替换元素

    ``` javascript
    let arr = [1, 2, 3, 4, 5];
    arr.splice(1, 2, 9, 8); // 从索引1开始，删除2个元素，插入9和8
    console.log(arr); // [1, 9, 8, 4, 5]
    ```

    4. 删除直到数组尾部

    ``` javascript
    let arr = [1, 2, 3, 4, 5];
    arr.splice(3); // 从索引3开始删除到末尾
    console.log(arr); // [1, 2, 3]
    ```

    5. 负数索引(从尾部开始数)

    ```
    let arr = [1, 2, 3, 4, 5];
    arr.splice(-2, 1); // 从倒数第2个开始，删除1个
    console.log(arr); // [1, 2, 3, 5]
    ```

    6. 关于负数索引

    ``` javascript
    arr.splice(start, deleteCount)
    ```

      - 如果 start 是负数，表示从数组末尾倒数第 start 个元素开始。
      - 例如 -1 表示“最后一个”，-2 表示“倒数第二个”。

    * 为什么 splice() 支持负数，而 arr[-1] 不行？

     | 项目                   | 是否支持负索引   | 原因/说明               |
| -------------------- | --------- | ------------------- |
| `arr[index]`         | ❌         | 标准数组访问语法，不支持负数索引    |
| `arr.at(index)`      | ✅（ES2022） | 新增方法，明确支持负数索引       |
| `splice(start, ...)` | ✅         | 内建方法内部实现对负数参数做了转换处理 |

  ---
  - 总结
   | 操作 | 示例                | 结果                 |
| -- | ----------------- | ------------------ |
| 删除 | `splice(i, n)`    | 删除 `i` 位置起 `n` 个元素 |
| 添加 | `splice(i, 0, x)` | 在 `i` 位置插入 `x`     |
| 替换 | `splice(i, n, x)` | 删除 `n` 个并插入 `x`    |

  ---
  - 实例

  ``` javascript
  //删除、替换、添加
  var arr = ['Genshin', '丝柯克', '芙芙', '夏洛蒂'];
  // ['深渊上半', '丝柯克', '芙芙', '夏洛蒂']
  arr.splice(0, 1, '深渊上半');
  //  ['深渊上半', '丝柯克', '芙芙', '夏洛蒂', '茜特拉利']
  arr.splice(arr.length, 0, '茜特拉利');
  /*
  arr.length 表示数组最后一个索引之后的位置
  0 表示不删除任何元素
  '茜特拉利' 要插入的值
  */
  console.log(arr);
  ```
---
* **splice容易混淆的点**
  - `splice()` 方法确实很容易让人搞混，尤其是：
    * 起始索引是从哪“开始算”的？
    * 删除的元素“包括不包括起点”？
    * 负数到底是从哪“倒着”算？
---

#### 🧠 `splice(start, deleteCount)` 背后的逻辑

1. 语法回顾：

```js
array.splice(start, deleteCount, item1?, item2?, ...)
```

2. 重点说明：

| 参数            | 说明                                                 |
| ------------- | -------------------------------------------------- |
| `start`       | 从哪个索引**开始删除**。这个索引是**包括的**（inclusive）。可以是负数（倒数位置）。 |
| `deleteCount` | 要删除的元素个数（从 `start` 开始往后数）                          |
| 后续参数          | 用来插入到被删除位置的新元素（可选）                                 |

---

3. 一句话记住：

> `splice()` 会从 `start` 开始，**包含这个位置**，往后删除 `deleteCount` 个元素。

---

4. 正数索引例子（从头开始数）：

```js
let arr = ['a', 'b', 'c', 'd', 'e'];
arr.splice(1, 2); // 从索引1开始，删除2个
console.log(arr); // ['a', 'd', 'e']
```

**解释：**

* 索引 `1` 是 `'b'`，开始删。
* 删除 `'b'`（索引1）和 `'c'`（索引2）。
* 所以剩下 `'a', 'd', 'e'`。

---

5. 负数索引例子（从尾部开始数）：

```js
let arr = ['a', 'b', 'c', 'd', 'e'];
arr.splice(-3, 1); // 删除倒数第3个
console.log(arr); // ['a', 'b', 'd', 'e']
```

6. **解释：**

* `-3` 对应的是索引 `2` → 元素 `'c'`。
* 删除 `'c'`。

---

7. **图解（索引位置）**：

```
正序索引：   0     1     2     3     4
           ['a', 'b', 'c', 'd', 'e']
反序索引：  -5   -4    -3    -2    -1
```

---

8. 负数计算公式（转换为正数）：

```js
实际索引 = arr.length + start;
```

例：`arr.splice(-2, 1)`
→ `start = 5 + (-2) = 3`
→ 实际从索引 `3`（元素 `'d'`）开始删。

---

9. 插入操作：

还可以插入元素：

```js
let arr = ['a', 'b', 'c'];
arr.splice(1, 0, 'X'); // 在索引1处插入'X'，不删除任何元素
console.log(arr); // ['a', 'X', 'b', 'c']
```

---

10. 总结口诀：

| 用法                | 说明                     |
| ----------------- | ---------------------- |
| `splice(i, n)`    | 从索引 `i` 开始，删掉 `n` 个元素  |
| `splice(-k, n)`   | 从倒数第 `k` 个元素开始，删 `n` 个 |
| `splice(i, 0, x)` | 在索引 `i` 插入 `x`，不删除     |
| 起始索引（`i`）         | **包含**这个位置             |

 11. 关键要点：
   * 包含起始位置：start 表示从数组的哪个索引开始操作，这个索引的元素会被计算删除或替换。
   * 负数索引：负数 start 表示从数组末尾倒数计算位置，例如 -1 表示最后一个元素，-2 表示倒数第二个。
   * 删除与插入同时进行：如果提供了新元素，先删除，再从 start 插入这些元素。
   * deleteCount 为 0 表示纯插入，不删除元素。

  12. 题目:
    > 从数组 [1, 2, 3, 4, 5, 6] 中删除倒数第 4 和倒数第 3 个元素。

    ``` js
    let arr = [1, 2, 3, 4, 5, 6];
    // 请写出 splice 语句

    arr.splice(-4, 2);
    /* 分析：
    1. start = -4 表示从倒数第4个元素开始删除
    2. 要删除倒数第4和倒数第3这两个元素，所以删除数量是 2
    */

    ```

---
* **arr.splice(-3, 2)**
  > 表示从倒数第 3 个元素开始，删除它以及它后面的 1 个元素，总共删除 2 个。
  > splice(负数, n) → 从倒数第 N 位开始，删 n 个（向后）
  > 实例

  ``` js
  let arr = ['a', 'b', 'c', 'd', 'e', 'f'];
  let removed = arr.splice(-3, 2);
  console.log(removed); // ['d', 'e']
  console.log(arr);     // ['a', 'b', 'c', 'f']
  ```
---
* **shift、 unshift、 pop、push**
  - 四个方法先列出来
   | 方法          | 作用    | 操作部位 | 是否删除 | 是否添加 |
| ----------- | ----- | ---- | ---- | ---- |
| `push()`    | 尾部加元素 | 尾巴   | ❌    | ✅    |
| `pop()`     | 尾部删元素 | 尾巴   | ✅    | ❌    |
| `unshift()` | 头部加元素 | 头部   | ❌    | ✅    |
| `shift()`   | 头部删元素 | 头部   | ✅    | ❌    |
  - 口诀:
    > “尾巴 pop push，头部 shift unshift。”
    > “头 shift 尾 pop，头 unshift 尾 push。”
  - 图解记忆法(想象盒子)

  ``` scss
  [       A       B       C       D       ]
         ↑                       ↑
      shift()               pop() ← 删除
      unshift()             push() ← 添加

  ```

  - 类比法：

  | 行为        | 方法          | 类比     |
| --------- | ----------- | ------ |
| 从后面塞一个元素  | `push()`    | ➕ 尾部进货 |
| 从后面拿走一个元素 | `pop()`     | ➖ 尾部出货 |
| 从前面塞一个元素  | `unshift()` | ➕ 头部进货 |
| 从前面拿走一个元素 | `shift()`   | ➖ 头部出货 |
  - 联想

  | 如果你是一个搬运工...       |
| ------------------ |
| 🛒 push → 把货物推到队尾  |
| 🪓 pop → 从队尾砍掉一个   |
| 💡 shift → 把队首挪掉   |
| ➕ unshift → 从前面塞进去 |

---
### 19. split join 应用
* **split join原理在查找替换方面的应用**

``` html
<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>split join原理在查找替换方面的应用</title>
    <style type="text/css">
      p {
        border: 10px solid #ccc;
        background: #FFC;
        width: 400px;
        padding: 20px;
        font-size: 16px;
        font-family: 微软雅黑
      }
      span {
        background: yellow;
      }
    </style>
</head>
<body>
  <input type = "text">
  <input type = "text">
  <input type = "button" value = "替换">
  <p>小时候经常锄地，得空的时候总要去看动画片，全然没有主动学习的意识。当时若把时间合理得分配一下，学习的压力也不会陡然来袭。岁月不能回转，时光只能向前，唯有总结经验教训，才能吃一堑长一智。世界发展出奇的快，紧赶慢赶还是拉了一大截，互联网时代开启了所有人的智慧，所思所想，所感所悟，网上都可以找到借鉴，知识的获取变得异常便捷，但也要看到人类早就把自己局限在了认知范围内，大数据推荐更是创造了信息茧房，人类虽然获取知识的途径变多了，但也被固有得经验所诅咒，无法突破信息封锁。</p>
  <script>
    var aInp = document.getElementsByTagName('input');
    var oP = document.getElementsByTagName('p')[0];

    aInp[2].onclick = function() {
      var str = aInp[0].value;
      var newStr = aInp[1].value;

      if(!str) return;
      oP.innerHTML = oP.innerHTML.split(str).join('<span>' + newStr + '</span>');
    }
  </script>
</body>
</html>
```

---
### 20. movie model
* movie model

``` html
  <!DOCTYPE html>
  <html>
  <head>
 	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width,  initial-scale=1">
 	<title>movie in quark</title>
	<script type="text/javascript" src="./js/arrCont.js">
  </script>
 	<script type="text/javascript" src="./js/arrSrc.js"></script>
 	<style type="text/css">
		body, li{
			margin: 0;
			padding: 0;
		}
		li{
			list-style: none;
			margin-left:20px;
			margin-bottom: 10px;
		}
		li a{
			text-decoration: none;
		}

	</style>
	<script type="text/javascript">
		window.onload = function(){
			// alert(arrCont.length);
			// alert(arrSrc.length);
			var oBody = document.body;
            var str = '';
            // function fn(n){
			// 	return n < 10 ? '0000' + n
			// 	   : n < 100 ? '000' + n
			// 	   : n < 1000 ? '00' + n
			// 	   : n < 10000 ? '0' + n
			// 	   : String(n);
			// }

			function fn(n) {
    			return String(n).padStart(4, '0'); // 统一补零到4位数
			}
			for(var i = 0; i < arrCont.length; i++){
				str += '<li><a href = "' + arrSrc[i].src + '" title = "'+ arrCont[i].cont + '" target = "_blank">' + fn(i) + '&nbsp;&nbsp;' + arrCont[i].cont + '</a></li>';
			}
			oBody.innerHTML = str;

		}

	</script>
</head>
<body>

</body>
</html>
```

  * **arrCont.js**

  ``` javascript
  // arrCont
  var arrCont = [
    {
      "cont":"风之谷"
    },
  ];
  ```

  * **arrSrc.js**

  ``` javascript
  // arrCont
  var arrSrc = [
    {
      "src":"https://pan.quark.cn/s/c1c50a9f2f05"
    },
  ];
  ```


---
![alt text](https://upload-bbs.miyoushe.com/upload/2022/11/01/266607709/6cc988d046df34315681e50f9c9f299c_1259576169906078498.PNG?x-oss-process=image//resize,s_600/quality,q_80/auto-orient,0/interlace,1/format,png)