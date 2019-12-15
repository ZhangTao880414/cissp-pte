# 复习
  * 判断注入点：
    - '  / 特殊符号
    - ' and 1=1 / ' and 1=2
    - ' and sleep(5)
  * 联合查询
    - order by / union select
  * 布尔注入
    - and exists() / ascii(mid(str,1,1))>96
  * 报错 updatexml(xml,xpath,string)
  * 延时 if(bool,1,2) sleep()
  * 文件读写 load_file('')  into outfile ''
  * 绕过
    - %0a/b  +--+ss  #%23  大小写
# Web安全
  * Web架构
  - 前端 / 后端 + 数据库
  * 前端
    - HTML/CSS/Javascript  vue / node.js
  * 后端
    - PHP - Apache - MySQL ----- ThinkPHP/Zend  3306
    - C# .NET -- IIS -- MSSQL                   1433
    - Java -- Apache/Tomcat -- Oracle -- ssh    1521
    - Python  --- flask/django
    - Redis -- 6379
## 文件上传
  * 文件上传原理
    - 接收文件  --> 移动到正常的目录下 uploads
    - 上传 一句话/webshell
  * 文件上传检查
    - 文件检查
      * 后缀名 -- 黑名单/白名单 -- 大小写
       - php = php3/4/5 phtml phar phpmoudle
       - .htaccess 加 解析 gif -- php
       - php. -- windows
      * MIME类型 -- image/png  application/octet--stream
      * 文件头 -- gif/GIF89a
      * 文件大小
      * 文件内容 - eval
    - 隐藏路径/文件名改名
    - 解析漏洞
    - 00截断
  * 文件上传流程
    1. 上传一张正常的图片
    2. 抓包--repeater里每次更改一项检查点
  * 一句话与Webshell
    - Webshell --- 语言 php
    - 一句话 --- 菜刀/蚁剑/冰蝎
## 文件包含
  * 文件包含原理
    -require/include --- 包含文件
  * 文件包含用法
    - http://localhost/dvwa/vulnerabilities/fi/?page=file1.php
    - 包含的文件如果是php代码，会被执行
    - 路径 -- 相对
    - ?file=../../etc/passwd
    - php://filter/read=convert.base64-encode/resource=../etc/passwd
  * 本地文件包含
  * 远程文件包含
    - curl/wget/system -- 注意一点：不能在远程解析执行
    - 一句话
## 命令执行
  - 分隔符 ; & |
  - 绕过 cat/tac/less/more/tail/head
  - curl
  - ip -- 192.168.1.12/ 12345675433
## XSS
  - XSS原理 --- HTML注入
  - js -- 获取cookie -- 发送到远端服务器
  - 反射型 url
  - 存储型 数据库
  - beef
## 代码审计
 - GET/POST/REQUEST
 - 危险函数

## 漏洞
  - 过滤不严格
  - 配置
