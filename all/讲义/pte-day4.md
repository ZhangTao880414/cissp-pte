# 渗透测试 PTE-PTS
## 渗透测试概念
  * 模拟攻击者
## 渗透测试流程
  * PEST
### 信息收集
#### 被动信息收集 - （社工）
  * 域名 - whois -- 注册邮箱
  * 子域名 -- google hacking
    - site / filetype xls/ inurl / error / warning
  * 电话号码 / ip段 / 简历 / 招聘信息
  * 端口/服务 -- shodan/zoomeye/fofa
  * 威胁情报库 OSINT
  * github / 云盘（云盘精灵）
  * CMS
  * 漏洞库信息
  * 微博 / facebook
#### 主动信息收集
  * 域名 -- dig / 子域名   C2：Command & Control 金丝雀 ATT&CK
  * ip -- 段
  * 端口 -- 服务
    - Tools ： nmap / ipscan / masscan
    - nmap： -p- / -Pn / -n / -sS / -sV / -O
      1. nmap -p- -Pn -n ip
      2. nmap -p 111 -sV ip
      - 网段 - 所有的linux -p 22
      - ipscan
  * 系统
  * Web 信息
    - 语言-框架/中间件/数据库 --- CMS
    - HTTP 截屏
    - 扫目录：
      - 后台 / robots.txt / zip/bak/old / upload / db / swp ~
      - 源代码 - form
      - Tools： 御剑 / Burp / dirbruter
   * 漏洞
    - 系统 - Nessus
    - Web  - AWVS
### 漏洞分析
  * Web应用：
    - Web ：SQL/file upload/文件包含/XXE/SSRF
    - CMS ：php -- wordpress/dede/dz/joomla……   zcms
      - wordpress ---- wpscan
    - 框架：tk/struts2/ java -- 反序列化
  * 中间件：tomcat -- 管理后台 -- 上传webshell /manager/html
  * 数据库：
    - mysql -- 提权root -- udf
    - sqlserver -- 提权sa -- xp_cmdshell
  * 操作系统：
    - msf
      1. msfconsole
      2. search xxx
      3. use xxx
      4. show options ---> set option xx
      5. show payloads --> set payload xx   powershell
      6. show options ---> set option xx
      7. run/exploit
    - py/rb/php/txt/c/
  * 网络：
    - 扫描/arp欺骗/AD域/snmp
  * 漏洞库信息
    - exploit-db/seebug/1337/cnvd/cve/github/twiter/facebook
### 漏洞利用(渗透测试)
 * 口令破解
    - Web类型 -- burp
    - 远程破解
      - 服务： ssh/mysql --- hydra/medusa/
      - hydra -l admin -P pwd.txt ip service
    - 本地破解
      - 系统
        * Windows
          1. SAM - c:/windows/system32/config
          2. LM / NTLM
          3. mimikatz/pwdump7
            - pwdump7.exe -s c:/windows/system32/config/SAM c:/windows/system32/config/SYSTEM > 1.txt
          4. hashcat -a 0 -m 1000 hash dic --force
          5. 彩虹表
        * Linux
          1. /etc/shadow /etc/passwd
          2. bcrypt
          3. john
      - 数据库
        * mysql -- 40位
 * Web漏洞
 * 数据库漏洞
 * 系统漏洞
### 后渗透
