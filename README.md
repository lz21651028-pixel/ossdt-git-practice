# OSSDT Git练习

用于《开源软件开发与技术》HW2的分支、提交、Pull Request及合并练习。练习材料与个人课程项目分开。

个人标识：440967。

## 分支工作流程

从main创建feature/intro分支，在分支上修改练习材料；检查差异后提交，将分支推送到GitHub，通过PR合并回main。

```sh
git switch -c feature/intro
git status --short
git diff
git add README.md
git commit -m "补充分支工作流程"
git push -u origin feature/intro
```

这是操作流程说明；实际执行命令及结果单独记录。
