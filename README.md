# byd.me API文档

## 域名注册查询接口

### 域名
  - 临时先用ip+端口 新域名还未备案
### 鉴权
  - 临时未开启 需要申请app id分配权限
### 请求方式 
  - GET
### 请求路径
  - /api/domain/check
### 请求参数
  - name  域名，支持带后缀和不带后缀
### 请求示例
  - /api/domain/check?name=hello
### 响应格式
  - json
### 响应示例


  使用Roaring Bitmaps（一种压缩位图实现 https://roaringbitmap.org 有多种语言实现）存储每个后缀是否可注册
  ```
  {
    data: {
        avaiable: false, // 带后缀时会返回指定后缀是否能注册
        bitmap: "OjAAAAEAAAAAADMBEAAAAAAAAQACAAMABAAFAAYABwAIAAkACgALAAwADQAOAA8AEAARABIAEwAUABUAFgAXABgAGQAaABsAHAAdAB4AHwAgACEAIgAjACQAJQAmACcAKAApACoAKwAsAC0ALgAvADAAMQAyADMANAA1ADYANwA4ADkAOgA7ADwAPQA+AD8AQABBAEIAQwBEAEUARgBHAEgASQBKAEsATABNAE4ATwBQAFEAUgBTAFQAVQBWAFcAWABZAFoAWwBcAF0AXgBfAGAAYQBiAGMAZABlAGYAZwBoAGkAagBrAGwAbQBuAG8AcABxAHIAcwB0AHUAdgB3AHgAeQB6AHsAfAB9AH4AfwCAAIEAggCDAIQAhQCGAIcAiACJAIoAiwCMAI0AjgCPAJAAkQCSAJMAlACVAJYAlwCYAJkAmgCbAJwAnQCeAJ8AoAChAKIAowCkAKUApgCnAKgAqQCqAKsArACtAK4ArwCwALEAsgCzALQAtQC2ALcAuAC5ALoAuwC8AL0AvgC/AMAAwQDCAMMAxADFAMYAxwDIAMkAygDLAMwAzQDOAM8A0ADRANIA0wDUANUA1gDXANgA2QDaANsA3ADdAN4A3wDgAOEA4gDjAOQA5QDmAOcA6ADpAOoA6wDsAO0A7gDvAPAA8QDyAPMA9AD1APYA9wD4APkA+gD7APwA/QD+AP8AAAEBAQIBAwEEAQUBBgEHAQgBCQEKAQsBDAENAQ4BDwEQAREBEgETARQBFQEWARcBGAEZARoBGwEcAR0BHgEfASABIQEiASMBJAElASYBJwEoASkBKgErASwBLQEuAS8BMAExATIBMwE=",
        query: "hello", 
        tld: "" // 带后缀时会返回后缀 例如.com
    },
    msg: "ok", // 请求提示
    status: 200  // 请求状态码 200：成功 500：内部错误 400：参数错误
  }
  ```

### bitmap映射关系
- ".com"=0
- ".net"=1
- ".org"=2
- ".info"=3
- ".name"=4
- ".io"=5
- ".link"=6
- ".click"=7
- ".email"=8
- ".top"=9
- ".pro"=10
- ".xyz"=11
- ".one"=12
- ".app"=13
- ".site"=14
- ".tech"=15
- ".today"=16
