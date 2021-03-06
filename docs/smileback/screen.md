# 共享屏幕接口文档

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



#### 1.0 共享屏幕列表信息

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/room/screen/list |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  |  房间ID|   |

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": [
        {
            "type":2 ,// 1 留言 2: h5 banner
            "screenId":1 ,//屏幕ID
            "id":"123",//广告ID
            "roomId":"123",//房间ID
            "title":"123",//标题
            "imageUrl":"/a",//广告图连接
            "link":"/a",//h5跳转链接
            "comment":"/a",//描述
        },{
            "type":1 ,//留言
            "screenId":1 ,//屏幕ID
            
            "uid": 11632,
            "name": null,
            "avatar": null,
            "certStatus": null,
            "level": 1,
            "id": 1292,
            "roomId": "bBSmnwFeDuvLtlt",
            "note": "test",
            "color": null,
            "addTime": 1620886397544,
            "commentsCount": 0,
            "noteType": 0,
            "imageUrl": "test",
            "tags": null,
            "userRole": 1,
            "auditStatus": 0,
            "thumbCount": 0,
            "thumbStatus": false,
            "hint": false,
            "topTime": null,
            "times": 0,
            "videoUrl": null,
            "goodsIds": null,
            "noteSize": null,
            "creator": true
        }
    ]
}

```





#### 1.1 批量添加共享屏幕

##### 接口说明



##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room/screen/add |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是 | stirng  |  房间ID |   |
| noteIds      | 否| int[]  |  留言ID |   |

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



#### 1.2 批量添加共享屏幕

##### 接口说明



##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room/screen/add |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是 | stirng  |  房间ID |   |
| noteIds      | 否| int[]  |  留言ID |   |

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




#### 1.2 批量添加共享屏幕

##### 接口说明



##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room/screen/add |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是 | stirng  |  房间ID |   |
| noteIds      | 否| int[]  |  留言ID |   |

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


#### 1.2 取消显示

##### 接口说明



##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room/screen/del |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是 | stirng  |  房间ID |   |
| noteId      | 是 |  int  |  留言ID |   |

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


#### 1.3 排序加删除

##### 接口说明



##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/room/screen/edit |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是 | stirng  |  房间ID |   |
| ids      | 是 |  int[]  |  排序删除后ID列表 |   |

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

































