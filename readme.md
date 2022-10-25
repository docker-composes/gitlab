# Gitlab 镜像

注意：
1. hostname 似乎只能是域名才能启动， 如：'example.com'。


查看日志：

```
docker logs -ft gitlab_web_1
```

查看管理员密码：

```
docker exec -it gitlab_web_1 grep 'Password:' /etc/gitlab/initial_root_password
```

登录链接：

http://localhost:1080


配置 LDAP 登录：

```
###! **remember to close this block with 'EOS' below**
gitlab_rails['ldap_servers'] = YAML.load <<-'EOS'
   main: # 'main' is the GitLab 'provider ID' of this LDAP server
     label: 'LDAP'
     host: '192.168.1.118'
     port: 389
     # uid: 'sAMAccountName'
     uid: 'uid'
     bind_dn: 'cn=admin,dc=example,dc=org'
     password: 'admin'
     encryption: 'plain' # "start_tls" or "simple_tls" or "plain"
     base: 'dc=example,dc=org'
     attributes:
       username : ['uid']
```
