# proxy-rules
国内使用代理规则

使用远程文件或下载本地使用：
使用本地时type: file，使用远程时type: http
````yaml

#---------------------------------------------------#
## 配置文件需要放置在 $HOME/.config/clash/*.yaml

## 这份文件是clashX的基础配置文件，请尽量新建配置文件进行修改。
## ！！！只有这份文件的端口设置会随ClashX启动生效

## 如果您不知道如何操作，请参阅 官方Github文档 https://github.com/Dreamacro/clash/blob/dev/README.md
#---------------------------------------------------#

# (HTTP and SOCKS5 in one port)
mixed-port: 7890
# RESTful API for clash
external-controller: 127.0.0.1:9090
allow-lan: false
mode: rule
log-level: warning

proxies:

proxy-groups:

rules:
  - DOMAIN-SUFFIX,google.com,DIRECT
  - DOMAIN-KEYWORD,google,DIRECT
  - DOMAIN,google.com,DIRECT
  - DOMAIN,aliyun.com,DIRECT
  - DOMAIN,csdn.net,DIRECT
  - DOMAIN-SUFFIX,ad.com,REJECT
  - GEOIP,CN,DIRECT
  - MATCH,DIRECT
# 内容：可以自行添加其它自己想要的规则
# ACL4SSR Online
  - RULE-SET,LocalAreaNetwork,DIRECT
  - RULE-SET,UnBan,DIRECT
  - RULE-SET,BanAD,REJECT
  - RULE-SET,BanProgramAD,REJECT
  - RULE-SET,GoogleFCM,DIRECT
  - RULE-SET,GoogleCN,DIRECT
  - RULE-SET,SteamCN,DIRECT
  - RULE-SET,Microsoft,DIRECT
  - RULE-SET,Apple,DIRECT
  - RULE-SET,Telegram,DIRECT
  - RULE-SET,ProxyLite,DIRECT
  - RULE-SET,ProxyMedia,DIRECT
  - RULE-SET,ChinaDomain,DIRECT
  - RULE-SET,ChinaCompanyIp,DIRECT
  - GEOIP,CN,DIRECT
  - MATCH,DIRECT
payload:
  # 添加下面的, 跟在后面
  - DOMAIN-SUFFIX,cn,Direct
  - DOMAIN-KEYWORD,geosite,Proxy
  - IP-CIDR,10.0.0.0/8,Direct
  - IP-CIDR,172.16.0.0/12,Direct
  - IP-CIDR,192.168.0.0/16,Direct
  - IP-CIDR,127.0.0.0/8,Direct
  - IP-CIDR,224.0.0.0/4,Direct
  - IP-CIDR,240.0.0.0/4,Direct
  - MATCH,Final
  # - IP-CIDR,10.0.0.0/8,Direct
  # - IP-CIDR,172.16.0.0/12,Direct
  # - IP-CIDR,192.168.0.0/16,Direct
  # - IP-CIDR,100.64.0.0/10,Direct
  # - IP-CIDR,::ffff:a00:0/108,Direct
  # - IP-CIDR,::ffff:ac10:0/108,Direct
  # - IP-CIDR,::ffff:c0a8:0/112,Direct
  # - IP-CIDR,fc00::/7,Direct
  # - IP-CIDR,fe80::/10,Direct

  # # 其它流量走 Proxy
  # - MATCH,AutoCN,Direct
  # - IP-CIDR,0.0.0.0/0,Proxy

rule-providers:
# 内容：可以自行添加其它自己想要在线规则列表
  LocalAreaNetwork:
    behavior: classical # domain, ipcidr or classical (premium core only)
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/LocalAreaNetwork.yaml"
    interval: 86400
    path: ./ACL4SSR/LocalAreaNetwork.yaml
  UnBan:
    behavior: classical 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/UnBan.yaml"
    interval: 86400
    path: ./ACL4SSR/UnBan.yaml
  BanAD:
    behavior: classical 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/BanAD.yaml"
    interval: 86400
    path: ./ACL4SSR/BanAD.yaml
  BanProgramAD:
    behavior: classical 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/BanProgramAD.yaml"
    interval: 86400
    path: ./ACL4SSR/BanProgramAD.yaml
  GoogleFCM:
    behavior: classical 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/Ruleset/GoogleFCM.yaml"
    interval: 86400
    path: ./ACL4SSR/GoogleFCM.yaml
  GoogleCN:
    behavior: classical 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/Ruleset/GoogleCN.yaml"
    interval: 86400
    path: ./ACL4SSR/GoogleCN.yaml
  SteamCN:
    behavior: classical 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/Ruleset/SteamCN.yaml"
    interval: 86400
    path: ./ACL4SSR/SteamCN.yaml
  Microsoft:
    behavior: classical 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/Ruleset/Microsoft.yaml"
    interval: 86400
    path: ./ACL4SSR/Microsoft.yaml
  Apple:
    behavior: classical 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/Ruleset/Apple.yaml"
    interval: 86400
    path: ./ACL4SSR/Apple.yaml
  Telegram:
    behavior: classical 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/Ruleset/Telegram.yaml"
    interval: 86400
    path: ./ACL4SSR/Telegram.yaml
  ProxyLite:
    behavior: classical 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/ProxyLite.yaml"
    interval: 86400
    path: ./ACL4SSR/ProxyLite.yaml
  ProxyMedia:
    behavior: classical 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/ProxyMedia.yaml"
    interval: 86400
    path: ./ACL4SSR/ProxyMedia.yaml
  ChinaDomain:
    behavior: classical 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/ChinaDomain.yaml"
    interval: 86400
    path: ./ACL4SSR/ChinaDomain.yaml
  ChinaCompanyIp:
    behavior: ipcidr 
    type: file
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/ChinaCompanyIp.yaml"
    interval: 86400
    path: ./ACL4SSR/ChinaCompanyIp.yaml


````
