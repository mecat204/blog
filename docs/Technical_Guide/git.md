### 01. 图文版的合并新增文件操作流程
* **分支新增文件合并并推送到远程主分支操作流程表**
| 步骤 | 操作内容           | 说明                  | 命令示例 / GitHub Desktop操作                                                                                 |
| -- | -------------- | ------------------- | ------------------------------------------------------------------------------------------------------- |
| 1  | 在功能分支上新增文件并提交  | 在分支上完成代码或文件新增及修改后提交 | Git: `git add .` + `git commit -m "新增文件"`<br>GitHub Desktop：在Changes填写提交信息，点击Commit                     |
| 2  | 切换到本地主分支（main） | 切换回主分支准备合并          | Git: `git checkout main`<br>GitHub Desktop：左上角选择main分支                                                  |
| 3  | 拉取远程主分支最新代码    | 保证本地主分支是最新状态        | Git: `git pull origin main`<br>GitHub Desktop：点击Pull origin                                             |
| 4  | 合并功能分支到主分支     | 把分支的新增内容合并进主分支      | Git: `git merge feature-branch`<br>GitHub Desktop：菜单Branch > Merge into current branch，选择feature-branch |
| 5  | 解决合并冲突（如果有）    | 如果出现冲突，手动编辑文件并提交解决  | 解决冲突后，Git: `git add .` + `git commit`                                                                   |
| 6  | 提交合并结果         | 合并产生的提交需提交保存        | GitHub Desktop：填写提交信息并提交                                                                                |
| 7  | 推送主分支到远程仓库     | 把合并后的主分支代码上传到远程仓库   | Git: `git push origin main`<br>GitHub Desktop：点击Push origin                                             |
---
* 备注
  - 每步操作前，请确认本地改动已保存并提交，避免丢失。
  - 合并冲突是正常现象，需耐心处理。
  - 合并前拉取远程代码，减少冲突概率。
  - 建议功能分支命名清晰（如 feature/新增功能名），方便管理。

---
![Alt text](https://upload-bbs.miyoushe.com/upload/2022/11/01/266607709/6cc988d046df34315681e50f9c9f299c_1259576169906078498.PNG?x-oss-process=image//resize,s_600/quality,q_80/auto-orient,0/interlace,1/format,png)

