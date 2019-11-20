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
	    "region": "xxx"  //server name: "long" . "short" . "other"
    }
   ### GET   "/refresh/token"
   ###### with token in headers
    mt: token
