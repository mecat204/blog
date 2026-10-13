### 0001. npm安装
**[001. 现有的 config 看一下]{s}**
``` Powershell
Get-Content ~/.ssh/config
```

---
### 0002. cmd
**[001. 只导出当前目录下的文件夹名]{s}**
``` cmd
dir /b /ad > name.txt
```

---
**[002. 包含所有子文件夹(输出完整路径)]{s}**
``` cmd
dir /s /b /ad > name.txt
```

---
**[003. Bat 批处理]{s}**
``` Bat
@echo off
set "output=name.txt"
if exist "%output" del "%output%"
for /d %%i in (*) do echo %%i >> "%output%"
echo 完成
pause
```

---
**[004. 递归获取所有层级文件夹的纯文件名]{s}**
``` Bat
@echo off
set "sourceDir=D:\doc"
set "output=name.txt"

if exist "%output%" del "%output%"

for /d /r "%sourceDir%" %%i in (*) do echo %%~nxi >> "%output%"

pause

```



---
![alt text](https://upload-bbs.miyoushe.com/upload/2022/11/01/266607709/6cc988d046df34315681e50f9c9f299c_1259576169906078498.PNG?x-oss-process=image//resize,s_600/quality,q_80/auto-orient,0/interlace,1/format,png)
