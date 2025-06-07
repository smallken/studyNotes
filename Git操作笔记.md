# Git操作笔记

## 1.实现本地连接远程库

1. 前提条件：

   - 远程已经创建了库；
   - 本地建立了项目，但没有上传到远程；
   - 远程是空库；
   - 本地已经绑定了远程github的密钥。

2. 增加远程绑定；

   增加：`git remote add origin github.com/smallken/wtfswap`

   origin是远程的别名

   git push -u origin main

   git remote -v显示成功了。

   报错了：error: src refspec main does not match any

   这个应该是推送的分支本地没有，git branch显示是master，修改分支名：

   git branch -M main

   又报错了：fatal: 'github.com/smallken/wtfswap' does not appear to be a git repository

   应该是链接不对，取消绑定。

   git remote remove origin

   重新绑定：git remote add origin https://github.com/smallken/wtfswap

   可能会报这个错：
   >Updates were rejected because the remote contains work that you do
   >hint: not have locally. This is usually caused by another repository pushing
   >hint: to the same ref. You may want to first integrate the remote changes
   >hint: (e.g., 'git pull ...') before pushing again.
   >hint: See the 'Note about fast-forwards' in 'git push --help' for details.

   强制推送：git push -u -f origin main

   