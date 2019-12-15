# 复习
  * 信息收集
    - 端口 nmap -p- -sV
    - Web -- 扫后台 - 御剑/Burp - robot-
# 渗透测试
## 漏洞利用
* 口令破解
  - Web口令 -- Burp（Tomcat）：请求头/Base64/admin：123
  - 数据库密码：暴力破解/配置文件 conn/config
  - 系统： Windows - mimikatz
* Web漏洞
  - SQL 注入
    1. 联合查询/暴力破解/文件读写
    2. 找注入点 -- 工具扫描 参数  ?id=
    3. waf
  - 文件上传  上传点 -- 扫后台
    1. 常见检查绕过
    2. 网站设置 --- 直接改 文件上传类型，增加asp/php
    3. 00截断 --16进制00  -- 有上传路径
    4. 解析漏洞
      - IIS解析
        - 文件： a.asp;.jpg
        - 目录： a.asp/1.jpg
      - Apache
        - 1.php.jpg
    5. 备份功能 - 数据库 -- 改名：只能传图片 jpg --> asp
    /admin/upfiles/201911870011.jpg
    http://192.168.193.129:81/gouwu/
    6. 编辑器漏洞
---- 提权 -----
1. 系统漏洞：远程/本地
2. 数据库
3. 其他应用：
* 数据库漏洞
  - MySQL
    - UDF
  - MSSQL
    - xp_cmdshell ： sa
* 系统漏洞
 - 常用命令
  * 基本
    - Win：cd / type / echo /systeminfo
  * 用户  whoami /all ; net user / net localgroup
    - net user test test /add  创建用户
    - net localgroup administrators test /add
    Linux：
    - useradd test / w / history
  * 进程
    - tasklist | findstr ; taskkill
    - ps -ef | grep / top ; kill -9
  * 网络
    - ipconfig / netstat -ano
    - netstat -ntlp
