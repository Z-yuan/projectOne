Git is a distributed version control system.
Git is free software.
添加用户名
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
显示当前目录pwd
把这个目录变成Git可以管理的仓库：git init
第一步，用命令git add告诉Git，把文件添加到仓库：
git add text.txt
第二步，用命令git commit告诉Git，把文件提交到仓库：
git commit 
简单解释一下git commit命令，-m后面输入的是本次提交的说明
git commit -m "这次改动的说明"
git status命令可以让我们时刻掌握仓库当前的状态
git status
git diff查看修改内容
git diff
修改测试