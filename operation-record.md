# HW2个人独立练习记录

- 个人标识：440967
- 仓库：https://github.com/lz21651028-pixel/ossdt-git-practice
- 默认分支：main
- 执行日期：2026-11-21
- 执行工具：Codex、Git CLI、GitHub网页。

## 分支、提交和PR

功能分支：`feature/intro`。

1. [df97961](https://github.com/lz21651028-pixel/ossdt-git-practice/commit/df97961)：补充分支工作流程。
2. [f4e98ec](https://github.com/lz21651028-pixel/ossdt-git-practice/commit/f4e98ec)：添加合并前检查和工具使用说明。

[个人PR #1](https://github.com/lz21651028-pixel/ossdt-git-practice/pull/1)已合并。
[合并提交6c34793](https://github.com/lz21651028-pixel/ossdt-git-practice/commit/6c34793158362aabb856a96aa3b912ca7f626b9e)包含两个分支提交。合并通过本地`git merge --no-ff`完成后推送main，GitHub将关联PR标记为已合并。

## 实际执行的命令

以下是本次执行的成功命令序列（省略重复的只读检查，未将网页操作虚构为命令）：

```sh
git init -b main
git add README.md practice.md
git diff --cached --stat
git commit -m "建立Git练习说明和冲突基准文件"
git remote add origin https://github.com/lz21651028-pixel/ossdt-git-practice.git
git -c http.proxy=http://127.0.0.1:7890 push -u origin main
git status --short
git switch -c feature/intro
git diff --stat
# 编辑README.md后：
git status --short
git diff -- README.md
git add README.md
git diff --cached --stat
git commit -m "补充分支工作流程"
# 编辑practice.md后：
git diff -- practice.md
git add practice.md
git diff --cached --stat
git commit -m "添加合并前检查和工具使用说明"
git -c http.proxy=http://127.0.0.1:7890 push -u origin feature/intro
git status --short
git diff main...HEAD --stat
git log --oneline -3
git -c http.proxy=http://127.0.0.1:7890 ls-remote --heads origin
git status --short
git switch main
git merge --no-ff feature/intro -m "合并个人练习PR #1：分支流程与合并检查"
git -c http.proxy=http://127.0.0.1:7890 push origin main
git -c http.proxy=http://127.0.0.1:7890 pull --ff-only
git status --short
git log -4 --oneline
```

用途及结果：`init`建立main；`add/commit`保存基准和两次有实际内容的修改；`switch`创建/切换分支；`status/diff`检查范围；`push`将分支发布到远程；`ls-remote`核对远程分支；`merge --no-ff`保存合并提交；最后`pull --ff-only`输出Already up to date，工作区无未提交文件。

`-c http.proxy=...`仅为本次命令使用本机实际运行的代理，没有修改全局Git配置；其他机器应使用自己的网络配置。

网页操作：在GitHub新建公开仓库；填写个人PR标题和说明。PR只包含README.md和practice.md的25行新增内容，合并前已读取并核对差异。

## 未完成的课程要求

本次按用户要求独立进行，没有同学通过自己的账号提交协作PR，也没有完成学生亲自处理同学协作产生的真实冲突。
因此本文件只记录实际完成的独立部分，不是可宣称满足全部要求的课程最终提交报告。课程报告需要的协作者、冲突产生与解决证据不能虚构。

## 工具使用与核查

Codex执行命令、整理文件，并通过GitHub API核对PR的merged状态、提交链接和文件范围。
人工核查方式：打开两个Commit及PR链接，对照本记录阅读修改；运行`git log --graph --oneline --all`理解分支与合并关系。
