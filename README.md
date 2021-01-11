# 概述
一个简单的基金推送工具，可推送到企业微信和Telegram的基金机器人

## 数据来源
数据采用**天天基金网**曲线图片数据，仅发送图片到机器人，由机器人发送到聊天群组中。

## 项目包结构
```
---bots
 |-- telebot        telegram 发送图片方式（WebHook）
 |-- wxbot          企业微信发送图片方式  （webhook）
---dao
 |-- fund           基金的基类，实现了获取图片的功能
 |-- user           用户的基类，存储用户的信息
---service
 |-- bot_service    实现了一些机器人接口，方便调用
---templates
 |-- home.html      前端页面
---data
 |-- my_fund.db     sqlite3 数据库位置，可挂载出去
app.py              项目入口
db_util.py          数据库操作通用类
scheduler.py        定时器模块【待完成】
db.sql              数据库结构，项目启动时会根据这个文件创建数据库
```

# 数据库设计
## 实体
1. 用户
   1. 用户id
   2. 用户名称
2. 机器人
   1. 机器人id（直接使用给定的即可）
   2. 聊天id
3. 基金
   1. 基金id（一定相同）

## 字段
1. 用户表
   1. 用户id
   2. 用户名称
   3. 使用？
   4. 机器人id
   5. 聊天id
2. 基金表
   1. 基金id（主键）
   2. 用户id

# TODO
## 后端
- [ ] 打印日志
- [ ] 测试并部署，发布
- [ ] 加入定时器功能
- [ ] 加入某些接口
  - [ ] `/fund/<id>`
  - [ ] `/fund/<id>?sendTo=<username>`
  - [ ] `/fund/<id>?sendTo=<userid>`

## 前端
- [ ] 设计页面展示
