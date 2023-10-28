# git_cmd
```bash
git 仓库创建
mkdir gitrepo
chown git:git gitrepo/
cd gitrepo
git init --bare test.git
chown -R git:git test.git
git clone git@10.252.1.146:/home/gitrepo/test.git
添加现有仓库到远端仓库：
git remote rm origin
git remote add origin git@10.252.1.15:/home/gitrepo/xx.git
git push --set-upstream origin master
添加gitignore,以及过滤规则
git rm -r --cached .
git add .
git commit -m “add gitignore”
git push

git checkout -b dev（本地分支名） origin/dev（远程分支名）

git fetch origin

git clean -dfx 
git checkout .

```