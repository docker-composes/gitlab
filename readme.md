# Gitlab 镜像

注意：
1. hostname 似乎只能是域名才能启动， 如：'example.com'。

查看管理员密码：

```
docker exec -it gitlab_web_1 grep 'Password:' /etc/gitlab/initial_root_password
```

登录链接：

http://localhost:1080