# 欢迎来到回眸文档

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## 测试环境说明

* 测试域名 	[http://smileback.xiaogang.org.cn](http://smileback.xiaogang.org.cn)
* 获取上传token接口: {{host}}/upload/token




## 通用接口

### 通用配置接口 

##### 请求说明

| http 请求方式          |get             |
|:------------- |:---------------:|
| url      |/config/global |

#####  输入参数

| 参数          |必选             | 类型       | 参数说明        | 备注          |
|:-------------|:---------------:|:-------------|:-------------|:-------------|
| platform      | 是| string  |  android/ios |  |



```json

{
c: 0,
m: null,
d: {
    provinces: [
    {
    code: "110000",
    name: "北京"
    }],
    servicePhone: "17301082390"
  }
}

```
