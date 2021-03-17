# 了解redis

## 大概

- remote dictionary server【远程字典服务器】（http通信）
  - tcp/ip http
  - dict - map - object - data
  - server
- 基于
  - 基于网络
  - 基于字典（内存）
- 是啥
  - in-memory database
  - key-value database
  - dictionary database
  - cache server


## 场景

- 商品秒杀活动【100个商品】（参考淘宝秒杀活动，一卡一卡然后就没了）
  - 前十个商品现在秒杀【访问量剧增】
  - cache【前十个】+mysql【后九十个】
- 热点排行【正常新闻搜索】（参考百度热榜）
  - 前十个热点新闻【访问量剧增】
  - cache【前十个】+mysql【后九十个】

## 官网介绍

> https://redis.io/

Redis is an open source (BSD licensed), in-memory data structure store, used as a **database**, cache, and **message broker**. 

