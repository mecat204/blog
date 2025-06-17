### 时间和日期
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
```