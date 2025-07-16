### python的运算
1. 幂运算

``` py
t = x ** 3
```
---
### chatgpt创建的coding
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
![alt text](https://upload-bbs.miyoushe.com/upload/2022/11/01/266607709/6cc988d046df34315681e50f9c9f299c_1259576169906078498.PNG?x-oss-process=image//resize,s_600/quality,q_80/auto-orient,0/interlace,1/format,png)