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
