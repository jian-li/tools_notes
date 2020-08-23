## 代理的设置
[TOC]
## ubuntu下使用kcp代理的设置 
已经配置好了`kcp`和`ssr`工具的启动脚本，只需要安装好环境就好。
```
sudo apt install shadowsocks
```

## ubuntu下使用v2ray代理的配置
```
curl -L -s https://install.direct/go.sh > go.sh
sudo bash go.sh
vim /etc/v2ray/config.json
```
文件的内容为：
```
{
  "inbounds": [{
    "port": 1080,
    "listen": "0.0.0.0",
    "protocol": "socks",
    "settings": {
      "auth": "noauth",
      "udp": true
    }
  }],
  "outbounds": [{
    "protocol": "vmess",
    "settings": {
      "vnext": [{
        "address": "xxx.xxx.xxx.xxx",
        "port": xxxx,
        "users": [{
          "id": "xxxx",
          "alterId": xxxx
        }]
      }]
    }
  }]
}
```
修改完之后，启动`v2ray`的命令如下：
```
sudo systemctl start v2ray.service
sudo systemctl status v2ray.service
```
## pip下载仓库的时候使用proxy
首先下载`pysocks`工具，然后在下载代码的时候使用`pysocks`代理。
```
sudo pip install pysocks
pip install <yourpacakge> --proxy socks5:127.0.0.1:1080
```

## 下载代码的时候使用proxy
```
git config --global http.proxy 'socks5://127.0.0.1:1080'
git config --global https.proxy 'socks5://127.0.0.1:1080'
```
或者更加方便的：
```
git clone -c http.proxy=socks5://127.0.0.1:1080 http://xxxx
```
##wget使用socks5代理
下载tsocks工具，命令如下：
```
sudo apt-get install tsocks -y
```
配置tsocks，将/etc/tsocks.conf里面的所有内容注释，只留下如下的几行，修改server，最终的文件有效内容为：
```
server = 127.0.0.1
server_type = 5
server_port = 1080
```
下载的时候命令如下
```
tsocks wget -c https://xxxxxx
```

## socks5转http和https
这里使用的工具是goproxy,下载的方法为：
```
git clone https://github.com/elazarl/goproxy
```
