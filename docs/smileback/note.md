# 留言接口文档

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



#### 1.0 发送留言

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/note/add |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| longtitude      | 是| double  |  经度 |  最多小数点后6位  |
| latitude      | 是| double  |  纬度 |   |
| roomId      | 是| string  |  空间ID |  |
| note      | 否| string  |  最多70字 |  |
| noteType      | 否| int  |  留言类型 | 0 文本 1 图文  2 视频|
| color      | 否| string  |  随机色值 |  16进制 #fffff  |
| imageUrl      | 否| string  |  图片地址 | |
| videoUrl      | 否| string  |  视频地址 | |
| tags      | 否| string  |  tag 标签json数组 |  参照tag参数说明 |
| multiRoom      | 否| boolean  |  是否同步连锁空间 | 默认值false|
| noteSize      | 否| string  |  尺寸 | 长*宽 |
| showScreen      | 否| boolean  |  是否显示在主屏幕 | 只有房主有权限 默认 false  |


__tags 参数说明__


```json
[{
    "content": "test", //标签内容
    "color": "default", //颜色
    "fontSize": 12, // 字号
    "rotateAngel": 0.0, //旋转角度
    "top": "50%", //距离图片上边百分比
    "left": "50%" //距离图偏左侧百分比
}]
```

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "id":5
    }
}

```


#### 1.1 删除留言

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/note/del |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| int  |  消息ID |  |

#####  错误说明

1. 没有操作权限


#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {

    }
}

```


#### 1.2 评论

##### 接口说明

为留言添加评论信息

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/note/comment |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| comment      | 是| string  |  评论 |  |
| noteId      | 是| int  |  留言ID |  |
| pid      | 是| int  |  父节点ID | 点击回复的留言ID，如果没有写0  |
| tCommentId      | 是| int  | 二级评论的顶级父评论ID |  如果没有写0 |

#####  错误说明

1. 没有操作权限


#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "id": 10 //评论ID
    }
}
```



#### 1.3 删除评论

##### 接口说明

为留言添加评论信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/note/comment/del |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| int  |  评论ID |  |


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



#### 1.3 详情

##### 接口说明

为留言添加评论信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/note/detail |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| noteId      | 是| int  | 留言ID|  |
| commentId      | 是| int  | 评论ID| 若回复某条评论则填写对应值，否则0  |
| page      | 否| int  | 页码|   |
| limit      | 否| int  | 单页条数|   |


#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        
        {
    "c": 0,
    "m": null,
    "d": {
        "note": {
            "avatar": "/x/y/z",   //留言数据
            "uid": 11443,
            "id": 2,
            "roomId": "B0FFLIND01", //空间ID
            "note": "test",
            "color": "#fffff",  //颜色
            "addTime": 1594198044901,
            "commentsCount": 10
        },
        "comments": {  //评论数据
            "pageSize": 10,
            "currentPage": 1,
            "list": [
                {
                    "id": 9,  //评论ID
                    "noteId": 2,  //留言ID
                    "uid": 11443, //用户ID
                    "level": "L2", //层级ID 直接回复留言的为L1，其他L2
                    "pid": 7,  //父ID ，回复某条留言的时候取该留言ID
                    "commentsCount": 0,  //回复数
                    "comment": "test", //回复
                    "addTime": null, //添加时间
                    "toUid": 11443, //回复人
                    "avatar": "/x/y/z", //头像
                    "toAvatar": "/x/y/z", //被回复头像
                    "reply": true, //是否回复
                    "tcommentId": 7 // 留言下L1 评论的ID，
                },
                {
                    "id": 10,
                    "noteId": 2,
                    "uid": 11443,
                    "level": "L2",
                    "pid": 8,
                    "commentCount": null,
                    "comment": "test",
                    "addTime": null,
                    "toUid": 11443,
                    "avatar": "/x/y/z",
                    "toAvatar": null,
                    "reply": false,
                    "tcommentId": 7
                }
            ],
            "end": true,
            "empty": false
        }
    }
}
    }
}
```



#### 1.4 互动状态同步

##### 接口说明

拉取同步互动状态

##### 请求说明

| http 请求方式          | post    |
|:------------- |:---------------:|
| url      |/note/remind/status |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| commentIds      | 是| int[]  | 评论ID| 评论ID数组 |



#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": [
        {
            "commentId": 100, //评论ID
            "commentDelete": false, //评论是否删除
            "pcommentDelete": false, //父评论是否删除
            "tcommentDelete": false, //顶级评论是否删除
            "noteDelete": true, //是否删除
            "remark": null, //备注名
            "roomId": "B0FFM6JAVG", //房间号
            "roomName": null // 房间名
        }
    ]
}

```



#### 1.5 点赞

##### 接口说明

拉取同步互动状态

##### 请求说明

| http 请求方式          | post    |
|:------------- |:---------------:|
| url      |/note/thumb |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| noteId      | 是| int  | 留言ID| |
| value      | 是| boolean  |  点赞值| true:点赞   false: 取消  |



#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "value": true  //当前值
    }
}
```




#### 1.6 置顶

##### 接口说明

置顶

##### 请求说明

| http 请求方式          | post    |
|:------------- |:---------------:|
| url      |/note/top |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| int  | 留言ID| |



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



#### 1.7 取消置顶

##### 接口说明

置顶

##### 请求说明

| http 请求方式          | post    |
|:------------- |:---------------:|
| url      |/note/untop |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| int  | 留言ID| |



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




#### 1.8 分页获取留言数据

##### 接口说明

分页面拉取留言数据

##### 请求说明

| http 请求方式          | get    |
|:------------- |:---------------:|
| url      |/note/list |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是| int  | 空间ID| |
| uid      | 否| int  | 用户ID|  查看某个用户在该空间的留言|
| limit      | 否| int  | 单页条数 |   默认10条|
| page      | 否| int  | 分页数 |    |



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
        "list": [
           {
                "uid": 11454,
                "name": "用户xnEFY",
                "avatar": "FonAFb_WlcDtbQFinDuh3QaGrqd0.jpeg",
                "certStatus": 1,
                "level": 1,
                "id": 183,
                "roomId": "B0FFK5WBZ0",
                "note": "23",
                "color": "DAB8F3",
                "addTime": 1602324668400,
                "commentsCount": 5,
                "noteType": 0,
                "imageUrl": null,
                "tags": null,
                "userRole": 0,
                "auditStatus": 0,
                "thumbCount": 0,
                "thumbStatus": false,
                "hint": false,
                "topTime": null,
                "times": 6,
                "videoUrl": null,
                "goodsIds": null,
                "noteSize": null,
                "showScreen": false,
                "commentList": [ //留言数据
                    {
                        "id": 233,
                        "uid": 12399,
                        "noteId": 183,
                        "name": "用户uCJsc",
                        "commentsCount": 1,
                        "delete": false,
                        "comment": "不"
                    },
                    {
                        "id": 190,
                        "uid": 11454,
                        "noteId": 183,
                        "name": "用户xnEFY",
                        "commentsCount": 2,
                        "delete": false,
                        "comment": "哈哈哈"
                    }
                ],
                "creator": false
            }
        ],
        "end": false,
        "empty": false,
        "startIndex": 0,
        "totalPage": null
    }
}
```




























