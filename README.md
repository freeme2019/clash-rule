# Freeme‘s clash-rule

![IMAGE 2023-02-24 14:47:22](https://user-images.githubusercontent.com/47546008/221110953-699fcdc2-b1f0-4f0e-ad14-a94a7809bea8.jpg)

### https://raw.githubusercontent.com/freeme2019/clash-rule/main/freeme.ini
#### 本模版特色：在ACL4SSR模版基础上增强了更多的主流分流规则更符合大部分人的使用习惯，加强了广告拦截，配合下方设置以及漏网之鱼策略组选择代理 可基本实现防DNS泄漏，配合openclash subconverter可以在线更新订阅节点。（但可能不适合性能较低的路由器）
#### 使用方法为：
#### 1、打开openclash-配置文件订阅-在编辑配置文件订阅信息页面内，把订阅转换模板改为自定义模版并使用以上raw链接，订阅失败时建议多改几个订阅转换服务地址试试。
#### 2、如果加载出错，建议openclash先还原配置再使用，并且请在覆写设置页面修改Github地址为代理地址“https://ghproxy.com/”以防无法连接。
#### 还原openclash http://你的路由ip/cgi-bin/luci/admin/services/openclash/restore
#### 3、每次更新订阅后，建议关闭重启一次openclash以避免加载的yaml来自旧缓存。
#### 4、推荐openclash+mosdos设置（更新到最新版本）：

mosdos下载及安装：https://github.com/QiuSimons/openwrt-mos/releases 进入openwrt-系统-文件传输，上传上个ipk文件并安装即可，然后开启mosdns使用内置默认设置即可，设置两条国外dns建议8.8.4.4和1.1.1.1。

openclash 使用fake-ip(tun)模式，使用meta核心并开启嗅探功能（覆写设置-*启用 TCP 并发、启用Geodata数据库、探测（嗅探）纯 IP 连接、自定义流量探测（嗅探）设置，插件设置-流量控制-勾选：路由本机代理、禁用QUIC、绕过中国大陆IP，dns设置-本地劫持-关闭（使用mosdns转发）、禁止Dnsmasq缓存DNS，覆写设置-勾选 自定义上游DNS，Fake-IP 持久化，Fake-IP-Filter 和绕过中国大陆 IP ，勾选绕过中国大陆IP后即可排除大部分国内访问经过核心，但如果还有额外的不需要走代理的小众白名单域名也请加到Fake-IP-Filter里，dns只需要设一条nameserver，填个本地mosdns的监听端口即可，比如 127.0.0.1:5335,udp   然后在“网络”-DHCP/DNS页面，DNS 转发填入127.0.0.1#5335，最后重启一下mosdns 和openclash。

以上设置完毕基本可达到较好的上网体验。如使用redir-host模式建议开启fallback组dns（即以上相同的mosdns本地端口127.0.0.1:5335,udp ）及fallback-Filter

#### *广告拦截基于domain匹配和DNS拦截原理，基本可以阻挡90%以上的广告，但可能无法拦截某些流量加密型广告（https）和软件app内置广告，如有需要可配合客户端adguard之类的软件进行高精度防护
#### *正常登录chatgpt除了选择(未被滥用的)美国节点外，还需要打开代理的udp转发设置。
