shadowsocks-chisel
==================

[shadowsocks](https://github.com/shadowsocks/shadowsocks-go) + [chisel](https://github.com/jpillora/chisel) = ❤❤

### necessary tool
* [docker](https://docs.docker.com/install/)
* chisel 
    * mac + linux cmd输入安装 `curl https://i.jpillora.com/chisel! | bash` 
    * windows需要去 [这里](https://github.com/jpillora/chisel/releases/tag/1.3.1) 下载exe  
* 任意一种ss
    * mac: [ShadowsocksX-NG](https://github.com/shadowsocks/ShadowsocksX-NG)
    * windows: [Shadows-windows](https://github.com/shadowsocks/shadowsocks-windows/releases)
    * Linux: 都用Linux了肯定知道ss怎么搞，一般是命令行的，这边举例一个[Shadowsocks-go](https://github.com/shadowsocks/shadowsocks-go/releases)，具体自行研究吧

### Getting started

1. 首先你需要下载一个，不然是跑不起来的

2. 克隆本项目到本地

3. 在命令行中进入项目目录

4. 输入命令

```bash
heroku login # 首先你需要登录，如果已经登录了就不用了。
heroku container:login # 这里要求 docker 正在运行，link docker
heroku create # 创建应用
heroku config:set CHISEL_AUTH=user:pass METHOD=rc4-md5 KEY=foobar # 设置应用的运行变量
heroku container:push web # 开始构造
heroku container:release web # 让服务器的程序跑起来
```

5. 至此heroku部分完成，接下来是 link, 如果 link 成功了会输出的日志会有 `client: Connected`  


```
$ chisel client --auth user:pass --keepalive 50s https://stormy-castle-77230.herokuapp.com 8388
2018/01/09 00:46:14 client: Connecting to wss://stormy-castle-77230.herokuapp.com:443
2018/01/09 00:46:14 client: tunnel#1 0.0.0.0:8388=>0.0.0.0:8388: Listening
2018/01/09 00:46:16 client: Fingerprint c9:a3:f1:ad:fd:52:7f:8e:9b:92:c1:40:2e:79:44:ce
2018/01/09 00:46:18 client: Connected (Latency 300.439478ms)
```
随后使用任意一种ss，填写服务器信息就可以连上了。
最上面有链接，下面是配置。

服务器： 127.0.0.1:8388
加密方式：rc4-md5
密码：foobar
