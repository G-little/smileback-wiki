# 喜欢接口文档

[TOC]
## 修订记录
----
日期 | 作者 | 修订类型 | 修订内容 | 版本|
---- | ---- | ---- | ---- | ---- |
2020年07月03日|冷立纲|A|新增设计方案|1.0|

> 【修订类型：A-新增  M-修改 D-删除】

## 背景



## 产品说明



## 关键流程说明

## 接口说明



#### 1.0 喜欢用户

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/room_user/like |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| longtitude      | 是| double  |  经度 |  最多小数点后6位  |
| latitude      | 是| double  |  纬度 |   |
| roomId      | 是| string  |  空间ID |  |
| toUid      | 是| string  |  对方用户ID |  |

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "likeStatus": 1,  //喜欢状态 1 单向喜欢 2 好友
        "user": {  //用户信息
            "avatar": "https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83erjrlX6c0rOZPcmMiax9g9mLHPUdvpBDbjpIZp9icRxoDtAzsYqjfJu3QwgGgibpdC0icxg4Mur3cmWAw/132",
            "uid": 11445,
            "likeStatus": 1
        }
    }
}

```




























