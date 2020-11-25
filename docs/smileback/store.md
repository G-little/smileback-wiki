# 小店相关接口文档

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


## 通用接口



### 店主端

-------

#### 特殊说明

1. 店主端接口均有店主权限校验，需统一设置storeId header 来校验店主对商店的操作权限
2. boss 产品管理接口统一前缀  /mall/admin



#### 1.0 小店列表（无需权限校验）

##### 接口说明

用户/店员 小店列表 ，需根据不同的角色(店员/店主)展示不同的按钮

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/mall/store/list |

#####  输入参数

无

#####  错误说明




#####  返回实例
```json

{
    "c": 0,
    "m": null,
    "d": [
        {
            "id": 1, //商店ID
            "inviteCode": "http://smileback.xiaogang.org.cn/invite/116.470293,39.996171_84/11632",  //邀请码
            "userRole": 1, // 用户角色
            "name": "大头娃", // 商店名称
            "auditStatus":0,  // 0
            "images": [ //商店图片
                "FkbNac6aQOaEVZU6Fam45uand5fv.png"
            ],
            "roomId": null //商店ID
        }
    ]
}
```


#### 1.1 商品

#### 1.1.1 商品管理列表接口

##### 接口说明

店主端商品管理主页

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/mall/admin/goods/list |

#####  Header 头

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| storeId      | 是| int  |  商店ID |   用于店主权限校验 |



#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| showType      | 否 | int  |  显示类型 |  1在售  0 待上架  -1 已下架  |
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
        "total": 1,
        "currentPage": 1,
        "list": [
            {
                "id": 10000000,
                "storeId": 1,
                "goodsSn": "",
                "detail": null, 图片
                "name": "测试",
                "retailPrice": 3.00,  //价格 
                "isOnSale": true, //在售状态
                "number": null, //库存
                "auditStatus": 0, //审核状态
                "saleCount": null //销售量
            }
        ],
        "end": true,
        "summary": {  //计数信息，只有第一页返回
            "onsaleTotal": 0,
            "tosaleTotal": 1,
            "downsaleTotal": 0
        },
        "empty": false,
        "startIndex": 0,
        "totalPage": 1
    }
}

```



#### 1.1.2 添加商品

##### 接口说明

添加商品

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/mall/admin/goods/add |

#####  Header 头

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| storeId      | 是| int  |  商店ID |   用于店主权限校验 |



#####  输入参数(post json)


```json    
{
    "goods":{
        "name":"测试",
        "categoryId":3,
        "retailPrice":100.00
    },
    "specifications":[{
        "specificationId":1,
        "specificationName":"规格",
        "value":"标准"
    }],
    "products":[{
        "price":3.0,
        "number":50,
        "specifications":[{
            "id":1,
            "value":"33"
        }]
    }]

}
    
```

_**goods参数说明**_

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| name      | 是 | string  |  商品名称 | |
| categoryId      | 是| int  |  商品类别 |  |
| freightPrice      | 是| double  |  邮费 |  0 包邮 否则填具体运费 |
| detail      | 是| image 数组  |  图片 | 至少一张，格式参见 image 说明  |
| videos      | 否| Video 数组  |  视频 | 格式参见 Video 说明  |


_**image参数说明**_

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| url      | 是 | string  |  图片地址 | |
| size      | 是| string  |  图片尺寸 | 例如 1024*768  |


_**Video参数说明**_

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| url      | 是 | string  |  视频地址 | |
| cover      | 是 | string  |  封面地址 | |
| size      | 是| string  |  视频尺寸 | 例如 1024*768  |



_**specifications参数说明**_

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| specificationId      | 是 | int  |  规格ID |  透过类别规格获取 |
| specificationName      | 是| string  |  规格名称 | 透过类别规格获取  |
| value      | 是| string  |  规格值 | |



_**products参数说明**_

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| specifications      | 是 | Specification 数组  |   |  参见Specification  格式说明  |
| price      | 是| double  |  价格 |  价格 |
| number      | 是| int  |  库存数量 | |
| url      | 否 | string  |  商品url | |


_**Specification参数说明**_

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是 | int | 规格ID  |  根据规格类别取得  |
| value      | 是| string  |  规格值 |   |

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


#### 1.1.3 修改商品信息

##### 接口说明

添加商品

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/mall/admin/goods/add |

#####  Header 头

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| storeId      | 是| int  |  商店ID |   用于店主权限校验 |



#####  输入参数(post json)


```json    
{
    "goods":{
        "name":"测试",
        "categoryId":3,
        "retailPrice":100.00
    },
    "specifications":[{
        "specificationId":1,
        "specificationName":"规格",
        "value":"标准"
    }],
    "products":[{
        "price":3.0,
        "number":50,
        "specifications":[{
            "id":1,
            "value":"33"
        }]
    }]

}
    
```

_**goods参数说明**_

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是 | int  |  商品ID | |
| name      | 是 | string  |  商品名称 | |
| categoryId      | 是| int  |  商品类别 |  |
| freightPrice      | 是| double  |  邮费 |  0 包邮 否则填具体运费 |
| detail      | 是| image 数组  |  图片 | 至少一张，格式参见 image 说明  |
| videos      | 否| Video 数组  |  视频 | 格式参见 Video 说明  |


_**image参数说明**_

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| url      | 是 | string  |  图片地址 | |
| size      | 是| string  |  图片尺寸 | 例如 1024*768  |


_**Video参数说明**_

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| url      | 是 | string  |  视频地址 | |
| cover      | 是 | string  |  封面地址 | |
| size      | 是| string  |  视频尺寸 | 例如 1024*768  |



_**specifications参数说明**_

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 否 | int  |  规格ID | id 不为空则是更新 |
| specificationId      | 是 | int  |  规格ID |  透过类别规格获取 |
| specificationName      | 是| string  |  规格名称 | 透过类别规格获取  |
| value      | 是| string  |  规格值 | |



_**products参数说明**_

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 否 | int  |  规格商品ID | id 不为空则是更新 |
| specifications      | 是 | Specification 数组  |   |  参见Specification  格式说明  |
| price      | 是| double  |  价格 |  价格 |
| number      | 是| int  |  库存数量 | |
| url      | 否 | string  |  商品url | |


_**Specification参数说明**_

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是 | int | 规格ID  |  根据规格类别取得  |
| value      | 是| string  |  规格值 |   |

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


#### 1.1.4 获取类别信息

##### 接口说明

类别信息获取

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/mall/catalog/all |





#####  输入参数

无

#####  错误说明




#####  返回实例
```json


{
    "c": 0,
    "m": null,
    "d": {
        "categoryList": [
            {
                "id": 1,
                "name": "水果",
                "keywords": "水果",
                "desc": "",
                "pid": 0,
                "iconUrl": "",
                "picUrl": "",
                "level": "L1",
                "sortOrder": 50,
                "addTime": null,
                "updateTime": null,
                "deleted": false
            },
            {
                "id": 2,
                "name": "蔬菜",
                "keywords": "蔬菜",
                "desc": "",
                "pid": 0,
                "iconUrl": "",
                "picUrl": "",
                "level": "L1",
                "sortOrder": 50,
                "addTime": null,
                "updateTime": null,
                "deleted": false
            }
        ],
        "currentCategory": {
            "id": 1,
            "name": "水果",
            "keywords": "水果",
            "desc": "",
            "pid": 0,
            "iconUrl": "",
            "picUrl": "",
            "level": "L1",
            "sortOrder": 50,
            "addTime": null,
            "updateTime": null,
            "deleted": false
        },
        "currentSubCategory": [
            {
                "id": 3,
                "name": "苹果",
                "keywords": "苹果",
                "desc": "",
                "pid": 1,
                "iconUrl": "",
                "picUrl": "",
                "level": "L2",
                "sortOrder": 50,
                "addTime": null,
                "updateTime": null,
                "deleted": false
            }
        ],
        "allList": {
            "1": [
                {
                    "id": 3,
                    "name": "苹果",
                    "keywords": "苹果",
                    "desc": "",
                    "pid": 1,
                    "iconUrl": "",
                    "picUrl": "",
                    "level": "L2",
                    "sortOrder": 50,
                    "addTime": null,
                    "updateTime": null,
                    "deleted": false
                }
            ],
            "2": []
        }
    }
}

```


#### 1.1.5 根据类别获取规格信息 

##### 接口说明

规格信息获取

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/mall/catalog/specification |





#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| id      | 是 | int | 类别ID  |   |



#####  错误说明




#####  返回实例
```json


{
    "c": 0,
    "m": null,
    "d": [
        {
            "id": 1,
            "catId": 0,
            "specificationName": "规格",
            "addTime": null
        },
        {
            "id": 2,
            "catId": 3,
            "specificationName": "颜色",
            "addTime": null
        },
        {
            "id": 3,
            "catId": 3,
            "specificationName": "重量",
            "addTime": null
        }
    ]
}

```


#### 1.1.6 商品详情

##### 接口说明

店主端商品管理主页

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/mall/admin/goods/detail |

#####  Header 头

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| storeId      | 是| int  |  商店ID |   用于店主权限校验 |



#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| goodsId      | 是 | int  |  商品ID|  |

#####  错误说明




#####  返回实例
```json


{
    "c": 0,
    "m": null,
    "d": {
        "catName": null,  //类别名称
        "goods": { //商品信息
            "id": 10000000,
            "storeId": 1, //商店ID
            "goodsSn": "", //商品sn
            "name": "测试",
            "categoryId": 3,
            "brandId": 0,
            "gallery": null,
            "keywords": "",
            "brief": "",
            "isOnSale": true,
            "sortOrder": 100,
            "picUrl": null,
            "shareUrl": null,
            "isNew": false,
            "isHot": false,
            "unit": "’件‘",
            "counterPrice": 0.00,
            "retailPrice": 3.00, //售价
            "vipPrice": 100000.00,
            "addTime": "2020-11-20 03:28:41",
            "updateTime": null,
            "deleted": false,
            "tags": null,
            "videos": null,
            "testReports": null,
            "goodsType": null,
            "auditStatus": 0,
            "freightPrice": 0.00, //运费
            "detail": null
        },
        "specifications": [ //商品规格
            {
                "id": 14,
                "storeId": 1,
                "goodsId": 10000000,
                "specificationId": 1,
                "specificationName": "规格",
                "value": "标准",
                "picUrl": "",
                "addTime": "2020-11-20 03:28:42",
                "updateTime": null,
                "deleted": false
            }
        ],
        "products": [ //规格商品信息
            {
                "id": 13,
                "storeId": 1,
                "goodsId": 10000000,
                "specifications": [
                    {
                        "id": 1,
                        "value": "标准"
                    }
                ],
                "price": 3.00,
                "number": 50,
                "url": null,
                "addTime": "2020-11-20 03:28:42",
                "updateTime": null,
                "deleted": false,
                "vipPrice": 0.00,
                "counterPrice": 0.00
            }
        ]
    }
}

```



#### 1.1.7 删除商品

##### 接口说明

删除商品信息

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/mall/admin/goods/del |

#####  Header 头

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| storeId      | 是| int  |  商店ID |   用于店主权限校验 |



#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| goodsId      | 是 | int  |  商品ID|  |

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


#### 1.1.8 商品下架

##### 接口说明

下架商品

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/mall/admin/goods/down |

#####  Header 头

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| storeId      | 是| int  |  商店ID |   用于店主权限校验 |



#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| goodsId      | 是 | int  |  商品ID|  |

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


#### 1.2 订单


#### 1.2.1 订单列表

##### 接口说明

订单列表信息

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /mall/admin/order/list |

#####  Header 头

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| storeId      | 是| int  |  商店ID |   用于店主权限校验 |



#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| showType      | 是|  int  |  订单列表  | 显示类型， 2，待发货； 3，待收货 5，已完成  |
| page      | 否|  int  |  分页  | 默认1  |
| limit      | 否|  int  |  限制单页条数  | 默认10  |






#####  错误说明




#####  返回实例
```json
    
{
    "c": 0,
    "m": null,
    "d": {
        "pageSize": 20,
        "total": 0,
        "currentPage": 1,
        "list": [
            {
                "id": 64,
                "orderSn": "20201123608626",
                "actualPrice": 3.00,
                "orderStatusText": "已付款",
                "aftersaleStatus": 0,
                "payTime": "2020-11-24 08:07:17",
                "totalNumber": 1,
                "goodsList": [
                    {
                        "id": 59,
                        "orderId": null,
                        "goodsId": null,
                        "goodsName": "测试",
                        "goodsSn": null,
                        "productId": null,
                        "number": 1,
                        "price": 3.00,
                        "specifications": [
                            {
                                "id": 1,
                                "value": "33"
                            }
                        ],
                        "picUrl": "",
                        "comment": null,
                        "addTime": null,
                        "updateTime": null,
                        "brief": null,
                        "gallery": null,
                        "videos": null,
                        "tags": null,
                        "aftersaleId": null,
                        "handleOption": null
                    }
                ]
            }
        ],
        "end": true,
        "empty": false,
        "startIndex": 0,
        "totalPage": 0
    }
}

```


#### 1.2.2 订单列表

##### 接口说明

订单列表信息

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /mall/admin/order/list |

#####  Header 头

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| storeId      | 是| int  |  商店ID |   用于店主权限校验 |



#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| showType      | 是|  int  |  订单列表  | 显示类型， 2，待发货； 3，待收货 5，已完成  |
| page      | 否|  int  |  分页  | 默认1  |
| limit      | 否|  int  |  限制单页条数  | 默认10  |






#####  错误说明




#####  返回实例
```json
    
{
    "c": 0,
    "m": null,
    "d": {
        "pageSize": 20,
        "total": 0,
        "currentPage": 1,
        "list": [
            {
                "id": 64,
                "orderSn": "20201123608626",
                "actualPrice": 3.00,
                "orderStatusText": "已付款",
                "aftersaleStatus": 0,
                "payTime": "2020-11-24 08:07:17",
                "totalNumber": 1,
                "goodsList": [
                    {
                        "id": 59,
                        "orderId": null,
                        "goodsId": null,
                        "goodsName": "测试",
                        "goodsSn": null,
                        "productId": null,
                        "number": 1,
                        "price": 3.00,
                        "specifications": [
                            {
                                "id": 1,
                                "value": "33"
                            }
                        ],
                        "picUrl": "",
                        "comment": null,
                        "addTime": null,
                        "updateTime": null,
                        "brief": null,
                        "gallery": null,
                        "videos": null,
                        "tags": null,
                        "aftersaleId": null,
                        "handleOption": null
                    }
                ]
            }
        ],
        "end": true,
        "empty": false,
        "startIndex": 0,
        "totalPage": 0
    }
}

```


#### 1.2.3 订单发货

##### 接口说明

订单列表信息

##### 请求说明

| http 请求方式          | post     |
|:------------- |:---------------:|
| url      | /mall/admin/order/ship |

#####  Header 头

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| storeId      | 是| int  |  商店ID |   用于店主权限校验 |



#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderId      | 是|  int  |  订单ID  | 订单ID |
| shipSn      | 是 |  string  |  物流单号  |  |
| shipChannel      | 是 |  string  | 物流编号  | 根据 /channel 接口返回 |






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


#### 1.2.4 物流公司查询

##### 接口说明

物流公司查询

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /mall/admin/order/channel |

#####  Header 头

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| storeId      | 是| int  |  商店ID |   用于店主权限校验 |



#####  输入参数


无






#####  错误说明




#####  返回实例
```json
    
{
    "c": 0,
    "m": null,
    "d": [
        {
            "code": "YZPY",
            "name": "中国邮政"
        },
        {
            "code": "JDKY",
            "name": "京东快递"
        },
        {
            "code": "SF",
            "name": "顺丰速运"
        },
        {
            "code": "ZTO",
            "name": "中通快递"
        },
        {
            "code": "YTO",
            "name": "圆通速递"
        },
        {
            "code": "YD",
            "name": "韵达速递"
        },
        {
            "code": "YZPY",
            "name": "邮政快递包裹"
        },
        {
            "code": "EMS",
            "name": "EMS"
        },
        {
            "code": "DBL",
            "name": "德邦快递"
        },
        {
            "code": "FAST",
            "name": "快捷快递"
        },
        {
            "code": "ZJS",
            "name": "宅急送"
        },
        {
            "code": "TNT",
            "name": "TNT快递"
        },
        {
            "code": "UPS",
            "name": "UPS"
        },
        {
            "code": "DHL",
            "name": "DHL"
        },
        {
            "code": "FEDEX",
            "name": "FEDEX联邦(国内件)"
        },
        {
            "code": "FEDEX_GJ",
            "name": "FEDEX联邦(国际件)"
        }
    ]
}
```


#### 1.3 退款地址

#### 1.0 用户收货地址列表

##### 接口说明

用户收货地址列表

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /admin/mall/address/list |

#####  输入参数

无

#####  错误说明


#####  返回实例
```json
    
  {
    "c": 0,
    "m": null,
    "d": {
        "pageSize": 1,
        "total": 1,
        "currentPage": 1,
        "list": [
            {
                "id": 3,  //地址ID
                "name": "我", //地址名称
                "userId": 11445, //用户ID
                "province": "北京市", //省份
                "city": "市辖区", //市区
                "county": "朝阳区", //地区
                "addressDetail": "211", //地址详情
                "areaCode": "110105", //地区编码
                "postalCode": null, //邮政编码
                "tel": "15201008961", //手机号
                "isDefault": true, //是否默认地址
                "addTime": "2020-06-29 14:46:15", //创建时间
                "updateTime": "2020-06-29 14:46:15", //更新时间
                "deleted": false //是否已删除
            }
        ],
        "unit": "条",
        "extInfo": null,
        "empty": false,
        "endIndex": 1,
        "startIndex": 0,
        "firstPage": true,
        "lastPage": true,
        "nextPage": 1,
        "previousPage": 1,
        "totalPages": 1
    }
}

```



#### 1.1 收货地址详情

##### 接口说明

收货地址详细信息

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /mall/admin/address/detail |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
|  id      | 是|  int  |  地址ID | |

#####  错误说明


#####  返回实例
```json
    
  {
    "c": 0,
    "m": null,
    "d": {
        "id": 3,  //地址ID
        "name": "我", //地址名称
        "userId": 11445, //用户ID
        "province": "北京市", //省份
        "city": "市辖区", //市区
        "county": "朝阳区", //地区
        "addressDetail": "211", //地址详情
        "areaCode": "110105", //地区编码
        "postalCode": null, //邮政编码
        "tel": "15201008961", //手机号
        "isDefault": true, //是否默认地址
        "addTime": "2020-06-29 14:46:15", //创建时间
        "updateTime": "2020-06-29 14:46:15", //更新时间
        "deleted": false //是否已删除
    }

}

```

#### 1.2 添加收货地址

##### 接口说明

添加收货地址

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /mall/admin/address/save |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
|  id      | 否|  int  |  收货地址 | |
|  name      | 是|  string  |  名称 | |
|  province      | 是|  string  |  省份 | |
|  city      | 是|  string  |  城市 | |
|  county      | 是|  string  |  乡 | |
|  addressDetail      | 是|  string  |  详细地址 | |
|  areaCode      | 是|  string  |  地址编码| |
|  postalCode      | 否|  string  |  邮政编码| |
|  tel      | 是|  string  |  电话 | |
|  isDefault      | 是|  boolean  | 是否默认地址 | |

#####  错误说明


#####  返回实例
```json
    
  {
    "c": 0,
    "m": null,
    "d": {
        "id": 3,  //地址ID
    }

}

```


#### 1.3 删除收货地址

##### 接口说明

删除收货地址

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /mall/admin/address/delete |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
|  id      | 是 |  int  |  收货地址 | |


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


#### 1.4 设置默认收货地址

##### 接口说明

收货地址详细信息

##### 请求说明

| http 请求方式          | post     |
|:------------- |:---------------:|
| url      | /mall/admin/address/default |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
|  id      | 是|  int  |  地址ID | |

#####  错误说明


#####  返回实例
```json
    
  {
    "c": 0,
    "m": null,
    "d": {
        "id": 3,  //地址ID
    }

}

```











### 用户端

-------

#### 1.1 商品

#### 1.1.1 小店商品列表接口


##### 接口说明

店主端商品管理主页

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/mall/goods/list |



#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| storeId      | 否 | int  |  商店ID |   |
| roomId      | 否 | string  |  空间ID |  空间/商店ID（有一个必填）  |
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
        "total": 1,
        "currentPage": 1,
        "list": [
            {
                "id": 10000000,
                "storeId": 1,
                "detail": null,
                "name": "测试",
                "retailPrice": 3.00
            }
        ],
        "end": true,
        "storeId": 1,
        "name": "大头娃",
        "images": null,
        "empty": false,
        "startIndex": 0,
        "totalPage": 1
    }
}

```


#### 1.1.2 商品详情

##### 接口说明

店主端商品管理主页

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/mall/goods/detail |




#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| goodsId      | 是 | int  |  商品ID|  |

#####  错误说明




#####  返回实例
```json


{
    "c": 0,
    "m": null,
    "d": {
        "catName": null,
        "goods": { //商品信息
            "id": 10000000,
            "storeId": 1,
            "goodsSn": "",
            "name": "测试",
            "categoryId": 3,
            "brandId": 0,
            "gallery": null,
            "keywords": "",
            "brief": "",
            "isOnSale": true,
            "sortOrder": 100,
            "picUrl": null,
            "shareUrl": null,
            "isNew": false,
            "isHot": false,
            "unit": "’件‘",
            "counterPrice": 0.00,
            "retailPrice": 3.00, //售价
            "vipPrice": 100000.00,
            "addTime": "2020-11-20 03:28:41",
            "updateTime": null,
            "deleted": false,
            "tags": null,
            "videos": null,
            "testReports": null,
            "goodsType": null,
            "auditStatus": 0,
            "freightPrice": 0.00, //运费
            "detail": null
        },
        "specifications": [ //商品规格
            {
                "id": 14,
                "storeId": 1,
                "goodsId": 10000000,
                "specificationId": 1,
                "specificationName": "规格",
                "value": "标准",
                "picUrl": "",
                "addTime": "2020-11-20 03:28:42",
                "updateTime": null,
                "deleted": false
            }
        ],
        "products": [ //规格商品信息
            {
                "id": 13,
                "storeId": 1,
                "goodsId": 10000000,
                "specifications": [
                    {
                        "id": 1,
                        "value": "标准"
                    }
                ],
                "price": 3.00,
                "number": 50,
                "url": null,
                "addTime": "2020-11-20 03:28:42",
                "updateTime": null,
                "deleted": false,
                "vipPrice": 0.00,
                "counterPrice": 0.00
            }
        ]
    }
}

```


#### 1.2 订单

#### 1.2.1 订单信息预览

##### 接口说明

店主端商品管理主页

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/mall/order/checkout |




#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| productId      | 是 | int  |  商品ID|  |
| amount      | 是 | int  |  商品数量|  |

#####  错误说明




#####  返回实例
```json


{
    "c": 0,
    "m": null,
    "d": {
        "goodsTotalPrice": 3.00,
        "freightPrice": 0.00, //邮费
        "orderTotalPrice": 3.00,
        "actualPrice": 3.00,
        "items": [  //
            {
                "storeId": 1,
                "storeName": "大头娃",
                "storeImages": null,
                "goodsList": [
                    {
                        "image": null,
                        "goodsId": 10000000,
                        "productId": null,
                        "name": "测试",
                        "specifications": null,
                        "price": 3.00,
                        "amount": 1
                    }
                ]
            }
        ],
        "defaultAddress": null, //默认地址
        "payTypes": [  //支付方式
            {
                "typeName": "balance",
                "comment": "余额支付",
                "thumbnail": null
            },
            {
                "typeName": "ALIPAYCASH",
                "comment": "支付宝支付",
                "thumbnail": null
            },
            {
                "typeName": "WX_APP",
                "comment": "微信支付",
                "thumbnail": null
            }
        ]
    }
}

```



#### 1.2.2 下单接口

##### 接口说明

店主端商品管理主页

##### 请求说明

| http 请求方式          |post             |
|:------------- |:---------------:|
| url      |/mall/order/submit |




#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| productId      | 是 | int  |  商品ID|  |
| amount      | 是 | int  |  商品数量|  |
| addressId      | 是 | int  |  地址   |  |
| message      | 否 | string  |  备注   |  |
| payType      | 是 | string  |  支付类型   | WX_APP  |

#####  错误说明




#####  返回实例
```json


 {
    "c": 0,
    "m": null,
    "d": {
            "payOrderId":xxxx,//订单号
            "callPayInfo":xxxxx, //各平台对应支付信息 
       }
    }

```



#### 1.2.3 取消订单

##### 接口说明

根据订单ID获取订单详细信息

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /mall/order/cancel |

#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderId      | 是|  int  |  订单详细信息  |  |


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


#### 1.2.4 支付订单

##### 接口说明

根据订单ID获取订单详细信息

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /mall/order/prepay |

#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderId      | 是|  int  |  订单ID  |  订单号 |
| payType      | 是|  string  |  支付方式  |  根据结算页拉取的支付项填写，小程序可以固定写死 WX_MP|






#####  错误说明




#####  返回实例
```json
    
   {
    "c": 0,
    "m": null,
    "d": {
            "payOrderId":xxxx,//订单号
            "callPayInfo":xxxxx, //各平台对应支付信息 
       }
    }

```




#### 1.2.5 订单列表

##### 接口说明

订单列表信息

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /mall/order/list |

#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| showType      | 是|  int  |  订单列表  | 显示类型，0，全部订单； 1，待付款； 2，待发货； 3，待收货； 4，待评价。 5，已完成  |
| page      | 否|  int  |  分页  | 默认1  |
| limit      | 否|  int  |  限制单页条数  | 默认10  |






#####  错误说明




#####  返回实例
```json
    
{
    "c": 0,
    "m": null,
    "d": {
        "pageSize": 20,
        "total": 0,
        "currentPage": 1,
        "list": [
            {
                "id": 64,
                "orderSn": "20201123608626",
                "actualPrice": 3.00,
                "orderStatusText": "未付款",
                "handleOption": { //操作按钮
                    "cancel": true,
                    "delete": false,
                    "pay": true,
                    "comment": false,
                    "confirm": false,
                    "refund": false,
                    "rebuy": false,
                    "aftersale": false,
                    "remind": false,
                    "logistic": false
                },
                "aftersaleStatus": 0,
                "goodsList": [  //订单商品信息
                    {
                        "id": 59,
                        "orderId": null,
                        "goodsId": null,
                        "goodsName": "测试",
                        "goodsSn": null,
                        "productId": null,
                        "number": 1,
                        "price": 3.00,
                        "specifications": [
                            {
                                "id": 1,
                                "value": "33"
                            }
                        ],
                        "picUrl": "",
                        "comment": null,
                        "addTime": null,
                        "updateTime": null,
                        "brief": null,
                        "gallery": null,
                        "videos": null,
                        "tags": null,
                        "aftersaleId": null,
                        "handleOption": null
                    }
                ],
                "storeInfo": {
                    "id": 1,
                    "name": "大头娃",
                    "intro": null,
                    "images": null
                },
                "groupin": false
            }       
        ],
        "end": true,
        "empty": false,
        "startIndex": 0,
        "totalPage": 0
    }
}

```




#### 1.2.6 订单详情

##### 接口说明

订单列表信息

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /mall/order/detail |

#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderId      | 是|  int  |   订单ID  |  |






#####  错误说明




#####  返回实例
```json
    
{
    {
    "c": 0,
    "m": null,
    "d": {
       "storeInfo": {
                    "id": 1,
                    "name": "大头娃",
                    "intro": null,
                    "images": null
                },
        "orderInfo": {  //订单信息
            "id": 47, //订单ID
            "orderSn": "20200711391009", //订单sN
            "message": "", //留言
            "addTime": "2020-07-11 18:48:01", //添加时间
            "payTime": "2020-07-11 18:48:01", //支付时间
            "consignee": "string", //收货人
            "mobile": "15201008961", //手机号
            "address": "stringstringstring string",  //收货地址
            "goodsPrice": 78.00,  //产品价格
            "couponPrice": 0.00, //优惠券价格
            "freightPrice": 8.00, //运费
            "actualPrice": 86.00, //实际支付
            "orderStatusText": "未付款",  //付款状态描述
            "handleOption": {  //处理状态
                "cancel": true,  //是否可取消
                "delete": false, //是否可删除
                "pay": true,  //是否可支付
                "comment": false, //是否可评论
                "confirm": false,  //是否可确认收货
                "refund": false, //是否可退货
                "rebuy": false, //是否可重新购买
                "aftersale": false, //是否可售后
                "remind": false, //是否可催单
                "logistic": true //是否可查看物流
            },
            "aftersaleStatus": 0,  //售后状态，0是可申请，1是用户已申请，2是管理员审核通过，3是管理员退款成功，4是管理员审核拒绝，5是用户已取消
            "expCode": null, //物流公司编码
            "expName": null, //物流名称
            "expNo": null //物流单号
        },
        "orderGoods": [  //订单产品信息
            {
                "id": 47,  //产品ID
                "orderId": 47, //订单ID
                "goodsId": 1006014, //商品ID
                "goodsName": "双宫茧桑蚕丝被 子母被", //名称
                "goodsSn": "1006014", //SN
                "productId": 11, //货品ID
                "number": 1, //数量
                "price": 1399.00, //价格
                "specifications": [  //规格
                    "标准"
                ],
                "handleOption": {  //操作按钮
                    "apply": false, //申请售后
                    "hotline": false, //客服热线
                    "cancel": false //取消售后
                },
                "aftersaleId":123,//售后ID
                "picUrl": "http://yanxuan.nosdn.127.net/2b537159f0f789034bf8c4b339c43750.png",  //图片
                "comment": 0,  //评论数
                "addTime": "2020-07-11 11:39:02", //添加时间
                "updateTime": "2020-07-11 11:39:02", //更新时间
                "deleted": false //是否已删除
            }
        ],
        "expressInfo": {
            "message": "ok",
            "nu": "SF1196520227006",
            "ischeck": "0",
            "condition": "00",
            "com": "shunfeng",
            "status": "200",
            "state": "0",
            "data": [
                {
                    "time": "2020-11-25 14:36:36",
                    "ftime": "2020-11-25 14:36:36",
                    "context": "[北京市]快件已发车"
                },
                {
                    "time": "2020-11-25 14:36:32",
                    "ftime": "2020-11-25 14:36:32",
                    "context": "[北京市]快件在【北京南法信中转场】已装车,准备发往 【北京海淀亿世界营业点】"
                },
                {
                    "time": "2020-11-25 14:05:25",
                    "ftime": "2020-11-25 14:05:25",
                    "context": "[北京市]快件到达 【北京南法信中转场】"
                },
                {
                    "time": "2020-11-25 13:57:30",
                    "ftime": "2020-11-25 13:57:30",
                    "context": "[北京市]快件已发车"
                },
                {
                    "time": "2020-11-25 13:52:50",
                    "ftime": "2020-11-25 13:52:50",
                    "context": "[北京市]快件在【北京顺义集散中心】已装车,准备发往 【北京南法信中转场】"
                },
                {
                    "time": "2020-11-25 13:02:45",
                    "ftime": "2020-11-25 13:02:45",
                    "context": "[北京市]快件到达 【北京顺义集散中心】"
                },
                {
                    "time": "2020-11-25 12:24:10",
                    "ftime": "2020-11-25 12:24:10",
                    "context": "[北京市]快件已发车"
                },
                {
                    "time": "2020-11-25 12:24:02",
                    "ftime": "2020-11-25 12:24:02",
                    "context": "[北京市]快件在【北京朝阳新荟城营业点】已装车,准备发往 【北京顺义集散中心】"
                },
                {
                    "time": "2020-11-25 11:08:19",
                    "ftime": "2020-11-25 11:08:19",
                    "context": "[北京市]顺丰速运 已收取快件"
                }
            ]
        }
    }
}

```


#### 1.2.7 取消订单

##### 接口说明

取消订单

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /mall/order/cancel |

#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderId      | 是|  int  |   订单ID  |  |






#####  错误说明




#####  返回实例
```json
    
{
    {
    "c": 0,
    "m": null,
    "d": {
       
    }
}

```



#### 1.2.8  重新支付订单

##### 接口说明

重新支付订单

##### 请求说明

| http 请求方式          | post     |
|:------------- |:---------------:|
| url      | /mall/order/prepay |

#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderId      | 是|  int  |   订单ID  |  |
| payType      | 是|  string  |   支付方式   |  根据结算页拉取的支付项填写，小程序可以固定写死 WX_MP |






#####  错误说明




#####  返回实例
```json
    
    {
    "c": 0,
    "m": null,
    "d": {
            "payOrderId":xxxx,//订单号
            "callPayInfo":xxxxx, //各平台对应支付信息 
       }
    }



```



#### 1.2.9  确认收货接口

##### 接口说明

订单列表信息

##### 请求说明

| http 请求方式          | post     |
|:------------- |:---------------:|
| url      | /mall/order/confirm |

#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderId      | 是|  int  |   订单ID  |  |


#####  错误说明




#####  返回实例
```json
    
    {
    "c": 0,
    "m": null,
    "d": {
        	
       }
    }



```


#### 1.2.10  删除订单接口

##### 接口说明

删除订单接口

##### 请求说明

| http 请求方式          | post     |
|:------------- |:---------------:|
| url      | /mall/order/delete |

#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderId      | 是|  int  |   订单ID  |  |


#####  错误说明




#####  返回实例
```json
    
    {
    "c": 0,
    "m": null,
    "d": {
        	
       }
    }



```



#### 1.2.11  评价接口

##### 接口说明

订单列表信息

##### 请求说明

| http 请求方式          | post     |
|:------------- |:---------------:|
| url      | /mall/order/comment |

#####  输入参数(post json)


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderGoodsId      | 是|  int  |   订单商品ID  |  |
| content      | 是|  string  |  商品内容信息  |  |
| star      | 是|  int  |  评价星级  | 1-5  |
| picUrls      | 是|  string[]  |  图片信息  |  |


    
``` json    
    {
      "anonymous": true,  //是否匿名
      "content": "string", //内容
      "picUrls": [ //图片数组
        {
            "url":"http://www.baidu.com", //url
            "type":"jpg/jpeg" //内容类型(可能是视频)
        }
      ],
      "star": 0, //星级
      "type": 0,  //如果是0，则查询商品评论；如果是1，则查询专题
      "valueId": 0  //商品或专题ID。如果type是0，则是商品ID；如果type是1，则是专题ID
    }
```



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



#### 1.2.12  待评价订单商品信息

##### 接口说明

待评价订单商品信息

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /order/goods |

#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderId      | 是|  int  |   订单ID  |  |


#####  错误说明




#####  返回实例
```json
    
    {
    "c": 0,
    "m": null,
    "d": {
        "id": 47,
        "orderId": 47,
        "goodsId": 1006014, //产品ID
        "goodsName": "双宫茧桑蚕丝被 子母被", // 产品名称
        "goodsSn": "1006014", //产品SN
        "productId": 11, //商品ID
        "number": 1, // 计数
        "price": 1399.00, //商品价格
        "specifications": [  //规格
            "标准"
        ],
        "picUrl": "http://yanxuan.nosdn.127.net/2b537159f0f789034bf8c4b339c43750.png",  //图片
        "comment": 0, //订单商品评论，如果是-1，则超期不能评价；如果是0，则可以评价；如果其他值，则是comment表里面的评论ID。
        "addTime": "2020-07-11 11:39:02",  //添加时间
        "updateTime": "2020-07-11 11:39:02", //更新时间
        "deleted": false
    }
}

```




#### 1.2.13 催单接口

##### 接口说明

催单

##### 请求说明

| http 请求方式          | post     |
|:------------- |:---------------:|
| url      | /order/remind |

#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderId      | 是|  int  |  订单详细信息  |  |


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



#### 1.2.14 重新购买

##### 接口说明

重新购买

##### 请求说明

| http 请求方式          | post     |
|:------------- |:---------------:|
| url      | /mall/order/rebuy |

#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderId      | 是|  int  |  订单详细信息  |  |


#####  错误说明




#####  返回实例
```json
    
   {
    "c": 0,
    "m": null,
    "d": {
        "addressId": 3,   //地址ID
        "couponId": 2, //优惠券ID
        "userCouponId": 5, //用户优惠券ID
        "cartId": 0, // 购物车ID
        "grouponRulesId": 0, //团购规则
        "grouponPrice": 0, //团购价
        "checkedAddress": {   //地址的选择
            "id": 3,  //地址ID
            "name": "我", //地址名称
            "userId": 11445, //用户ID
            "province": "北京市", //省
            "city": "市辖区", //市
            "county": "朝阳区", //朝阳
            "addressDetail": "211", //地址详情
            "areaCode": "110105", //地址编码
            "postalCode": null, //邮政编码
            "tel": "15201008961", //手机号
            "isDefault": true, //是否默认
            "addTime": "2020-06-29 14:46:15", //创建时间
            "updateTime": "2020-06-29 14:46:15", //更新时间
            "deleted": false //是否已删除
        },
        "availableCouponLength": 2, //可用优惠券数量
        "goodsTotalPrice": 237.00, //产品总价格
        "freightPrice": 0,  //运费
        "couponPrice": 10.00, //优惠金额
        "orderTotalPrice": 227.00, //订单总金额
        "actualPrice": 227.00, //实付金额 
        "checkedGoodsList": [  //结算商品列表
            {
                "id": 10,  //ID
                "userId": 11445, //用户ID
                "goodsId": 1057036, //产品ID
                "goodsSn": "1057036", //产品SN
                "goodsName": "日式纯色水洗亚麻抱枕", //产品名称
                "productId": 71, //商品ID
                "price": 79.00, //商品价格
                "number": 3, //商品数量
                "specifications": [  //规格
                    "标准"
                ],
                "checked": true, //是否选中
                "picUrl": "http://yanxuan.nosdn.127.net/8a9ee5ba08929cc9e40b973607d2f633.png", //缩略图
                "addTime": "2020-07-03 23:11:14", //添加时间
                "updateTime": "2020-07-03 23:35:09", //更新时间
                "deleted": false //是否已删除
            }
        ],
    "payTypes": [  //支付方式列表
            {
                "typeName": "balance",
                "comment": "余额支付",
                "thumbnail": null
            },
            {
                "typeName": "ALIPAYCASH",
                "comment": "支付宝支付",
                "thumbnail": null
            },
            {
                "typeName": "WX_APP",
                "comment": "微信支付",
                "thumbnail": null
            }
        ]   
    }
}


```



#### 1.2.15 订单重新支付

##### 接口说明

订单重新支付 

##### 请求说明

| http 请求方式          | get     |
|:------------- |:---------------:|
| url      | /mall/order/repay |

#####  输入参数


| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| orderId      | 是|  int  |   订单ID  |  |






#####  错误说明




#####  返回实例
```json
    
{
    {
    "c": 0,
    "m": null,
    "d": {
        "actualPrice":1.23, //实付金额
        "payTypes":[  //支付方式列表
            {
                "typeName": "balance",
                "comment": "余额支付",
                "thumbnail": null
            },
            {
                "typeName": "ALIPAYCASH",
                "comment": "支付宝支付",
                "thumbnail": null
            },
            {
                "typeName": "WX_APP",
                "comment": "微信支付",
                "thumbnail": null
            }
        ] 
    }
}

```








































