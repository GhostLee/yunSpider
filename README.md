百度云爬虫
-----

> 最近在找实习工作,有点无聊,没事搞,研究了下爬百度网盘的用户分享

- 获取用户订阅:
 http://yun.baidu.com/pcloud/friend/getfollowlist?query_uk=%s&limit=24&start=%s&bdstoken=e6f1efec456b92778e70c55ba5d81c3d&channel=chunlei&clienttype=0&web=1&logid=MTQ3NDA3NDg5NzU4NDAuMzQxNDQyMDY2MjA5NDA4NjU=  
    (query_uk limit start是必须参数)
- 获取用户粉丝: 
http://pan.baidu.com/pcloud/friend/getfanslist?query_uk=%s&limit=24&start=%s&bdstoken=null&channel=chunlei&clienttype=0&web=1&logid=MTQ3NDAzNjQwNzg3OTAuNzM1MzMxMDUyMDczMjYxNA==
    (query_uk limit start是必须参数)
- 获取用户分享: 
http://pan.baidu.com/pcloud/feed/getsharelist?t=1474202771918&category=0&auth_type=1&request_location=share_home&start=0&limit=60&query_uk=224534490&channel=chunlei&clienttype=0&web=1&logid=MTQ3NDIwMjc3MTkxOTAuMzA1NjAzMzQ4MTM1MDc0MTc=&bdstoken=e6f1efec456b92778e70c55ba5d81c3d
    (query_uk limit start auth_type是必须参数)

 
> 上面3个连接请求必须带上 `("Referer", "https://yun.baidu.com/share/home?uk=23432432#category/type=0")`,uk多少无所谓,否则请求不到json数据,
获取用户订阅和获取用户粉丝每次请求一次休眠2s的话可以无限制请求,对ip没要求,获取用户分享超坑,一个ip只能请求10次,并且休眠也没用.
因为没有那么多ip,我就去研究手机版的用户分享,手机版获取用户分享可以一次性连续请求60次,60次后必须休眠35s左右在继续请求就可以,不会像pc版那样必须换ip,
但是手机版只能请求网页源码,然后用正则进行匹配.

- 手机版分享:
 http://pan.baidu.com/wap/share/home?uk=2889076181&start=%s&adapt=pc&fr=ftw (uk:**每个百度网盘用户的唯一标示**,start:用户可能有上百上千个分享,必须分页,start默认从0开始,手机版默认分页是20个每页)
 
 
 
## License

yunSpide source code is licensed under the Apache Licence, Version 2.0 (http://www.apache.org/licenses/LICENSE-2.0.html).
