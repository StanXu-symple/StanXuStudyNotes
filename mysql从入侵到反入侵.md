# mysql从入侵到反入侵

## 摘要

今天登陆了我许久未登录的腾讯云mysql，发现我库表都没了，映入眼帘的只有一条勒索信息，我淦，还有这操作！于是下定决心学学mysql的安全和相关语句

![image-20210310114740334](\picture\Beinvaded.png)

## mysql远程登录认证

```mysql
--授权root用户可以从任意电脑登录MySQL数据库。如下所示：
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'youpassword' WITH GRANT OPTION;

--授权root用户可以从10.10.1.35登录MySQL数据库，如下所示：
GRANT ALL PRIVILEGES ON *.* TO 'root'@'10.10.1.35' IDENTIFIED BY 'youpassword' WITH GRANT OPTION;

--grant 普通数据用户，查询、插入、更新、删除 数据库中所有表数据的权利
grant select on testdb.* to common_user@'%'  
grant insert on testdb.* to common_user@'%'  
grant update on testdb.* to common_user@'%'  
grant delete on testdb.* to common_user@'%'  
```

## mysql-用户表详解

[https://www.cnblogs.com/liuhaidon/archive/2019/09/12/11511129.html](https://www.cnblogs.com/liuhaidon/archive/2019/09/12/11511129.html)

