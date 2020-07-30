# 封面接口相关文档

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



#### 1.0 设置封面

##### 接口说明

添加留言信息

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/cover/set |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  | 房间号 |   |
| imageUrl      | 是| string  | 图片|   |

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


#### 1.1 引用封面

##### 接口说明

引用封面

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/cover/ref |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  | 房间号 |   |
| id      | 是|  | | xxx  |

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



#### 1.2 封面广场

##### 接口说明

封面广场

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/cover/list |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| roomId      | 是| string  | 房间号 |   |
| page      | 否| int  | 分页|   |
| limit      | 否| int  | 单页条数|   |

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "pageSize": 10,
        "total": 8,
        "currentPage": 1,
        "list": [
            {
                "uid": 11443,  //用户ID
                "avatar": "/x/yz", //头像
                "id": 2, //ID
                "roomId": "B0FFJCVONP", //房间ID
                "imageUrl": "/aaaa", //图像
                "refCount": 4 //引用人数
            }
        ],
        "end": true,
        "empty": false
    }
}

```




























