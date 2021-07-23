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



#### 1.8 收藏

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/my/favourite/list |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| page      | 否| int  |   |   分页 默认第一页  |
| limit      | 否| int  |   |   限制条数  |


#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "pageSize": 1,
        "total": null,
        "currentPage": 1,
        "list": [  //我收藏的空间分页查询
            {
                "id": "SThggtVyGGYySVB",
                "images": [
                    "FpieKiGGnBaC61StMWSMKLflN3YQ.jpg"
                ],
                "name": "音乐和社交的碰撞",
                "longitude": null,
                "latitude": null,
                "distance": null,
                "userCount": 51,
                "allowEntry": false,
                "roomType": 6,
                "typeCode": null,
                "hasGroup": false,
                "groupCount": 0,
                "showStore": false,
                "ext": null,
                "logo": null,
                "parent": null,
                "level": 4,
                "onlineCount": 17,
                "bossUid": 11552,
                "creatorUid": 11552,
                "chainStore": false,
                "seq": null,
                "talk": null,
                "talkStatus": null,
                "privacy": false,
                "unRead":false, //是否已读
                "userList": [
                    {
                        "uid": 11454,
                        "name": "用户xnEFY",
                        "avatar": "FonAFb_WlcDtbQFinDuh3QaGrqd0.jpeg",
                        "certStatus": 1,
                        "level": 1
                    },
                    {
                        "uid": 11455,
                        "name": "用户VGQom",
                        "avatar": "FmevEt6RtAtjKSzVy7P2a-O3IFfU.jpg",
                        "certStatus": null,
                        "level": 1
                    },
                    {
                        "uid": 11468,
                        "name": "用户IPrqe",
                        "avatar": "FkpEdl5YiM7vkblsCYNwg6eTq1oB.jpg",
                        "certStatus": null,
                        "level": 1
                    },
                    {
                        "uid": 11552,
                        "name": "用户eGUNI",
                        "avatar": "Fk2xCK40yl1MatKBYVgwvkO-vltQ.jpg",
                        "certStatus": null,
                        "level": 1
                    },
                    {
                        "uid": 12193,
                        "name": "用户nnNaY",
                        "avatar": "FjTF7mzQPIEqj3x4kH89y0nUXcdH.jpg",
                        "certStatus": null,
                        "level": 1
                    },
                    {
                        "uid": 12244,
                        "name": "用户BhHDO",
                        "avatar": "FlXRpGu3buxg4UXYP08hxPaNCERy.jpg",
                        "certStatus": null,
                        "level": 1
                    }
                ]
            }
        ],
        "end": false,
        "myRoomList": [ //我创建的空间，只有第一页有
            {
                "id": "B0FFIKDKS5",
                "images": [
                    "http://resources.kinstalk.com/gfetifkkhop3zbdfhmo9.jpg"
                ],
                "name": "山西刀削面",
                "longitude": 116.481368,
                "latitude": 39.995825,
                "distance": null,
                "userCount": 1,
                "allowEntry": true,
                "roomType": 0,
                "typeCode": "050300",
                "hasGroup": false,
                "groupCount": 0,
                "showStore": false,
                "ext": null,
                "logo": null,
                "parent": [],
                "level": 0,
                "onlineCount": 1,
                "bossUid": 11478,
                "creatorUid": null,
                "chainStore": false,
                "seq": null,
                "talk": null,
                "talkStatus": null,
                "privacy": false,
                "userList": [
                    {
                        "uid": 11478,
                        "name": "用户skdEn",
                        "avatar": "FqsHvZCJcN5XPwHmiuKqia2z6YJD.jpg",
                        "certStatus": null,
                        "level": 1
                    }
                ],
                "checked": false
             }        
           ],
        "more":false,//是否展示更多  
        "empty": false,
        "startIndex": 0,
        "totalPage": null
    }
}

```






#### 1.9 根据空间ID列表查询空间信息

##### 接口说明

根据空间ID列表查询空间信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/my/room/list |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| int数组  |  空间ID  |  example: /a?id=1&id=2&id=3    |


#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": [  
            {
                "id": "SThggtVyGGYySVB",
                "images": [
                    "FpieKiGGnBaC61StMWSMKLflN3YQ.jpg"
                ],
                "name": "音乐和社交的碰撞",
                "longitude": null,
                "latitude": null,
                "distance": null,
                "userCount": 51,
                "allowEntry": false,
                "roomType": 6,
                "typeCode": null,
                "hasGroup": false,
                "groupCount": 0,
                "showStore": false,
                "ext": null,
                "logo": null,
                "parent": null,
                "level": 4,
                "onlineCount": 17,
                "bossUid": 11552,
                "creatorUid": 11552,
                "chainStore": false,
                "seq": null,
                "talk": null,
                "talkStatus": null,
                "privacy": false,
                "unRead":false, //是否已读
                "userList": [
                    {
                        "uid": 11454,
                        "name": "用户xnEFY",
                        "avatar": "FonAFb_WlcDtbQFinDuh3QaGrqd0.jpeg",
                        "certStatus": 1,
                        "level": 1
                    },
                    {
                        "uid": 11455,
                        "name": "用户VGQom",
                        "avatar": "FmevEt6RtAtjKSzVy7P2a-O3IFfU.jpg",
                        "certStatus": null,
                        "level": 1
                    },
                    {
                        "uid": 11468,
                        "name": "用户IPrqe",
                        "avatar": "FkpEdl5YiM7vkblsCYNwg6eTq1oB.jpg",
                        "certStatus": null,
                        "level": 1
                    },
                    {
                        "uid": 11552,
                        "name": "用户eGUNI",
                        "avatar": "Fk2xCK40yl1MatKBYVgwvkO-vltQ.jpg",
                        "certStatus": null,
                        "level": 1
                    },
                    {
                        "uid": 12193,
                        "name": "用户nnNaY",
                        "avatar": "FjTF7mzQPIEqj3x4kH89y0nUXcdH.jpg",
                        "certStatus": null,
                        "level": 1
                    },
                    {
                        "uid": 12244,
                        "name": "用户BhHDO",
                        "avatar": "FlXRpGu3buxg4UXYP08hxPaNCERy.jpg",
                        "certStatus": null,
                        "level": 1
                    }
                ]
            }
        ]
}

```




























