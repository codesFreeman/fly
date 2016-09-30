GIT命令汇总

增加svn分支到git
git config --add svn-remote.2.2.x.url https://svn.jboss.org/repos/modeshape/branches/2.2.x/
git config --add svn-remote.2.2.x.fetch :refs/remotes/2.2.x
git svn fetch 2.2.x
git checkout -b local-2.2.x -t 2.2.x
git branch -a

查看未提交
git status 只能查看未传送提交的次数
git cherry -v 只能查看未传送提交的描述/说明
git log master ^origin/master 则可以查看未传送提交的详细信息

创建新空分支
git symbolic-ref HEAD refs/heads/newbranch
rm .git/index
git clean -df
git commit -m ‘init’
git push remoteName

git底层命令
git ls-files 展示文件
git ls-tree 展示对象树
git cat-file -p ID 用于查看对象内容
git rev-parse [HEAD|refs/heads/master|master] 用于显示引用对应的提交ID
git config core.logallrefupdates 提供分支日志功能此项返回true
git --exec-path git所有命令所在目录

git rev-parse 版本表示法
git rev-parse --symbolic --glob=refs/* 显示定义的所有引用
git rev-parse --symbolic —tags 显示里程碑
git rev-parse --symbolic —branches 显示所有分支

git rev-list 版本范围表示法

忽略文件
.gitignore

文件归档
git archive -o latest.zip HEAD 基于最新建立提交归档
git archive -o par.tar HEAD src doc 只将src doc建立到归档par.tar
git archive —format=tar —prefix=1.0/ v1.0|gzip > foo-1.0.tar.gz 基于里程碑v1.0建立归档，并为档案中的文件添加目录前缀1.0
