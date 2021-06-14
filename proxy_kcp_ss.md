# kcp_ss加速


这里安装的`shadowsocks`和`kcptun`用的都是`docker`的方式，方法很简单。

## 安装`docker`
```
# 安装docker-ce
sudo apt-get install -y install docker-ce
systemctl start docker
```
### 服务器端配置
## 安装`shadowsocks`
```
docker pull shadowsocks/shadowsocks-libev
```
然后就是创建容器并启动
```
docker run --privileged --restart=always -tid -e PASSWORD=12345 -e METHOD=aes-256-cfb -p 20000:8388 -p 20000:8388/udp shadowsocks/shadowsocks-libev
```

## 安装`kcptun`
使用下面的命令：
```
docker pull xtaci/kcptun
docker run -p 20001:20001 -p 20001:20001/udp -v /kcptun:/kcptun -d --restart=always xtaci/kcptun server -c "/kcptun/config.json"
```
【注意】需要创建`/kcptun`文件夹，并且讲`config.json`文件放到`/kcptun`目录下。然后就是`kcptun`的端口和`shadowsocks`的端口并不是一个端口（这个应该是运行端口），消息的传播是用`config.json`文件定义的。

这里的`config.json`文件是`kcptun`的配置文件，具体的内容如下所示：
```
{
    "listen":":20001",
    "target":"x.x.x.x:20000",
    "key":"qazwsxedc",
    "crypt":"aes-192",
    "mode":"fast3",
    "autoexpire":60
}
```
其中`target`的`x.x.x.x`是`vps`的`ip`地址。

### 客户端配置
## `mac`下配置
`mac`端的配置用的是`Shadowsocks-NG`，
配置如下所示：
![mac上Ss-NG配置参数](imgs/mac_images.jpg)
其中:
- 1是`shadowsocks`的配置参数，其中，`Port`需要使用`kcptun`映射之后的端口。
- `kcptun`的配置参数和`config.json`文件里面的一样。

## `windows`下配置


## `ubuntu`下配置



