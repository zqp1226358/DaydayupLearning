error: RPC failed; curl 56 OpenSSL SSL_read: SSL_ERROR_SYSCALL, errno 10054
 

只需要设置Git忽略ssl证书错误即可，使用下面的命令：

git config --global http.sslVerify "false"
