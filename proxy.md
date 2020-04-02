## 代理的设置
## ubuntu下配置v2ray
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

## 下载代码的时候使用proxy
```
git config --global http.proxy 'socks5://127.0.0.1:1080'
git config --global https.proxy 'socks5://127.0.0.1:1080'
```
或者更加方便的：
```
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
