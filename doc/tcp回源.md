# TCP回源

## 1. TCP回源组网
<pre>
rtmp pull client X<---[mediago server A]<---[mediago server B]<---rtmp push client Y
</pre>

如上图: pull client X去server A拉流，A若没有对应的流，就去server B回源。<br/>

## 2. 如何配置回源
<pre>
{
    "loglevel":"info",
    "listen": 1935,
    "httpoper": "enable",
    "operport": 8090,
    "httpflv": "enable",
    "flvport": 8000,
    "servers":[
        {
            "servername":"live",
            "gopnumber":2,
            "upstream_enable":"enable",
            "upstream_host":["x.x.x.x"],
            "upstream_type":"tcp"
        }
    ]
}
</pre>
其中: <br/>
* "upstream_enable":"enable": <br/>
为使能回源功能
* "upstream_host":["x.x.x.x"]: <br/>
x.x.x.x为上游server的hostip或域名
* "upstream_type":"tcp": <br/>
表示回源的传输协议使用传统的tcp


