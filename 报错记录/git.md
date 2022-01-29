

## error: RPC failed; curl 56 OpenSSL SSL_read: SSL_ERROR_SYSCALL, errno 10054
 
只需要设置Git忽略ssl证书错误即可，使用下面的命令：

git config --global http.sslVerify "false"


## git无法pull仓库refusing to merge unrelated histories
如果合并了两个不同的开始提交的仓库，在新的 git 会发现这两个仓库可能不是同一个，为了防止开发者上传错误，于是就给下面的提示：fatal: refusing to merge unrelated histories
如我在Github新建一个仓库，写了License，然后把本地一个写了很久仓库上传。这时会发现 github 的仓库和本地的没有一个共同的 commit 所以 git 不让提交，认为是写错了 origin ，如果开发者确定是这个 origin 就可以使用 --allow-unrelated-histories 告诉 git 自己确定
因为他们是两个不同的项目，要把两个不同的项目合并，git需要添加一句代码，在 git pull 之后，这句代码是在git 2.9.2版本发生的，最新的版本需要添加 --allow-unrelated-histories 告诉 git 允许不相关历史合并
假如我们的源是origin，分支是master，那么我们需要这样写
git pull origin master --allow-unrelated-histories 如果有设置了默认上传分支就可以用下面代码

我的解决是git pull origin main --allow-unrelated-histories

## git push前先git pull

## 使用git commit命令时遇到 fatal: Unable to create index.lock File exists 错误的解决办法
在项目根目录下找到 .git 文件夹。打开该文件夹。找到文件夹里面的index.lock 文件，将其删除，即可解决问题。


## git 大致步骤

- git init
- git add .
- git commit -m "1"
- git branch -M main
- git remote add origin <url>
- git push -u origin main  (push考虑要不要pull)
 
 ## 父子仓库问题
 git submodule add <url>
 
