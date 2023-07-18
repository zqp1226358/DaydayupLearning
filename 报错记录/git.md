

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
- pull的话 git pull --rebase origin main   拉取readme 看清楚是main分支

 > 如果已经建立好ssh连接的，之后修改origin 就直接拷贝ssh那个选项，不用看http那个选项
> 某天想改一下仓库的名称 然后再修改本地的  保持一致
> 使用命令git remote set-url origin  《yoururl》
> git remote -v 查看是否变动
> 期间因为换成了http那个链接，使用密码验证，自己搞了个token  因为21年之后就不能靠密码验证了
>
> 如果想改一下仓库的文件夹名称，也有相应的命令修改，有机会可以尝试一下
 
 ## 父子仓库问题
 git submodule add <url>
 
 ## git clone问题
 git clone在gittee默认是matser分支
 如果想要clone  dev分支的代码，就使用 git clone -b 分支名 仓库url

 ## 如果clone不全
 也有可能是带有自链接，试试这条命令git submodule update --init --recursive
 
 ## gitee 团队提交代码步骤
 
 先拉取代码
 
 然后git add .
 git commit -m "xx"
 git push origin dev
 输入gitee账号和密码  同旧qm
 
 
 ## 放弃刚刚修改的版本
 使用git  回滚命令
 https://blog.csdn.net/mus123/article/details/104200696
 
 ## git pull 报错
 Pull is not possible because you have unmerged files解决
 git reset --hard FETCH_HEAD
 https://blog.51cto.com/halolk/1304701
 
 ## git上传 取消上传 node_modules/ 内的文件
 在 gitignore 文件中添加 node_modules/
 
