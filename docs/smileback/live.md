# 对讲相关接口

[TOC]
## 修订记录
----
日期 | 作者 | 修订类型 | 修订内容 | 版本|
---- | ---- | ---- | ---- | ---- |
2020年12月21日|冷立纲|A|新增设计方案|1.0|

> 【修订类型：A-新增  M-修改 D-删除】

## 背景

对讲相关接口

## 产品说明



## 关键流程说明

## 接口说明


#### 1.0 申请对讲权限

##### 接口说明

用户收货地址列表

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /live/apply |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
|  roomId      | 是|  string  |  空间ID | |

#####  错误说明


#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": {
        "status": 0,  // 0 空闲 1 直播中
        "type": "VIDEO", // "VIDEO"  / "VOICE"
        "currentUser": 11632,  //直播用户
        "playUrl": "rtmp://liveplay.faceface2.com/live/null", //播放地址
        "pushUrl": "rtmp://livepush.faceface2.com?", //推送地址
        "pushEndTime": "2020-12-21 17:57:14", //推流截止时间
        "maxPushSeconds": 60  //最长推流时长(秒)
    }
}    

```



#### 1.1 直播对讲开始

##### 接口说明

开始对讲，直播信息广播给群组用户

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /live/start |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
|  roomId      | 是|  string  |  空间ID | |

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

#### 1.2 停止直播对讲

##### 接口说明

添加收货地址

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /live/end |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
|  roomId      | 是|  string  |  空间ID | |

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



#### 1.3 直播对讲详情

##### 接口说明

添加收货地址

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /live/get |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
|  roomId      | 是|  string  |  空间ID | |

#####  错误说明


#####  返回实例
```json
    
  {
    "c": 0,
    "m": null,
    "d": {
        "status": 0,  // 0 空闲 1 直播中
        "type": "VIDEO", // "VIDEO"  / "VOICE"
        "currentUser": 11632,  //直播用户
        "playUrl": "rtmp://liveplay.faceface2.com/live/null", //播放地址
    }
}    

```









