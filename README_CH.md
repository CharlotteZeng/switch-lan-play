# 必要条件
- PC与Switch
- PC与Switch必须在同一路由器网络内，当然如果你有win10，可以尝试win10发射热点，个人不做保障。
- 正版NS也可以使用，因为这并不是破解，而是利用网络将局域网放大（我们本身就在一个很大的局域网内就是了），无关破解。


# 1、PC端
- 下载并安装[WinPcap](https://www.winpcap.org/install/default.htm)
- 下载[lan-play工具](https://github.com/spacemeowx2/switch-lan-play/releases)
- 使用管理员权限运行这个lan-play工具，你会看到下面这个
```
lan-play.exe --relay-server-addr ip:11451
```  
后面的ip:11451是你需要填写的，至于ip，则是你部署服务器的ip，当然如果你有域名，也可以使用域名。

之后你会看到

```
1. \Device\NPF_{538AED4A-7BC9-47D9-A1DD-3F8E0AD2D2B0} (Microsoft Corporation)
        IP: [10.0.75.1]
2. \Device\NPF_{A885EB2A-D362-4846-8554-E6F59A044EB9} (Intel(R) Ethernet Connection (2) I219-V)
        IP: [192.168.233.153]
Enter the interface number (1-2):
```  
类似上面的信息，根据个人的情况而定，输入想要的数字即可。

PC端工作完成。

# 2、Switch端
- switch打开Internet，进入WiFi，连接与PC在同一路由器上的WiFi，连接后点击Internet settings,Change Settings,IP Address Settings选择Manual，在IP Address填入10.13.?.?，后面两个?是1~254任意数字，但是不能与其他连接同一服务器的NS设置为一样的。
- Subnet Mask填入255.255.0.0
- Gateway填入10.13.37.1
- DNS内填写8.8.8.8以及8.8.4.4或是其他你知道的都行，这里不做限制。
- 在想要联网玩的游戏内按下L+R+左手柄，切换为局域网，即可游玩。目前支持的游戏很少，仅仅是老任第一方的支持。

# 3、服务器端部署
- 需要git，具体百度Linux如何安装git，如果你是win服务器当我没说。
- 需要npm，还是百度Linux如何安装npm，如果你还是win服务器还是当然没说。
- 运行以下代码。
```
git clone https://github.com/spacemeowx2/switch-lan-play.git
cd switch-lan-play/server
npm install
npm run build
npm run server
```  

成功后你会看到![QQ20181006-125008.png](https://ws1.sinaimg.cn/large/c13993a9gy1fvyf02bphgj20i604n0t4.jpg)
后面的Client count表示已连接的数量，PC上运行lan-play后输入正确的服务器ip以及端口，即可显示，再往后就是流量显示了。
