### 01. return
* 实例1: 报错，说明网页环境有特殊限制。尝试在 空标签页 (about:blank) 中新建 Snippet 执行，或在无痕窗口测试。

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
    alert(521); //alert(521)在return后面故此无法  弹  出。
    }
  alert(520); //alert(520)在函数外面，和return无  关。

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

---

### 02. 箭头函数
* 遍历数组

 ``` javascript
 [1, 2, 3].forEach(item => {
     console.log(item)
 })
 ```

* 遍历数组进行幂运算

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
### 03. script标签的注意事项
* 实例

 ``` html
<!doctype html>
<head>
    <meta http-equiv = "Content-Type" content = "text/html"; charset = "utf-8">
  <title>script标签的注意事项</title>
  <script>
    //alert(detectNum('123aaa456')); // 检测 '23aaa456'中是否包含数字

   window.onload = function () {
        var aInp = document.getElementsByTagName(input');

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

   // script标签在head标签里面时，要用window.oload函数包裹。在body里面则不需要。
  </script>
</head>
<body>
  <input type="text">
  <input type="button" value="按钮">
</body>
<html>
```

---
### 04. shake 左摇右摆|过时代码
* shake

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

### 05. sort排序问题的应用
* sort
* 实例

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

---
### 06. splice
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
    ---
    3. 替换元素

    ``` javascript
    let arr = [1, 2, 3, 4, 5];
    arr.splice(1, 2, 9, 8); // 从索引1开始，删除2个元素，插入9和8
    console.log(arr); // [1, 9, 8, 4, 5]
    ```
    ---
    4. 删除直到数组尾部

    ``` javascript
    let arr = [1, 2, 3, 4, 5];
    arr.splice(3); // 从索引3开始删除到末尾
    console.log(arr); // [1, 2, 3]
    ```
    ---
    5. 负数索引(从尾部开始数)

    ```
    let arr = [1, 2, 3, 4, 5];
    arr.splice(-2, 1); // 从倒数第2个开始，删除1个
    console.log(arr); // [1, 2, 3, 5]
    ```
    ---
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

* 总结
   | 操作 | 示例                | 结果                 |
| -- | ----------------- | ------------------ |
| 删除 | `splice(i, n)`    | 删除 `i` 位置起 `n` 个元素 |
| 添加 | `splice(i, 0, x)` | 在 `i` 位置插入 `x`     |
| 替换 | `splice(i, n, x)` | 删除 `n` 个并插入 `x`    |

* 实例

  ``` javascript

  var arr = ['Genshin', '丝柯克', '芙芙', '夏洛蒂'];
  // ['深渊上半', '丝柯克', '芙芙', '夏洛蒂']
  arr.splice(0, 1, '深渊上半');
  //  ['深渊上半', '丝柯克', '芙芙', '夏洛蒂', '茜特拉利']
  arr.splice(arr.length, 0, '茜特拉利');
  console.log(arr);
  /*
  arr.length 表示数组最后一个索引之后的位置
  0 表示不删除任何元素
  '茜特拉利' 要插入的值
  */
  ```


---
### 07. splice容易混淆的点
* `splice()` 方法确实很容易让人搞混，尤其是：
  - 起始索引是从哪“开始算”的？
  - 删除的元素“包括不包括起点”？
  - 负数到底是从哪“倒着”算？


* `splice(start, deleteCount)` 背后的逻辑

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

* **解释：**
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
 - 还可以插入元素：

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
  2. 要删除倒数第4和倒数第3这两个元素，所以删除数  是 2
  */

    ```

---
### 08. arr.splice(-3, 2)
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
### 09. shift、 unshift、 pop、push
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
![alt text](https://upload-bbs.miyoushe.com/upload/2022/11/01/266607709/6cc988d046df34315681e50f9c9f299c_1259576169906078498.PNG?x-oss-process=image//resize,s_600/quality,q_80/auto-orient,0/interlace,1/format,png)