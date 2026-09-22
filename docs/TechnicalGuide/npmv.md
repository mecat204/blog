### 0001. npm安装
1. npm安装卡顿解决方案

``` gitbash
user@DESKTOP-SFEF080 MINGW64 ~/Desktop
$ npm config get proxy
null

user@DESKTOP-SFEF080 MINGW64 ~/Desktop
$ npm config set proxy http://127.0.0.1:10506

user@DESKTOP-SFEF080 MINGW64 ~/Desktop
$ npm config set https-proxy http://127.0.0.1:10506

user@DESKTOP-SFEF080 MINGW64 ~/Desktop
$ npm config get proxy
http://127.0.0.1:10506

user@DESKTOP-SFEF080 MINGW64 ~/Desktop
$
```

2. 清除缓存
``` bash
npm cache  clean --force
```
3. 删除 node_modules 和 package-lock.json 后重试
``` bash
rm -rf node_modules package-lock.json
npm install
```

4. 切换国内镜像源(如果你在国内)

``` bash
npm config set registry https://registry.npmmirror.com
npm install
```
5. 升级NPM
  - 有些 NPM 版本可能有 bug，可以尝试升级：
  ``` bash
  npm install -g npm
  ```

6. 使用pnpm或yarn替代安装
  - 比如用pnpm
  ``` bash
  npm install -g pnpm
  pnpm install
  ```
7. 增加 Git 缓存区大小
``` bash
git config --global http.postBuffer 524288000
```
- 设置为 500MB，大大提升 Git 传输能力（默认才 1MB）
8. 使用 --depth=1 做浅克隆（只克隆最近一次提交）
``` bash
git clone --depth=1 https://github.com/jaywcjlove/reference.git
```

---
### 0002. npm、cnpm、yarn、pnpm 之间的关系
* npm / cnpm / yarn / pnpm 本身都是“包管理工具”，
它们的任务只是：
👉「根据依赖清单（package.json）去安装你项目所需的依赖包」
👉「决定这些包是局部安装（node_modules）还是全局安装（系统路径）」
👉「帮你统一管理版本、缓存、速度、镜像源等」
---
* 它们之间的关系:
| 工具名    | 是否默认自带       | 安装方式                  | 特点                         |
| ------ | ------------ | --------------------- | -------------------------- |
| `npm`  | ✅ Node.js 自带 | 无需安装                  | 官方标准，通用但有时速度慢              |
| `cnpm` | ❌ 需手动安装      | `npm install -g cnpm` | 淘宝镜像的 npm，更快（但更新慢）         |
| `yarn` | ❌ 需手动安装      | `npm install -g yarn` | Facebook 推出，速度快、离线缓存、锁定更稳定 |
| `pnpm` | ❌ 需手动安装      | `npm install -g pnpm` | 体积小，速度快，节省磁盘空间的新一代工具       |
---
* **安装的只是依赖，不是安装 npm 本身。**

* 可以把项目结构和这些工具看成这样

```
[你安装 Node.js]
   ↓
自动获得 npm（包管理工具）

[你用 npm/yarn/pnpm]
   ↓
它读取项目的 package.json
   ↓
去下载需要的包（依赖）
   ↓
放到 node_modules/
```
* **原来如此。我就说怎么老得安装npm,有时候还得用cnpm,或者yarn.它们的道理都相通，配置好了就不需要额外安装。安装的只是局部或者全局的包或者叫做依赖。**

* **一句话总结:**
npm install 是用来安装包的，默认是安装在当前项目目录（局部）；
npm install -g 是安装在全局系统路径中，方便你在命令行全局使用；
而 **npm 本身是 Node.js 附带的，不需要单独安装**。

* **图解理解:**

```
你安装 Node.js
   ↓
Node.js 自动带上 npm 工具
   ↓
npm 用来安装“别的包”（不是它自己）

├─ npm install express       ← 局部安装（项目依赖）
│   └─ ./node_modules/express
│
├─ npm install -g nodemon    ← 全局安装（命令行工具）
│   └─ C:\Users\你\AppData\Roaming\npm\nodemon.cmd

（注意：不是在安装 npm 本身）

```

* 扩展建议
  - npx 是用来临时调用 CLI 工具的，比如：

  ```
  npx create-react-app myapp
  ```

  - 可以不全局安装 create-react-app，更轻量。

---
### 0003. 详解 npx create-react-app myapp

``` bash
npx create-react-app myapp
```

这行命令的作用是：

**用官方提供的 create-react-app 脚手架工具，在当前目录下创建一个名为 myapp 的 React 项目。**

* **分段解析：**
1. npx
  - **全称**：npm package runner（npm 的包运行器）

  - **作用**：

    - 临时运行一个 npm 包，即使你没有全局安装它。

    - 使用完后自动清除缓存，不会在本地留下任何垃圾。

**为什么用它？**
如果你没有全局安装 create-react-app，也能使用它 —— 比 npm install -g create-react-app 更轻便。

2. create-react-app
  - **这是一个 npm 包的名字**，它是 Facebook 提供的官方 React 脚手架工具。

  - 作用：

    - 快速初始化一个 React 项目结构。

    - 自动安装所有依赖（如 React、ReactDOM、Webpack、Babel 等）。

    - 内置开发服务器、打包工具、热更新、代码分割支持等。

**简单理解：**
就像 Word 里点“新建模板”那样，它会自动给你铺好地基，把项目框架搭起来。

3. myapp
- 这是你要创建的项目文件夹名。

- create-react-app 会：

  - 创建一个叫 myapp 的新目录

  - 在里面初始化项目文件

  - 自动执行 npm install 安装依赖

> 你最终会得到一个结构如下的目录：

``` java
myapp/
├── node_modules/
├── public/
├── src/
├── package.json
├── README.md
└── ...
```

✅ 命令整体流程总结：
- npx 找到 create-react-app 工具（如果本地没有就临时下载）

- create-react-app 创建名为 myapp 的项目目录

- 自动初始化项目结构（React + 配套工具）

- 自动执行 npm install 安装所有依赖

- 最后提示你进入目录，运行开发服务器：
``` bash
cd myapp
npm start
```

✅ 你可以立即使用的命令：
``` bash
cd myapp
npm start
```
这时浏览器会自动打开 http://localhost:3000，显示一个默认的 React 页面。

*  Bonus：如果你想用 yarn 替代 npm:
``` bash
npx create-react-app myapp --use-npm      # 强制用 npm（默认可能是 yarn）
npx create-react-app myapp --use-pnpm     # 用 pnpm
npx create-react-app myapp --template typescript   # 创建 TypeScript 模板
```

---
### 0004. Git Clone 常见用法对照表
| 用法                  | 命令示例                                                                    | 说明                            |
| ------------------- | ----------------------------------------------------------------------- | ----------------------------- |
| **克隆完整仓库**          | `git clone https://github.com/user/repo.git`                            | 默认拉取整个历史记录（体积可能很大）            |
| **浅克隆（只取最新一次提交）**   | `git clone --depth=1 https://github.com/user/repo.git`                  | 只下载最新提交，节省空间和时间               |
| **浅克隆 N 次提交**       | `git clone --depth=5 https://github.com/user/repo.git`                  | 下载最近 5 次提交，历史有限               |
| **克隆特定分支**          | `git clone -b develop https://github.com/user/repo.git`                 | 拉取指定分支（默认是 `main` 或 `master`） |
| **浅克隆指定分支**         | `git clone -b develop --depth=1 https://github.com/user/repo.git`       | 拉取某个分支的最新版本                   |
| **只克隆单个分支（不带其他分支）** | `git clone --single-branch -b develop https://github.com/user/repo.git` | 节省空间，只保留一个分支                  |
| **克隆到指定目录**         | `git clone https://github.com/user/repo.git myproject`                  | 把仓库克隆到 `myproject/` 文件夹       |
| **克隆子模块一起拉取**       | `git clone --recursive https://github.com/user/repo.git`                | 如果仓库有子模块，会一起下载                |
| **后续初始化子模块**        | `git submodule update --init --recursive`                               | 克隆后再下载子模块                     |
| **镜像克隆**            | `git clone --mirror https://github.com/user/repo.git`                   | 用于做完整的镜像（包含所有 refs 和分支）       |
| **裸仓库克隆**           | `git clone --bare https://github.com/user/repo.git`                     | 仅含 Git 数据，不含工作区，适合做远程备份       |

---
![alt text](https://upload-bbs.miyoushe.com/upload/2022/11/01/266607709/6cc988d046df34315681e50f9c9f299c_1259576169906078498.PNG?x-oss-process=image//resize,s_600/quality,q_80/auto-orient,0/interlace,1/format,png)
