# Clash-Rule
private function only
仅供自己使用

## 一些修改过的设置:
port: 7890
<br/>
socks-port: 7891
<br/>
redir-port: 7892
<br/>
mixed-port: 7893
<br/>
allow-lan: false
<br/>
mode: Rule
<br/>
log-level: error
<br/>
ipv6: false
<br/>
external-controller: 127.0.0.1:50048

## 配置解释:
### hosts
添加了
<br/>
mtalk.google.com
<br/>
services.googleapis.cn
<br/>
raw.githubusercontent.com

### DNS:
默认关闭ipv6
<br/>
默认使用redir-host模式
<br/>
未保留fakeip模式, 在测试中已知会造成解析错误、与TUN模式起冲突等多种问题
<br/>
默认使用dns53以获得最快响应速度
<br/>
保留备用的dot和doh设置, 防止污染情况出现

### fallback-filter:
开启GEO-IP
<br/>
设置ipcidr - 240.0.0.0/4
<br/>
添加部分常用域名

### 系统层代理:
0.13.8版本之后, 此设置已从TAP网卡模式替换为TUN模式, 以获得更好的性能
1.<br/>
设置WinTUN配合Service Mode接管不遵循系统代理的软件

### proxy-groups:
以下基于ACL4SSR的配置文件进行部分改动

| 分组                    | 类型                 |
| ---------------------- | -------------------- |
|🚀                      | 代理列表，包含常用的、以及被污染的域名                                        |
| Google服务              | Google的域名                                                             |
| Youtube                | YouTube服务的分流                                                         |
| Telegram               | Telegram的域名                                                           |
| Netflix                | Netflix服务的域名                                                         |
| 巴哈姆特                | 巴哈姆特服务的域名                                                          |
| 国内媒体                | 国内媒体网站的域名                                                          |
| 哔哩哔哩                | Bilibili网站内大陆地区的分流                                                |
| 游戏平台                | PS、Steam等游戏平台的域名                                                   |
| Microsoft              | 微软公司的域名                                                             |
| OneDrive               | 微软公司OneDrive服务的分流                                                 |
| Apple                  | 苹果公司的域名                                                             |
| 优先直连                | 优先考虑直连的域名、例如国内公司、BT下载、国内网盘、有CDN加速的网站                |
| 拦截                   | 包含常见广告关键字、广告联盟                                                  |
| Others                 | 除配置之外的所有域名, 默认走代理                                              |
