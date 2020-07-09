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

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
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
                    "longitude": 116.473344,
                    "latitude": 39.992997,
                    "times": 1
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




























