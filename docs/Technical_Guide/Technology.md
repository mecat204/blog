### 00. coding online
1. [coding online](https://v39.livecodes.io/)
1. [hexhub·运维·code](https://www.hexhub.cn/)
1. [codex](https://openai.com/codex/)
1. [PasteBin](https://paste.fastmirror.net/)
---
### 01. 技术
1. [合并多个txt](https://zhuanlan.zhihu.com/p/147758957)
---
### 02. Command
1. 创建序列
``` html
window.onload = function(){
	var oBody = document.body;
	var len = 400;
	var str = 'https://web.movie.com/videos/123456/123456_';
	for(var i = 0; i <= len; i++){
		oBody.innerHTML += '<li>' + str + fn(i) + '.ts<li>';
	}
	function fn(n){
		return i < 10 ? '00' + n : (i < 100 ? '0'+ n : n)
	}
}
```
1. 保存目录到文件
``` cmd
tree /f
```

1. sublime txt 删除空白行
```
^\s*$
```

1. 列出详细地列出内容（包括隐藏文件等）可以加参数：

```cmd
dir /a /s
```

- `/a`：显示所有文件，包括隐藏文件；
- `/s`：递归列出所有子目录的文件。
如需导出目录列表到一个文本文件，可以加上重定向：

```cmd
dir /a /s > filelist.txt
```
1. 合并ts文件
``` cmd
copy /b  F:\f\*.ts  E:\f\new.ts
copy /b *.ts new.ts
copy /b "%~dp0"\*.ts  "%~dp0"\new.ts
```
1. 替换多个[[ab][cd]], 其中ab,cd为不同的两位数
```
搜索:\[\[\d+\]\[d+\]\]
替换:
```
---
### 03. snippet
1. **计算常数e**

``` javascript
function calculateE(n) {
let e = 1;
let factorial = 1;

for (let i = 1; i <= n; i++) {
factorial *= i;
e += 1 / factorial;
console.log(`Iteration ${i}: e ≈ ${e}`);
}

return e;
}
// 每2秒计算一次e的近似值
setTimeout(() => {
console.log('Calculating e...');
const result = calculateE(10);  // 计算10次迭代
console.log('Final approximation:', result);
}, 2000);

```


---
### 04. AI时代 VS 传统编程
**AI编程对职业程序员的真实影响**

初级岗位的替代风险
根据行业报告，AI已能完成40%-60%的标准化编码工作（如CRUD操作、API调用），初级程序员岗位需求显著下降。Meta等公司已用AI工具替代部分外包团队，传统"代码劳工"岗位正在消失。
但AI生成的代码常存在逻辑漏洞或架构缺陷，仍需人类审核。某金融公司因AI代码未正确处理支付回调机制导致重大故障，凸显人类工程师的不可替代性。
高阶岗位的价值提升
系统架构师、AI工程师等岗位需求增长120%，年薪可达普通程序员2-4倍。核心能力转向：架构设计、复杂系统调试、AI工具驯化等。
提示词工程（Prompt Engineering）成为新技能焦点。资深工程师通过精准提示词控制AI生成代码的质量，效率比纯手工编码提升3倍以上。
---

**业余学习与职业发展的平衡策略**
学习重心转移
基础巩固：掌握核心原理（算法、网络协议、设计模式），这些是理解AI生成代码的基础。例如用AI工具实现功能后，手动优化其生成的SQL查询性能。
AI协作技能：学习GitHub Copilot、Cursor等工具的高级用法，如通过注释生成完整函数、利用"链式思考"功能调试复杂逻辑。
差异化能力建设
垂直领域结合：将编程与自身行业知识结合。例如：
医疗从业者可学习生物信息学编程

教师掌握教育科技工具开发
软技能强化：项目管理、跨部门沟通等能力难以被AI替代。某制造业转行工程师通过"技术+供应链管理"复合能力实现职业跃迁。

---
**职业转型的可行路径**

新兴岗位机会
岗位类型	所需技能	适合转型基础
AI应用工程师	大模型微调、API集成	有项目经验的业余开发者
技术型产品经理	需求分析、AI工具使用	行业背景+基础编程
数据工程顾问	SQL优化、ETL流程设计	数据库操作经验
风险较低的切入点
DevOps/云运维：AWS认证+自动化脚本能力仍需求旺盛，且AI渗透率较低
边缘计算开发：物联网设备编程需硬件知识，AI替代难度大
开源贡献：参与Apache等基金会项目，建立可验证的技术履历

---
**关键行动建议**

测试职业适配性
用AI工具完成一个完整项目（如搭建个人博客），记录人工介入的环节，这些就是你的价值点
在Kaggle等平台参加AI辅助的编程比赛，评估竞争力
学习资源聚焦
免费工具：阿里云通义灵码（适合中文提示词）、CodeLlama（本地部署）
课程：Coursera《AI时代的软件工程》（斯坦福2025新课）

---
**Mermaid**

行业正在经历"技术达尔文主义"——淘汰的是工具型程序员，进化出的是"AI驯兽师"。你的年龄反而可能成为优势：成熟的学习方法和行业经验，正是驾驭AI最需要的特质。建议先从AI协作项目入手，逐步向架构设计或垂直领域专家转型。

---
### 05. m3u8下载使用说明
1. index.m3u8的地址
```
https://vip.lz-cdn1.com/20220418/2536_5e792872/index.m3u8
```
---
2. index.m3u8的内容
```
#EXTM3U
#EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=800000,RESOLUTION=1080x608
1200k/hls/mixed.m3u8
```
3.mixed的内容
``` m3u8
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-PLAYLIST-TYPE:VOD
#EXT-X-MEDIA-SEQUENCE:0
#EXT-X-TARGETDURATION:8
#EXT-X-DISCONTINUITY
#EXTINF:4.000000,
7dafceff34c000000.ts
#EXTINF:4.000000,
7dafceff34c000001.ts
#EXTINF:7.480000,
7dafceff34c000002.ts
···广告部分
#EXTINF:6.933333,
9c65c55229598a51a49359c9a6e5f72f.ts
#EXTINF:3.166667,
9728c9a61705591433f18b1f92e1b892.ts
...
#EXTINF:4.000000,
7dafceff34c001597.ts
#EXTINF:1.160000,
7dafceff34c001598.ts
#EXT-X-ENDLIST
```
4. 解析地址
``` js
str = 'https://vip.lz-cdn1.com/20220418/2536_5e792872/' + '1200k/hls/' + '7dafceff34c000000.ts';
https://vip.lz-cdn1.com/20220418/2536_5e792872/1200k/hls/7dafceff34c000000.ts
```
5. 提取下载视频的所有名称
``` cmd
dir *.ts /b > rename.bat
```
6. 修改名称，之后再合并文件
``` cmd
copy /b "%~dp0"\*.ts  "%~dp0"\new.ts
%~dp0 则是 当前盘符和路径 的意思
```
7. 解释6
```
这里使用copy命令的文件合并功能进行ts文件的合并，copy后面的 /b  参数表示把文件按二进制格式来合并，如果不加这个参数，则会把目标当成文本文件来合并，并在文件内添加不必要的标记，这会导致播放出错，所以必须加 /b 参数
%~dp0 则是 当前盘符和路径 的意思
```
---
### 06. BAT.bat
* port_killer.bat

```
@echo off
setlocal enabledelayedexpansion

:: 提示用户输入端口号
set /p port=请输入要检测并关闭的端口号：

:: 查找端口占用的 PID
for /f "tokens=5" %%a in ('netstat -ano ^| findstr :%port%') do (
    set pid=%%a
)

if not defined pid (
    echo 端口 %port% 没有被占用。
    pause
    exit /b
)

echo 端口 %port% 被进程 PID %pid% 占用。

:: 查询进程名称
for /f "tokens=1" %%p in ('tasklist /FI "PID eq %pid%" /FO TABLE /NH') do (
    set procName=%%p
)

echo 进程名: %procName%

:: 询问是否结束进程
set /p confirm=是否要结束该进程？(y/n)：

if /i "%confirm%"=="y" (
    taskkill /PID %pid% /F
    echo 进程 %pid% 已结束。
) else (
    echo 操作已取消。
)

pause

```
### 07. 端口管理
* 端口占用管理
  - 最开始是npm start启用的，后来我想在另一个本地仓库中启动docsify serve docs中启动。发现启动的还是3000端口。现在有两个诉求。第一，先关闭npm start启动的3000.我在启动docsify serve docs的3000.或者直接修改docsify serve docs中的3000到4000
1. 关闭原先 npm start 占用的 3000 端口进程
  - 这个进程很可能是一个 node 进程（比如 React/Vite/VitePress 项目）
    * 手动关闭方式（推荐）：
      打开 CMD 或 PowerShell：
      ``` cmd
	  netstat -ano | findstr :3000
	  ```
      你会看到类似输出：
       ``` nginx
         TCP    127.0.0.1:3000     ...     LISTENING       12345
       ```
      拿到最后一列的 PID，例如：12345，然后执行：
      ``` cmd
	  taskkill /PID 12345 /F
	  ```
      看到：
	  ```
	  makefile
      成功: 已终止 PID 12345 的进程。
	  ```
---
2. 启动 docsify 的方式（选择其一）
  - 方式 A：继续用 3000 端口启动（前提是已释放）
  ``` bash
  docsify serve docs
  ```
  默认就是 3000，如果端口空闲会成功。

  - 方式 B：修改为其他端口，例如 4000
  ``` bash
  docsify serve docs -p 4000
  ```
  可以加 -o 自动打开浏览器：
  ```
  docsify serve docs -p 4000 -o
  ```
---
3. 最终建议：加一行启动脚本
  - 你可以在 package.json 中添加一个脚本命令，方便以后运行：
  ``` json
  {
  "scripts": {
    "docs": "docsify serve docs -p 4000"
  }
  }

  ```
  然后运行：
  ``` bash
  npm run docs
  ```
---
04. 0.0.0.0:3000这个是什么
  * 0.0.0.0:3000 表示：
    - 一个程序在本机上监听所有 IPv4 网络接口的 3000 端口
  * 分解解释：
    - .0.0.0：并不是一个“真实 IP”，而是一个通配地址，代表：
	  > “本机上所有 IPv4 网络接口（如本地回环、无线网卡、有线网卡等）”
	- :3000：监听的端口号是 3000
  * 举例对比理解
  | 显示地址               | 含义                         |
| ------------------ | -------------------------- |
| `127.0.0.1:3000`   | 只监听本地（你本机访问才行）             |
| `192.168.1.5:3000` | 只监听内网某个网卡                  |
| `0.0.0.0:3000`     | 监听所有网卡上所有 IPv4 接口，包括局域网/本地 |

  * 什么时候会看到？
    - 你运行 netstat -ano | findstr :3000 或 npm start 等服务型命令时，如果出现：
    ``` nginx
	TCP    0.0.0.0:3000    ...   LISTENING     12345
	```
	表示：你电脑上的某个程序正在监听端口 3000，且接受来自任何来源的连接（包括你自己访问、局域网其他电脑访问都可以）。
  * 安全提示：
    - 如果你运行的是开发服务器（如 npm start 启动的 React/Vite 项目），而监听地址是 0.0.0.0，那说明
	  - 局域网内其他设备也可以访问你这台机器的 3000 端口
	  如果有安全考虑，建议只监听 localhost 或用防火墙阻断外部访问
  * 如何只监听本地？
    - 大多数开发框架支持指定监听地址，例如：

	``` bash
	npm start -- --host 127.0.0.1 --port 3000
	```

	或者(React/Vite)

	``` bash
	vite --host 127.0.0.1 --port 3000

	```
---
05. 什么是 TIME_WAIT?
``` cmd
TCP    127.0.0.1:3000         127.0.0.1:7580         TIME_WAIT       0
  TCP    127.0.0.1:3000         127.0.0.1:7582         TIME_WAIT       0
  TCP    127.0.0.1:3000         127.0.0.1:7584         TIME_WAIT       0
  TCP    127.0.0.1:3000         127.0.0.1:7586         TIME_WAIT       0
  TCP    127.0.0.1:3000         127.0.0.1:7591         TIME_WAIT       0
  TCP    127.0.0.1:3000         127.0.0.1:7592         TIME_WAIT       0
  TCP    127.0.0.1:3000         127.0.0.1:7664         TIME_WAIT       0
  TCP    127.0.0.1:3000         127.0.0.1:7665         TIME_WAIT       0
  TCP    127.0.0.1:3000         127.0.0.1:7670         TIME_WAIT       0
  TCP    127.0.0.1:3000         127.0.0.1:7671         TIME_WAIT       0
  TCP    127.0.0.1:3000         127.0.0.1:7672         TIME_WAIT       0
  TCP    127.0.0.1:3000         127.0.0.1:7673         TIME_WAIT       0
```
* TIME_WAIT 是 TCP 协议的正常现象：
  - 表示连接已经关闭
  - 系统在等待一段时间（通常是 1-4 分钟）来确保剩余的数据都被正确处理
  - 这个状态不会阻止新的程序监听同样的端口
* 现在看到的这些 TIME_WAIT 状态连接：
``` nginx
TCP    127.0.0.1:3000  →  TIME_WAIT       0
```
说明：
  >  监听该端口的进程已经被成功关闭（或者已退出），只剩下 TCP 协议栈中遗留的连接在“延迟清理”状态。
* 重点：
  > 即使你看到很多 TIME_WAIT，端口 3000 现在是空闲的！你可以放心启动 docsify 或其他服务监听 3000。
* 如何验证 3000 是否真的空闲？
``` cmd
netstat -ano | findstr ":3000" | findstr LISTENING
```
如果**没有输出**，就说明没有程序在监听，端口空闲。
* 总结：
  > **看到 TIME_WAIT 不用担心，它不等于端口被占用。只要没有 LISTENING 状态，3000 端口就可以正常使用**

---
### 08. npm start为何会打开多个端口。
* 问题回顾：你看到的是多个连接到 127.0.0.1:3000，但只有一个进程监听它

``` nginx
TCP    0.0.0.0:3000         ...   LISTENING       16456  ← 被 node 占用
TCP    127.0.0.1:3000       127.0.0.1:7580       TIME_WAIT     0
TCP    127.0.0.1:3000       127.0.0.1:7675       ESTABLISHED   16456
...s
```

* 为什么 npm start（例如 React/Vite 项目）会出现多个连接占用 3000？
  - 原因 1：开发服务器自动打开浏览器，建立多个连接
    * 当你运行 npm start，默认启动的是开发服务器（如 Vite、Webpack Dev Server、React Scripts）
    * 它会尝试 自动在浏览器打开 http://localhost:3000
    * 浏览器会发起多个连接：页面、CSS、JS、HMR（热更新）等
    * 每个请求/连接都会导致一个条目出现在 netstat 中
	所以会看到多个：

	``` makefiles
	127.0.0.1:3000 ←→ 127.0.0.1:xxxx
	```
  - 原因 2：热更新/开发中 WebSocket 连接
  比如 Vite、React、Next.js 开发服务器会维持“热更新连接”：
    * 页面打开后，会有一个 WebSocket 长连接
    * 每当你修改文件，它就会通知浏览器刷新或热替换
  所以你会看到一条 ESTABLISHED 状态的连接：

  ``` makefile
  127.0.0.1:3000 ←→ 127.0.0.1:7675   ESTABLISHED
  ```

  - 原因 3：TIME_WAIT 是关闭连接后的正常残留
    * 每次浏览器请求文件（如 JS、CSS、图片），请求结束后，TCP 连接并不是立刻销毁，而是进入 TIME_WAIT
    * 这个状态在 Windows 默认持续约 2 分钟
  - **重点:**
    > 不管你看到多少条 3000 端口相关的连接，真正监听 3000 端口的只有一个进程（如 PID 16456）
	你可以通过这个命令确认是谁：
	``` cmd
    netstat -ano | findstr :3000 | findstr LISTENING
	```
---
### 09. 项目运行
* Vue开发的，需要 node 环境来运行。
  - 手动安装
    * 安装 NodeJS，参考官方文档
    * 使用 git clone 下载项目到本地, 不使用 git 可能因为缺少依赖而无法运行
    * 打开命令行，在项目根目录下，运行npm install来下载依赖。
    * 执行npm start来启动项目，项目默认地址为http://localhost:3000
    * 在浏览器中打开http://localhost:3000 来访问项目。
---

* 使用Docker
  - 创建镜像 docker build -t typing-word:001 .
  - 启动容器 docker run --name typing-word -p 3000:3000 -d typing-word:001
---
### 10. excel填充序列001-065该如何操作
* **使用TEXT函数结合ROW函数**
  - 输入公式：在起始单元格（如A1）输入公式 =TEXT(ROW(A1),"000")。这会返回文本格式的"001"（ROW(A1)返回1，TEXT函数将其格式化为三位数）
  - 拖动填充：选中该单元格，向下拖动填充柄至第65行（A65），即可生成001到065的序列
  - 优点：动态更新，删除或插入行时序列自动调整。

* **设置单元格格式自动补零**
  - 输入起始数字：在A1输入数字1，A2输入数字2（或直接输入1后按Ctrl键拖动生成序列）
  - 设置单元格格式：
    * 选中A1:A65单元格区域，右键选择 “设置单元格格式”。
  - **在 “自定义” 类型中输入格式代码 000，点击确定**
  - 填充序列：
    * 输入1后，通过菜单 “开始” → “填充” → “序列”，设置类型为“等差序列”，步长1，终止值65，完成后所有数字自动显示为三位数
  - 优点：直观操作，适合固定范围填充。

* **手动输入结合文本格式**
  - **输入初始值：在A1直接输入 '001（单引号强制文本格式），避免Excel自动去除前导零**
  - 拖动填充：
  - 按住右键拖动填充柄到A65，松开后选择 “填充序列”，自动生成001到065的文本序列或按住Ctrl键拖动填充柄快速生成连续编号

* 补充技巧：SEQUENCE函数（Excel 2021及以上版本）
    - 输入公式 =TEXT(SEQUENCE(65),"000")，直接生成65行的三位数序列
---
![alt text](https://upload-bbs.miyoushe.com/upload/2022/11/01/266607709/6cc988d046df34315681e50f9c9f299c_1259576169906078498.PNG?x-oss-process=image//resize,s_600/quality,q_80/auto-orient,0/interlace,1/format,png)