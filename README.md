# vless

## 概述一个支持多种编程语言的云平台即服务。目前支持Ruby、Java、Node.js、Scala、Clojure、Python、PHP和Perl等语言，基础操作系统是Debian。



## 镜像

经测试本镜像占用内存资源较低，运行稳定。

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https%3A%2F%2Fgithub.com%2Frptec%2Fheroku-vless)

## 注意

### 路径

`WebSocket` 路径(配置文件中的 `path` )为 `/` 。你也可以自行修改

### 端口

`端口` 为 `443` 。 


### UUID

`UUID` 默认为 `10974d1a-cbd6-4b6f-db1d-38d78b3fb109` 你也可以在部署时自由修改（建议修改）。

## 流量中转

使用cloudflare的workers来`中转流量`，配置为： 

```
addEventListener(
      "fetch",event => {
         let url=new URL(event.request.url);
         url.hostname="你的heroku域名.herokuapp.com";
         let request=new Request(url,event.request);
         event. respondWith(
           fetch(request)
         )
      }
    ) 
```


