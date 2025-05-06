### npm安装
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



