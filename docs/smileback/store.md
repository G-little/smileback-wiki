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








































