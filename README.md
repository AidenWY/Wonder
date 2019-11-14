# Resources
    v2ray白话版：https://toutyrater.github.io/
    v2ray手册：https://www.v2ray.com/
    docker中文版手册（目前貌似已经停止更新，不是最新版本，仅能做参考用）：https://bingohuang.gitbooks.io/docker_practice/content/
    v2ray工具及GUI源码（and、win、mac都有在git上托管源码，ios没有）：https://bingohuang.gitbooks.io/docker_practice/content/

# Interface
   ### POST  "/login" 
   ###### with json
     {
	    "email": "xxx", 格式校验没做
	    "password": "xxx",
	    "udid": "xxx",
     }
   ### POST  "/register"
   ###### with json
     {
	    "email": "xxx", 格式校验没做
	    "password": "xxx",
	    "udid": "xxx",
     }
   ### POST  "/auth/serverConfig" 
   ###### with token in headers 
    wt: token
   ###### and with json
    {
	"region": "xxx"
    }
   ### GET   "/refresh/token"
   ###### with token in headers
    mt: token
# Data Simple 
  ### long
    {
    "data": {
        "log": {
            "loglevel": "info"
        },
        "outbounds": [
            {
                "tag": "proxy",
                "settings": {
                    "vnext": [
                        {
                            "port": xxx,
                            "users": [
                                {
                                    "security": "xxx",
                                    "id": "xxxx",
                                    "alterId": xxx
                                }
                            ],
                            "address": "xxx"
                        }
                    ]
                },
                "mux": {
                    "enabled": false,
                    "concurrency": 8
                },
                "streamSettings": {
                    "wsSettings": {
                        "path": "/"
                    },
                    "network": "ws",
                    "tlsSettings": {
                        "allowInsecure": true
                    },
                    "security": "tls"
                },
                "protocol": "vmess"
            },
            {
                "tag": "direct",
                "settings": {
                    "userLevel": 2018,
                    "domainStrategy": "AsIs"
                },
                "streamSettings": {},
                "protocol": "freedom"
            },
            {
                "protocol": "blackhole",
                "tag": "block",
                "settings": {}
            }
        ],
        "routing": {
            "rules": [
                {
                    "type": "field",
                    "domain": [
                        "domain:doubleclick.net"
                    ],
                    "outboundTag": "block"
                },
                {
                    "type": "field",
                    "domain": [
                        "domain:setup.icloud.com"
                    ],
                    "outboundTag": "proxy"
                },
                {
                    "type": "field",
                    "ip": [
                        "8.8.8.8/32",
                        "8.8.4.4/32",
                        "1.1.1.1/32",
                        "1.0.0.1/32",
                        "9.9.9.9/32",
                        "149.112.112.112/32",
                        "208.67.222.222/32",
                        "208.67.220.220/32"
                    ],
                    "outboundTag": "proxy"
                },
                {
                    "type": "field",
                    "ip": [
                        "geoip:cn",
                        "geoip:private"
                    ],
                    "outboundTag": "direct"
                },
                {
                    "type": "field",
                    "outboundTag": "direct",
                    "port": "123"
                },
                {
                    "type": "field",
                    "domain": [
                        "domain:pstatp.com",
                        "domain:snssdk.com",
                        "domain:toutiao.com",
                        "domain:ixigua.com",
                        "domain:apple.com",
                        "domain:crashlytics.com",
                        "domain:icloud.com",
                        "cctv",
                        "umeng",
                        "domain:weico.cc",
                        "meituan",
                        "dianping",
                        "maoyan",
                        "domain:ele.me",
                        "domain:elemecdn.com",
                        "domain:eleme.cn",
                        "domain:jd.com",
                        "domain:360buy.com",
                        "domain:360buyimg.com",
                        "domain:douyu.tv",
                        "domain:douyu.com",
                        "domain:douyucdn.cn",
                        "geosite:cn"
                    ],
                    "outboundTag": "direct"
                },
                {
                    "type": "field",
                    "ip": [
                        "149.154.167.0/24",
                        "149.154.175.0/24",
                        "91.108.56.0/24",
                        "125.209.222.0/24"
                    ],
                    "outboundTag": "proxy"
                },
                {
                    "type": "field",
                    "domain": [
                        "twitter",
                        "domain:twimg.com",
                        "domain:t.co",
                        "google",
                        "domain:ggpht.com",
                        "domain:gstatic.com",
                        "domain:youtube.com",
                        "domain:ytimg.com",
                        "pixiv",
                        "domain:pximg.net",
                        "tumblr",
                        "instagram",
                        "domain:line-scdn.net",
                        "domain:line.me",
                        "domain:naver.jp",
                        "domain:facebook.com",
                        "domain:fbcdn.net",
                        "pinterest",
                        "github",
                        "dropbox",
                        "netflix",
                        "domain:medium.com",
                        "domain:fivecdm.com"
                    ],
                    "outboundTag": "proxy"
                }
            ],
            "domainStrategy": "IPIfNonMatch"
        },
        "dns": {
            "clientIp": "115.239.211.92",
            "servers": [
                "223.5.5.5",
                "114.114.114.114",
                {
                    "address": "8.8.8.8",
                    "port": 53,
                    "domains": [
                        "fbcdn",
                        "facebook",
                        "domain:fb.com",
                        "instagram",
                        "whatsapp",
                        "akamai",
                        "domain:line-scdn.net",
                        "domain:line.me",
                        "domain:naver.jp",
                        "domain:googlevideo.com"
                    ]
                },
                "8.8.4.4"
            ],
            "hosts": {
                "localhost": "127.0.0.1",
                "www.localnetwork.uop": "127.0.0.1"
            }
        },
        "policy": {
            "levels": {
                "0": {
                    "uplinkOnly": 0,
                    "handshake": 4,
                    "connIdle": 15,
                    "downlinkOnly": 0
                },
                "2018": {
                    "uplinkOnly": 0,
                    "handshake": 4,
                    "connIdle": 15,
                    "downlinkOnly": 0
                }
            }
        },
        "inbounds": [
            {
                "settings": {
                    "udp": true,
                    "allowTransparent": true
                },
                "listen": "127.0.0.1",
                "streamSettings": {},
                "protocol": "http",
                "port": 1080,
                "sniffing": {
                    "enabled": true,
                    "destOverride": [
                        "http",
                        "tls"
                    ]
                }
            }
        ]
    },
    "msg": "Succeed",
    "name": "long",
    "status": 0
    }
