# Mysql
### ✅常用命令✅
#### 0.连接
```bash
mysql -h {host} -u {username} -P {port} -p -t {dbname}
```
#### 1.用户管理
#### 1.1 增
```sql
create user zhangsan identified by 'zhangsan';
create user misp identified by 'misp';
```
#### 1.2 授权
```sql
grant {privilegesCode 授权类型} on zhangsanDb.* to zhangsan@'%' identified by 'zhangsan'; flush privileges;
flush privileges;
```
```
privilegesCode授权类型枚举：
* all privileges：所有权限。
* select：读取权限。
* delete：删除权限。
* update：更新权限。
* create：创建权限。
* drop：删除数据库、数据表权限。
```
#### 1.3 改密
```sql
update mysql.user set password = password('zhangsannew') where user = 'zhangsan' and host = '%'; 
flush privileges;
```
#### 1.4 删
```sql
drop user zhangsan@'%';
```

### 2.curd
#### 2.1 增
#### 2.2 删
#### 2.3 改
#### 2.4 查


### 🔶不常用命令🔶
#### 1.Online DDL
##### 更改表名
```sql
alter table <table_name> rename to <new_table_name>
```
#### text字段类型改json
```sql
alter table <table_name> modify <field_name> json;
```
#### 2.备份与恢复表
##### 2.1 表备份成sql文件
```sql
mysqldump -h {host} -u {username} -P {port} -p {password} -t {dbname} > dump.sql
```
##### 2.2 sql文件恢复成表
```sql
mysql -h {host} -u {username} -P {port} -p {password} -t {dbname}  < dump.sql
```
##### 2.3 高效的本地库内复制
```sql
1. 复制表结构及数据到新表：create table <new table> select * from <old table>
2. 只复制表结构到新表（此时会默认使用innodb）：create table <new table> select * from <old table> where 1 = 2 
```
#### 3.
##### 3.1


### 参考文档
* [官方文档](https://mongoing.com/docs/index.html)
* [菜鸟教程](https://www.runoob.com/mongodb/mongodb-tutorial.html)


