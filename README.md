ReadMe
================
###数据采集遇到IP被封的情况处理：
####1.购买代理IP
####2.购买动态代理IP（同一个代理IP每次访问会动态改变）
####3.远程拨号主机（如VPS）
###原理
---------------
  本实例使用远程VPS虚拟主机重新拨号切换ip，代理端口设置为固定
  VPS主机只作为代理机供应一个代理
  TCP服务端部署于某台服务器（可通过外网访问）
  客户端为VPS主机
  客户端和服务端保持连接，
  当爬虫需要切换IP的时候使用开放的API向服务器上的TCP服务端发起连接并通信
  服务端收到请求之后向VPS主机上的TCP客户端发出消息，通知其切换IP并重新向服务端进行连接
  服务器端收到新的客户端连接并判定为IP供应方之后，保存IP并返回给爬虫程序

