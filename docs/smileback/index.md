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
        "list": [
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
| page      | 否| int  |  当前页 |  |


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
        "users": {
            "pageSize": 10,
            "currentPage": 1,
            "list": [
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
        "counter": {
            "onlineCount": 0,
            "noteCount": null,
            "signinCount": 0
        },
        "users": {
            "pageSize": 10,
            "currentPage": 1,
            "list": [
                {
                    "avatar": "https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83erjrlX6c0rOZPcmMiax9g9mLHPUdvpBDbjpIZp9icRxoDtAzsYqjfJu3QwgGgibpdC0icxg4Mur3cmWAw/132",
                    "uid": 11445,
                    "likeStatus": null,
                    "times": 2  //打卡次数
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
                "delete": false
            }
        ],
        "end": true
    }
}

```






















