# 我的接口文档

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



#### 1.0 我的主页

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/my/index |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| page      | 否| int  | 页码|   |
| limit      | 否| int  | 单页条数|   |
| longtitude      | 否| double  | 经度|   |
| latitude      | 否| double  | 维度|   |
| roomType      | 否| int  | 房间类型  4 小组|   |

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "hasStore":false, //是否有小店
        "userRoleList": [
            {
                "id": "B0FFJIYRS9",
                "inviteCode": "http://faceface2.com/invite/B0FFJIYRS9/11644",
                "name": "鹿角巷THEALLEY(望京soho店)(暂停营业)"
            }
        ],
        "user": {
            "avatar": "https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83erjrlX6c0rOZPcmMiax9g9mLHPUdvpBDbjpIZp9icRxoDtAzsYqjfJu3QwgGgibpdC0icxg4Mur3cmWAw/132",
            "uid": 11445,
            "avatarStatus":1, // 0 待审核  1 通过  -1 驳回
        },
        "roomHistoys": {
            "pageSize": 10,
            "currentPage": 1,
            "list": [
                {
                    "id": "B0FFLIND01",
                    "images": [
                        "http://store.is.autonavi.com/showpic/746c517bb8827721dbdd0a10fffe47a8",
                        "http://store.is.autonavi.com/showpic/273a9d8df5bf4d6361c0ab7d078e6647",
                        "http://store.is.autonavi.com/showpic/07de48c96a09c2f34b601036e848e6f9"
                    ],
                    "name": "鲜粮卷饼王",
                    "groupName": "小组名",
                    "longitude": 116.473344,
                    "latitude": 39.992997,
                    "times": 1
                    "auditStatus":0,  //审核状态 1 通过 0 待审核  -1 驳回
                    "onlineCount":1 //在线人数
                }
            ],
            "end": true,
            "empty": false
        }
    }
}

```


#### 1.1 我去过的空间详情

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/my/room/detail |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| page      | 否| int  | 页码|   |
| limit      | 否| int  | 单页条数|   |
| id      | 是| string  | 空间ID|   |
| type      | 否| int  |  查询类型 | 0 所有留言  1我发布的   |

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "name": "鲜粮卷饼王",
        "counter": {
            "myNoteCount": 2,  //我的留言
            "noteCount": 3 //总留言
        },
        "notes": {
            "pageSize": 500,
            "currentPage": 1,
            "list": [
               
                {
                    "avatar": "/x/y/z",  //头像
                    "uid": 11443, //用户
                    "id": 2, //留言ID
                    "roomId": "B0FFLIND01", //空间ID
                    "note": "test", //描述
                    "addTime": 1594198044901,
                    "commentsCount": 10 //总留言数
                }
            ],
            "end": true,
            "empty": false
        }
    }
}
```



#### 1.2 移除空间详情

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/my/history/remove |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  |   |  房间ID  |

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
       
    }
}
```

#### 1.3 获取支付宝授权URL

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/pay/ALIPAYCASH/auth_url |

#####  输入参数

无

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
       "url":"http:/xxxx"
    }
}
```


#### 1.4 绑定支付宝

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/pay/ALIPAYCASH/bind_account |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| authCode      | 是| string  |   |  支付宝授权码  |

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
       
    }
}
```



#### 1.5 我的钱包

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/my/wallet |

#####  输入参数

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "money":200.00,
        "drawMoney":12, //可取现金额
        "bindAccount":"xxxxx", //绑定账户
        "bindStatus":0, //绑定状态 0 未绑定  1已绑定
    }
}
```


#### 1.6 我的交易记录

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/my/transactions |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| limit      | 否| int  |   |  单页条数  |
| last      | 否| int  |   |  最后拉取时间戳  |


#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "limit": 20,
        "last": 1597366552441,
        "list": [
            {
                "money":2, //交易金额
                "tranNum":"xxxx", //交易流水
                "accountId":"xxxx", //交易账户
                "type":1, //交易类型 1入账 2出账
                "comment":"描述", //描述
                "createTime":1234567, //创建时间  毫秒
                
            },
        ],
        "end": true
    }
}
```



#### 1.7 提现

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/my/withdraw |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| money      | 否| double  |   |   提现金额  |


#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "money":200.00,
        "drawMoney":12, //可取现金额
        "bindAccount":"xxxxx", //绑定账户
        "bindStatus":0, //绑定状态 0 未绑定  1已绑定
    }
}

```




























