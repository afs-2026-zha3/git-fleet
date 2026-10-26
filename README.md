# Git Fleet — zha3

本班 Git 协作练习。全班共用 `main`，每个固定小组一艘船，共 4 组。

## 开始

```sh
git clone https://github.com/afs-2026-zha3/git-fleet.git
cd git-fleet
git branch --show-current
git status
```

使用自己的 GitHub 用户名（不带 @）作为唯一 ID。在 `introductions/<id>.txt` 写一句自我介绍，只提交自己的文件。

## 两轮协作

每轮等待讲师暂停写入并宣布共同基线，确认工作区干净，运行 `git pull --ff-only origin main` 和 `git rev-parse --short HEAD` 核对基线。更新失败时先请教练检查。

第一轮编辑 `boarding.txt`，第二轮编辑 `reboarding.txt`；只修改本组列表，保留组标题和结束标记。先在本地加入自己的 ID 并提交，等待讲师开放推送窗口。发生冲突时保留远端 ID 原顺序，再追加自己的 ID，不替别人添加。第一轮列表的第一个 ID 是船长；第二轮船长最后返回。船长先准备本地提交，等待本组其他人发布后再合并、发布自己的 ID。

## 操作卡

以下以第一轮为例；自我介绍和第二轮请替换为实际文件名。

```sh
git diff
git add boarding.txt
git diff --cached
git commit -m "docs: add my boarding ID"
# 等待讲师开放推送窗口
git push origin main
```

若远端已前进导致推送被拒绝：

```sh
git fetch origin
git merge --no-ff --no-edit origin/main
```

若发生内容冲突，运行 `git status` 并检查冲突文件，保留已发布 ID 的顺序并追加自己的 ID，移除冲突标记，然后：

```sh
git add boarding.txt
git diff --cached
git diff --cached --check
git commit -m "docs: preserve all boarding IDs"
git push origin main
```

自动合并成功时无需额外创建冲突处理提交。若推送再次被拒绝，重复 fetch 和 merge，不重做原 ID 提交。

最终停止写入后，每人运行：

```sh
git pull --ff-only origin main
git rev-parse --short HEAD
git status
```

核对讲师公布的最终提交和干净工作区。遇到无法解释的状态，保留现场并请教练帮助。不得强推、reset 共享分支或删除他人成果。
