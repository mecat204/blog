### 001. python的运算
1. 幂运算

``` py
t = x ** 3
```

---
### 002. chatgpt创建的coding
* txt_to_md.py
  - 以“===”间隔来生成“===”内最大标题为文件名.md

``` py
import os
import re

# 路径设置
SOURCE_FILE = "chat_output.txt"
SAVE_DIR = "E:/code/Obsidian/doc/mds"
SPLIT_MARK = "==="

def safe_filename(name):
    """清除非法文件名字符"""
    return re.sub(r'[\\/:*?"<>|]', '_', name.strip())

def extract_max_level_title(text):
    """
    提取段落中标题层级最低的（即 # 最少的）
    优先找 # ，其次 ## ，然后 ###...
    """
    titles = re.findall(r'^(#{1,6})\s+(.+)', text, re.MULTILINE)
    if not titles:
        return "untitled"

    # 找到标题中 # 最少的，也就是最大级别的标题
    titles.sort(key=lambda x: len(x[0]))
    return safe_filename(titles[0][1])

def convert_txt_to_md_by_max_title(source_file, save_dir, separator):
    if not os.path.exists(source_file):
        print("❌ 源文件不存在")
        return

    with open(source_file, 'r', encoding='utf-8') as f:
        content = f.read()

    if not content.strip():
        print("⚠️ 内容为空")
        return

    parts = [p.strip() for p in content.split(separator) if p.strip()]
    if not parts:
        print("⚠️ 未检测到内容段落")
        return

    os.makedirs(save_dir, exist_ok=True)

    for i, part in enumerate(parts):
        title = extract_max_level_title(part)
        filename = f"{title}.md"
        filepath = os.path.join(save_dir, filename)

        # 避免重名
        count = 1
        while os.path.exists(filepath):
            filepath = os.path.join(save_dir, f"{title}_{count}.md")
            count += 1

        with open(filepath, 'w', encoding='utf-8') as f:
            f.write(part)

        print(f"✅ 已生成：{filepath}")

    # 可选：清空源文件
    with open(source_file, 'w', encoding='utf-8') as f:
        f.write("")

if __name__ == "__main__":
    convert_txt_to_md_by_max_title(SOURCE_FILE, SAVE_DIR, SPLIT_MARK)

```

---
### 003. python -m
* **Python 常用 `-m` 命令速查表**

> 使用 `python -m 模块名` 可直接从命令行调用 Python 模块的 CLI 接口。

| 模块名称        | 示例命令                                   | 用途说明                                       |
|----------------|--------------------------------------------|------------------------------------------------|
| http.server     | `python -m http.server 8000`               | 启动一个简单的 HTTP 文件服务器（默认当前目录） |
| venv            | `python -m venv env`                       | 创建一个虚拟环境                               |
| ensurepip       | `python -m ensurepip`                      | 安装 pip（部分环境默认无 pip 时使用）          |
| pip             | `python -m pip install requests`           | 安装/管理 Python 包（推荐使用这种方式）        |
| unittest        | `python -m unittest test_module.py`        | 运行 Python 的单元测试框架                     |
| timeit          | `python -m timeit "x = sum(range(100))"`   | 测量代码执行时间                               |
| json.tool       | `python -m json.tool input.json`           | 格式化 JSON 文件                               |
| pdb             | `python -m pdb script.py`                  | 启动内置调试器运行脚本                         |
| py_compile      | `python -m py_compile myscript.py`         | 编译 Python 源码为 `.pyc` 字节码               |
| smtpd           | `python -m smtpd -c DebuggingServer -n localhost:1025` | 启动一个调试用邮件服务器                     |
| trace           | `python -m trace --trace myscript.py`      | 跟踪程序执行（逐行追踪）                       |
| tokenize        | `python -m tokenize myscript.py`           | 输出 Python 文件的词法分析结果（调试用）       |
| zipfile         | `python -m zipfile -c archive.zip file.py` | 使用 zipfile 模块创建/查看 zip 文件            |
| tabnanny        | `python -m tabnanny myscript.py`           | 检查缩进是否一致（找 tab 和 space 错误）       |
| compileall      | `python -m compileall .`                   | 编译当前目录下所有 Python 文件为字节码         |
| dis             | `python -m dis myscript.py`                | 反汇编 Python 字节码（查看底层执行逻辑）       |
| site            | `python -m site`                           | 查看 Python 模块的搜索路径等信息               |

---

* **推荐命令用法建议**
  - 总是使用 `python -m pip` 代替直接调用 `pip`，避免多 Python 版本冲突问题。
  - 启动开发调试服务器时使用 `http.server` 模块，不需安装任何包。
  - 进行性能测试时可快速用 `timeit` 验证方案优劣。
  - 使用 `unittest` 组织并运行测试用例，有利于自动化测试流程。

* **补充说明**
  - 你可以在命令行输入以下命令来查看某个模块是否支持 CLI：

``` bash
python -m 模块名 --help
```

---
### 004. Python 常用命令与模块运行大全
* **🐍 Python 常用命令与模块运行速查表**

> 本文汇总了 Python 常用命令、模块运行方式、调试技巧和性能测试命令，适用于日常开发、测试和学习。

* **📦 基本执行命令**

| 命令                              | 示例                                       | 用途说明                       |
|-----------------------------------|--------------------------------------------|--------------------------------|
| `python`                          | `python`                                   | 启动交互式解释器               |
| `python script.py`                | `python hello.py`                          | 执行 Python 脚本文件           |
| `python -c "code"`                | `python -c "print(1+2)"`                   | 执行一段命令行 Python 代码     |
| `python -`                        | `python -`（然后输入代码）                 | 从标准输入读取代码执行         |
| `python -m module`                | `python -m http.server 8000`               | 以模块方式运行内置或安装模块   |

* **🔧 常用参数（Flags）**

| 参数                 | 说明                                  |
|----------------------|---------------------------------------|
| `-V`, `--version`    | 查看 Python 版本                      |
| `-h`, `--help`       | 查看命令帮助信息                      |
| `-i`                 | 脚本运行结束后进入交互模式            |
| `-O`                 | 优化模式运行，生成 `.pyo` 文件         |
| `-B`                 | 禁止生成 `.pyc` 缓存文件              |
| `-S`                 | 启动时不自动导入 `site` 模块           |
| `-E`                 | 忽略环境变量（如 `PYTHONPATH`）        |
| `-u`                 | 强制输出不使用缓冲                    |
| `-X dev`             | 启用开发者模式（更多错误提示）        |
| `-X showrefcount`    | 显示引用计数（调试 CPython）           |

* **🧪 测试与调试相关模块**

| 模块名              | 示例命令                               | 用途说明                          |
|---------------------|----------------------------------------|-----------------------------------|
| `unittest`          | `python -m unittest`                   | 运行 Python 单元测试              |
| `doctest`           | `python -m doctest myfile.py`          | 运行文档字符串测试                |
| `pdb`               | `python -m pdb myfile.py`              | 启动调试器调试脚本                |
| `trace`             | `python -m trace --trace script.py`    | 跟踪代码执行，逐行输出            |
| `dis`               | `python -m dis myfile.py`              | 查看字节码（反汇编）              |
| `tabnanny`          | `python -m tabnanny myfile.py`         | 检查缩进一致性（tab/space）问题   |

* **🛠️ 工具与性能相关模块**

| 模块名              | 示例命令                                   | 用途说明                          |
|---------------------|--------------------------------------------|-----------------------------------|
| `timeit`            | `python -m timeit "x=sum(range(100))"`     | 测量代码运行时间                  |
| `compileall`        | `python -m compileall .`                   | 编译所有 Python 文件为 `.pyc`     |
| `py_compile`        | `python -m py_compile myfile.py`           | 编译单个 Python 文件              |
| `site`              | `python -m site`                           | 查看模块搜索路径等信息           |
| `tokenize`          | `python -m tokenize myfile.py`             | 输出代码的 token 流（词法分析）   |

* **🌐 网络与文件服务模块**

| 模块名              | 示例命令                                   | 用途说明                           |
|---------------------|--------------------------------------------|------------------------------------|
| `http.server`       | `python -m http.server 8000`               | 启动简易 HTTP 文件服务器          |
| `zipfile`           | `python -m zipfile -c archive.zip file.py` | 创建压缩包                         |
| `json.tool`         | `python -m json.tool data.json`            | 格式化 JSON 文件                   |
| `smtpd`（3.9 以下） | `python -m smtpd -c DebuggingServer -n localhost:1025` | 本地调试 SMTP 邮件服务器  |

* **🧬 虚拟环境与包管理模块**

| 模块名              | 示例命令                              | 用途说明                          |
|---------------------|---------------------------------------|-----------------------------------|
| `venv`              | `python -m venv env`                  | 创建虚拟环境                      |
| `ensurepip`         | `python -m ensurepip`                 | 安装 pip                          |
| `pip`               | `python -m pip install requests`      | 安装 Python 第三方包              |

* **📝 附加：查看支持的全部选项**

```bash
python --help
python -m module_name --help


---
![alt text](https://upload-bbs.miyoushe.com/upload/2022/11/01/266607709/6cc988d046df34315681e50f9c9f299c_1259576169906078498.PNG?x-oss-process=image//resize,s_600/quality,q_80/auto-orient,0/interlace,1/format,png)