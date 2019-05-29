# mediago
## 1. 什么是mediago
quic是基于udp的下一代高质量传输协议。mediago用quic协议来传输rtmp直播流。<br>
mediago在实现普通rtmp over tcp的基础上，同时实现rtmp over quic的服务，提供弱网环境下/高RTT等网络环境下的流媒体服务。

## 2. 什么应用场景适合rtmp over quic
什么应用场景适合rtmp over quic。这要基于quic传输优点：
* connect连接建立的低延时
* 灵活的拥塞控制
* 无头部阻塞的多路复用(TCP是有头部阻塞的)
* 对头部和负载进行认证和加密
* 流和连接的流控
* 连接迁移
<br/>

笔者总结常用场景：<br/>
* 网络丢包率高 <br/>
网络带宽足够，但是网络质量差，容易丢包，容易连接断开。<br/>
因为quic有0RTT快速连接的能力，丢包重传中ACK回复的block大，能容忍碎片丢包等特性，比传统TCP好很多。
* 长距离传输 <br/>
网络传输RTT比较高，quic在连接断开后的重连是0RTT，高效传输数据。

## 3. 如何使用mediago
mediago非常适合做弱网环境直播，或跨国长距离直播。<br>
### 3.1 mediago支持功能简介:<br/>
* rtmp over tcp推拉流
* rtmp over quic推拉流
* httpflv over tcp
* http over quic
* 基于tcp服务器间回源
* 基于quic服务器间回源

<br>

### 3.2 运行环境
linux：笔者在centos上使用

### 3.3 wiki文档
wiki: [使用说明](https://github.com/runner365/mediago_bin/blob/master/doc/Index.md)

### 3.4 quic协议翻译
[quic协议翻译精选](https://github.com/runner365/read_book/blob/master/Quic/Quic_Wire_layout_specification_%E8%87%AA%E8%AF%91.md)
