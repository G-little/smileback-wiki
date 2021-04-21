# 首页接口文档

[TOC]
## 修订记录
----
日期 | 作者 | 修订类型 | 修订内容 | 版本|
---- | ---- | ---- | ---- | ---- |
2020年07月03日|冷立纲|A|新增设计方案|1.0|

> 【修订类型：A-新增  M-修改 D-删除】

## 背景

获取就近空间数据

## 产品说明



## 关键流程说明

## 接口说明



#### 1.0 获取就近空间数据

##### 接口说明

获取就近空间数据

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room/index |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| longtitude      | 是| double  |  经度 |  最多小数点后6位  |
| latitude      | 是| double  |  纬度 |   |
| keywords      | 否| string  |  关键词 |  |
| limit      | 否| int  |  单页条数 |  |
| page      | 否| int  |  当前页 |  |


#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "pageSize": 10,
        "currentPage": 1,
        "list": [{  //寻找同乡
                "id": null,
                "images": null,
                "name": "寻找同乡",
                "longitude": null,
                "latitude": null,
                "distance": "0",
                "userCount": null,
                "allowEntry": true,
                "roomType": 7,  //空间类型
                "typeCode": null,
                "hasGroup": false,
                "groupCount": null,
                "showStore": false,
                "ext": {
                    "status": -1  //没有同乡群的情况
                },
                "logo": null,
                "parent": null,
                "level": 0,
                "onlineCount": null,
                "bossUid": null,
                "creatorUid": null
            },
            {
                "id": "B0FFLIND01",  //ID
                "images": [  //图片
                    "http://store.is.autonavi.com/showpic/746c517bb8827721dbdd0a10fffe47a8",
                    "http://store.is.autonavi.com/showpic/273a9d8df5bf4d6361c0ab7d078e6647",
                    "http://store.is.autonavi.com/showpic/07de48c96a09c2f34b601036e848e6f9"
                ],
                "name": "鲜粮卷饼王",  // 名称
                "distance": "15", //距离 米
                "userCount": 0 //用户数
                "roomType":1, // 0 普通 1 城市空间 2 商圈
                "hasGroup":false, //是否有小组
                "groupCount":0, //小组计数
                "onlineCount":22,// 在线人数
                "level":1 ,//空间等级
                "chainStore": true // 是否连锁空间
                "seq":"001",//空间序号
                "ext": {  //附加信息
                    "id": "01020200810001", //id
                    "parentId": "010", //父节点
                    "addTime": "2020-08-11 14:53:42", //添加时间
                    "num": 1, //序号
                    "startTime": 1597136400000, //开始时间
                    "endTime": 1597136400000, //结束时间
                    "bgUrl": "/xxxx", //北京
                    "fontType": 1, //字体
                    "name": "POP PARTY 001", //名字
                    "deleted": false, //删除状态
                    "remainMillisSeconds": 7577269 //剩余时间(毫秒）
                }
            }
        ],
        "end": false,
        "hotKeywords": null,
        "address": null,
        "likeYouCount": null,
        "empty": false
    }
}

```



#### 1.0.1 空间详情

##### 接口说明

获取空间详情数据

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/room/get |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| string  |  空间ID |    |



#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "id": "010",
        "images": [
            "http://resources.kinstalk.com/k1d59pugbdfp0mc0i6tf.png"
        ],
        "name": "北京市PARTY 001",
        "longitude": null,
        "latitude": null,
        "distance": null,
        "userCount": 8,
        "allowEntry": false,
        "roomType": 1,
        "ext": {
            "id": "POP01020200827001",
            "parentId": "010",
            "addTime": "2020-08-27 10:53:59",
            "num": 1,
            "startTime": 1598432400000,
            "endTime": 1598518800000,
            "bgUrl": "http://resources.kinstalk.com/jri94gif8o92zkc85189.jpg",
            "fontType": 2,
            "name": "PARTY 001",
            "deleted": false,
            "userCount": null,
            "remainMillisSeconds": 21960298
        }
    }
}

```


#### 1.1 签到

##### 接口说明

签到

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/room_user/signin |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| string  | 空间ID |   |
| longtitude      | 是| double  |  经度 |  最多小数点后6位  |
| latitude      | 是| double  |  纬度 |   |

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "counter": {
            "onlineCount": 0,  //在线人数
            "noteCount": null, //留言条数
            "signinCount": 0 //来过人数
        },
        "users": {  //用户分页
            "pageSize": 10,  //单页条数 
            "currentPage": 1, //当前分页
            "list": [
                {
                    "avatar": "/x/y/z",  //头像
                    "uid": 11443, //用户
                    "likeStatus": null //喜欢状态
                },
                {
                    "avatar": "https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83erjrlX6c0rOZPcmMiax9g9mLHPUdvpBDbjpIZp9icRxoDtAzsYqjfJu3QwgGgibpdC0icxg4Mur3cmWAw/132",
                    "uid": 11445,
                    "likeStatus": null
                },
                {
                    "avatar": "https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83errQTDLFchBwAtga1R9kSRvIicUqjtIcczJNSEdSKrt7quEpITyxNo2Yrxaf8CyfFdtVTNI7OtxRag/132",
                    "uid": 11447,
                    "likeStatus": null
                }
            ],
            "end": true,
            "empty": false
        }
    }
}
```




#### 1.2 离开

##### 接口说明

签到

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/room_user/leave |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| string  | 空间ID |   |

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



#### 1.3 分页获空间详情数据

##### 接口说明

签到

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/room/detail |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| string  | 空间ID |   |
| type      | 否 |  int  |  请求类型  |  1:在线，2:留言，3:来过  |
| limit      | 否| int  |  单页条数 |  |
| page      | 否| int  |  当前页 |  |
| role      | 否| int  |  角色 | 5 管理员  |


#####  错误说明




#####  返回实例

__喜欢状态说明__

0:无  1:喜欢 2:好友

__在线类型(1)__

```json

{
    "c": 0,
    "m": null,
    "d": {
        "counter": {
            "onlineCount": 0,  //在线人数
            "noteCount": null, //留言数
            "signinCount": 0 // 签到数
        },
        "unReadCounter": { //未读数
            "noteCount": 0, // 新增留言
            "userCount": 0 //新增签到
        },
        "bossStatus":-1 , //-1 无  0 待领取 1 已有Boss
        "bossUid":123,// boss ID
        "users": {
            "pageSize": 10,
            "currentPage": 1,
            "list": [
                {
                    "avatar": "https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83erjrlX6c0rOZPcmMiax9g9mLHPUdvpBDbjpIZp9icRxoDtAzsYqjfJu3QwgGgibpdC0icxg4Mur3cmWAw/132",
                    "uid": 11445,
                    "likeStatus": null
                    "hint":false, //是否有暗号
                },
                {
                    "avatar": "https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83errQTDLFchBwAtga1R9kSRvIicUqjtIcczJNSEdSKrt7quEpITyxNo2Yrxaf8CyfFdtVTNI7OtxRag/132",
                    "uid": 11447,
                    "likeStatus": null
                }
            ],
            "end": true,
            "empty": false
        }
    }
}

```

__留言类型(2)__


```json

{
    "c": 0,
    "m": null,
    "d": {
        "counter": {
            "onlineCount": 0,
            "noteCount": null,
            "signinCount": 0
        },
        "bossStatus":-1 , //-1 无  0 待领取 1 已有Boss
        "bossUid":123,// boss ID
        "notes": {
            "pageSize": 500,
            "currentPage": 1,
            "list": [
                {
                    "avatar": null,  //头像
                    "uid": null, //用户
                    "id": 1, //id
                    "roomId": "B0FFLIND01", //房间号
                    "note": "test", //内容
                    "color": "#fffff",  //颜色
                    "addTime": 1594196130758, //添加时间
                    "commentsCount": 0, //计数
                    "auditStatus":0, //0 待审核 1 审核通过 -1 驳回
                    "thumbCount": 222, //点赞数
                    "tags": [ //标签
                        {
                            "content": "test",
                            "color": "default",
                            "fontSize": 12,
                            "rotateAngel": 0.0,
                            "top": "50%",
                            "left": "50%"
                        }
                    ]
                }
            ],
            "end": true,
            "empty": false
        }
    }
}

```

__签到类型(3)__

```json

{
    "c": 0,
    "m": null,
    "d": {
        "qrCode":"http://xxxxxxx",
        "counter": {
            "onlineCount": 0,
            "noteCount": null,
            "signinCount": 0
        },
        "bossStatus":-1 , //-1 无  0 待领取 1 已有Boss
        "bossUid":123,// boss ID
        "users": {
            "pageSize": 10,
            "currentPage": 1,
            "list": [
                {
                    "avatar": "https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83erjrlX6c0rOZPcmMiax9g9mLHPUdvpBDbjpIZp9icRxoDtAzsYqjfJu3QwgGgibpdC0icxg4Mur3cmWAw/132",
                    "uid": 11445,
                    "likeStatus": null,
                    "times": 2,  //打卡次数
                    "hint":false, //是否有暗号
                },
                {
                    "avatar": "https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83eqDw87BjTffT03d4T5z9ynn6bia79vWUdDzXbvvCrhbL5oBAYIOTe6iaH790uto7CTkH71oDEpzuMjQ/132",
                    "uid": 11446,
                    "likeStatus": null,
                    "times": 1
                },
                {
                    "avatar": "https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83errQTDLFchBwAtga1R9kSRvIicUqjtIcczJNSEdSKrt7quEpITyxNo2Yrxaf8CyfFdtVTNI7OtxRag/132",
                    "uid": 11447,
                    "likeStatus": null,
                    "times": 1
                },
                {
                    "avatar": "/x/y/z",
                    "uid": 11443,
                    "likeStatus": null,
                    "times": 1
                }
            ],
            "end": true,
            "empty": false
        }
    }
}

```




#### 1.4 用户详细信息

##### 接口说明

签到

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/room_user/detail |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| uid      | 是| int  | 用户ID |   |
| roomId      | 是| string  | 空间ID |   |
| limit      | 否| int  |  单页条数 |  |
| page      | 否| int  |  当前页 |  |


#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "name": "鲜粮卷饼王",  //名称
        "imAdmin":true, //我是否是admin ？
        "userRole":0, //用户角色  0:普通 1:boss 2:员工
        "user": {
            "avatar": "/x/y/z",  //头像
            "uid": 11443, //用户ID
            "likeStatus": 0  //喜欢状态
        },
        "hint":false, //是否有暗号
        "rooms":{
                "pageSize": 10,
                "total": null,
                "currentPage": 1,
                "list": [
                    {
                        "id": "XgJMUNdlTaxKbfU",
                        "images": [
                            "Fr7_9xj8GEX1_ljebvMPK9-NBQr6.jpg"
                        ],
                        "name": "民谣在路上",
                        "longitude": null,
                        "latitude": null,
                        "distance": null,
                        "userCount": 26,
                        "allowEntry": false,
                        "roomType": 6,
                        "typeCode": null,
                        "hasGroup": false,
                        "groupCount": 0,
                        "showStore": false,
                        "ext": null,
                        "logo": null,
                        "parent": null,
                        "level": 5,
                        "onlineCount": 16,
                        "bossUid": 14853,
                        "creatorUid": 14853,
                        "chainStore": false,
                        "seq": null,
                        "talk": null
                    }
                ],
                "end": true,
                "empty": false,
                "startIndex": 0,
                "totalPage": null
            },
        "notes": { //留言数据
            "pageSize": 500,
            "currentPage": 1,
            "list": [
                {
                    "avatar": "/x/y/z",
                    "uid": 11443,
                    "id": 2,
                    "roomId": "B0FFLIND01",
                    "note": "test",
                    "addTime": 1594198044901,
                    "commentsCount": 10
                },
                {
                    "avatar": "/x/y/z",
                    "uid": 11443,
                    "id": 3,
                    "roomId": "B0FFLIND01",
                    "note": "test",
                    "addTime": 1594198416707,
                    "commentsCount": 0
                }
            ],
            "end": true,
            "empty": false
        }
    }
}

```


#### 1.4.1  设置用户角色

##### 接口说明

签到

##### 请求说明

| http 请求方式          | post             |
|:------------- |:---------------:|
| url      |/room_user/set_role |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  | 空间ID |   |
| uid      | 是| int[]  | 用户ID array |   |
| role      | 是| int  |  用户角色 |  0:普通用户 1:boss 2:员工   |
| inviteMoney      | 否| double  |  奖励金额 |  奖励金额 |



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


#### 1.4.2  移除角色

##### 接口说明

签到

##### 请求说明

| http 请求方式          | post             |
|:------------- |:---------------:|
| url      |/room_user/remove_role |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  | 空间ID |   |
| uid      | 是| int[]  | 用户 array |   |



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


#### 1.4.3  添加主页房间

##### 接口说明

添加主页房间

##### 请求说明

| http 请求方式          | post             |
|:------------- |:---------------:|
| url      |/room_user/add_room |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomList      | 是| string[]  | 房间 array |   |



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


#### 1.4.2  分页获取主页房间

##### 接口说明

添加主页房间

##### 请求说明

| http 请求方式          | get             |
|:------------- |:---------------:|
| url      |/room_user/index_room_list |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| page      | 否 |  int  |  分页 |   |
| limit      | 否 |  int  |  条数 |   |



#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "pageSize": 10,
        "total": null,
        "currentPage": 1,
        "list": [
            {
                "id": "XgJMUNdlTaxKbfU",
                "images": [
                    "Fr7_9xj8GEX1_ljebvMPK9-NBQr6.jpg"
                ],
                "name": "民谣在路上",
                "longitude": null,
                "latitude": null,
                "distance": null,
                "userCount": 26,
                "allowEntry": false,
                "roomType": 6,
                "typeCode": null,
                "hasGroup": false,
                "groupCount": 0,
                "showStore": false,
                "ext": null,
                "logo": null,
                "parent": null,
                "level": 5,
                "onlineCount": 16,
                "bossUid": 14853,
                "creatorUid": 14853,
                "chainStore": false,
                "seq": null,
                "talk": null
            }
        ],
        "end": true,
        "empty": false,
        "startIndex": 0,
        "totalPage": null
    }
}
```


#### 1.4.3  删除主页

##### 接口说明

添加主页房间

##### 请求说明

| http 请求方式          | post             |
|:------------- |:---------------:|
| url      |/room_user/del_room |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 否 |  stirng  |  房间ID |   |



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








#### 1.5 弹幕

##### 接口说明

签到

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/danmuku/send |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  | 空间ID |   |
| content      | 是| string  | 内容 |   |
| danmuType      | 否| int  | 弹幕类型 |  0 普通 1广告  |
| multiRoom      | 否| boolean  | 是否连锁空间同步 |  默认否  |


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


#### 1.6 弹幕列表

##### 接口说明

签到

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/danmuku/list |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  | 空间ID |   |


#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "limit": 1000,
        "last": 1596105412381,
        "list": [
            {
                "id": 1,
                "roomId": "B0FFJY9UP5",
                "uid": 11635,
                "content": "咯弄",
                "addTime": 1596105412381,
                "danmuType":1, //1 广告 0 普通
                "delete": false,
                "userRole":0, //用户角色  0:普通 1:boss 2:员工
            }
        ],
        "end": true
    }
}

```


#### 1.6 广告弹幕列表

##### 接口说明

签到

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/danmuku/ad/list |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  | 空间ID |   |


#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": [
        {
            "id": 1,
            "roomId": "B0FFJY9UP5",
            "uid": 11635,
            "content": "咯弄",
            "addTime": 1596105412381,
            "danmuType":1, //1 广告 0 普通
            "delete": false,
            "userRole":0, //用户角色  0:普通 1:boss 2:员工
        }
    ]
}

```


#### 1.7 更新弹幕

##### 接口说明

签到

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/danmuku/ad/update |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| int  | 弹幕ID |   |
| content      | 是| string  | 弹幕内容 |   |


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


#### 1.8 删除弹幕

##### 接口说明

签到

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/danmuku/ad/del |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| int  | 弹幕ID |   |


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


#### 1.7 获取邀请CODE（测试用）

##### 接口说明

测试code 获取

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/room/random_code |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| string  | 房间号 |   |
| inviteUser      | 是| int  | 邀请人ID |   |





#####  错误说明




#####  返回实例

```json

    {
    "c": 0,
    "m": null,
    "d": {
        "code": "^AQENXjcUU"
    }


```


#### 1.8 根据Code 获取房间信息

##### 接口说明

签到

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room/code2room |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| code      | 是| string  | 邀请码 |   |


#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "id": "B0FFG72WB4",
        "name": "秀域科技健康(望京街店)",
        "userList": [  //用户列表
            {
                "avatar": "FqTd6VEjTbp4UjkquMmaZF_d9Zzj.jpg",
                "uid": 11491,
                "remark": null,
                "userRole": 0,
                "likeStatus": 0
            }
        ]
    }
}

```



#### 1.9 收藏空间

##### 接口说明

收藏空间

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room/favorite/add |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  | 空间ID |   |


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



#### 1.10 取消收藏空间

##### 接口说明

取消收藏

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room/favorite/remove |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  | 空间ID |   |


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



#### 1.11 设置家乡

##### 接口说明

设置家乡

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room/set_home|

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| code      | 是| string  | 家乡省份code |   |
| longtitude |是 | double  | 经度 |   |
| latitude |是 | double  | 维度 |   |


#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "name": "山东人在110000",
        "groupCount": 0,
        "hasGroup": false,
        "bossStatus": -1,
        "roomType": 7,
        "bossUid": null,
        "showStore": false,
        "storeId": null,
        "level": null,
        "favorite": false,
        "images": [
            "Fjt3oB_msFfsELeYvmb546PQu-zs.jpg"
        ],
        "roomId": "370000in110000",
        "roomNum": 256,
        "inviteUrl": "http://smileback.xiaogang.org.cn/invite/370000in110000/11632",
        "creatorUid": null,
        "counter": {
            "onlineCount": 0,
            "noteCount": 0,
            "signinCount": 0
        },
        "users": {
            "pageSize": 500,
            "total": null,
            "currentPage": 1,
            "list": null,
            "end": true,
            "empty": true,
            "startIndex": 0,
            "totalPage": null
        },
        "firstTime": false
    }
}
```




#### 1.12 陪伴灯

##### 接口说明

设置家乡

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room_user/light|

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  | 房间号 |   |
| light |是 | boolean  | 灯的状态 |   |



#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "lightTime":123434, //点灯开始时间，毫秒值
        "light":true, //灯状态
    }
}
```



#### 1.13 首页提醒

##### 接口说明

首页提醒

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room/remind_list|

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| page |否 |  int  | 分页 |  默认值1  |
| limit |否 |  int  | 分页条数 |  默认值10  |
| latitude |是 |  double  |  |  经度  |
| longtitude |是 |  double  |  |  维度   |



#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "pageSize": 10,
        "total": 2,
        "currentPage": 1,
        "list": [
            {
                "id": "AbekYmJDejcqGHV",
                "images": [
                    "FvKvc62BV_qHf0Zx20SnRkXue8WC.jpg"
                ],
                "roomType": 6,  //空间类型
                "name": "奇幻电影",
                "userCount": 0, //在线人数
                "noteCount": 0 //未读留言
            },
            {
                "id": "B0GRBMF2XV",
                "images": [
                    "http://resources.kinstalk.com/qap1kqa5ez2ohv82s8gb.jpg"
                ],
                "roomType": 0,
                "name": "庭珍牛肉粉",
                "userCount": 0,
                "noteCount": 0
            }
        ],
        "end": true,
        "empty": false,
        "startIndex": 0,
        "totalPage": 1
    }
}

```





#### 1.14 连锁空间列表

##### 接口说明

连锁空间列表，只有baoss 有权限获取

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/room/chain_list|

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| page |否 |  int  | 分页 |  默认值1  |
| limit |否 |  int  | 分页条数 |  默认值10  |
| roomId |是 |  string  | 空间ID | 
 |



#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "pageSize": 10,
        "total": null,
        "currentPage": 1,
        "list": [
            {
                "id": "B0FFI0M9RJ",
                "images": [
                    "http://resources.kinstalk.com/usslqxrmlvrlzu0ujgs9.jpg"
                ],
                "name": "晓寿司(望京soho店)",
                "onlineCount": 6,
                "userCount": 55,
                "level": 0,
                "roomType": 0,
                "showStore": null,
                "chainName": "晓寿司(望京soho店)001",
                "bossUid": 12762,
                "creatorUid": null
            },
            {
                "id": "utTlgufNSVCrPTX",
                "images": [
                    "http://resources.kinstalk.com/usslqxrmlvrlzu0ujgs9.jpg"
                ],
                "name": "晓寿司(望京soho店)",
                "onlineCount": 0,
                "userCount": 1,
                "level": 0,
                "roomType": 0,
                "showStore": false,
                "chainName": "晓寿司(望京soho店)001",
                "bossUid": 12762,
                "creatorUid": null
            }
        ],
        "end": true,
        "empty": false,
        "startIndex": 0,
        "totalPage": null
    }
}

```



#### 1.15 创建空间

##### 接口说明

创建空间

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room/create|

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| coverUrl |是 |  string  | 封面 |  |
| name |是 |  string  | 空间名 |   |
| privacy |是 |  boolean  | 是否隐私空间 | 
| syncIndex |否 |  boolean  | 是否同步首页 | 



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































