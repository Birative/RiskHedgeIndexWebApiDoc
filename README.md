

# RiskHedge指數接口文档[![HitCount](http://hits.dwyl.io/{BBSee}/{Risk_Hedge}.svg)](http://hits.dwyl.io/{BBSee}/{star_reading})

|     开发部门     |       RiskHedge       |
| :--------------: | :------------------------: |
|      开发者      |           BBSee           |
|       文档       |           BBSee           |
|       邮箱       |  |
|   文档编辑时间   |         2020.7.21         |
|      统一编码           |         UTF-8无BOM         |
|     统一时区     |       UTC/GMT+08:00        |
| 小数默认精确位数 |             2             |



## 一、websocket接口文档

连接websocket，指数每秒发布一次，服务器会向客户端主动推送该条数据

### 1、获取实时数据接口

接口说明

- [x] 接口说明: 连接websocket即可获取实时推送
- [x] 请求地址： ws://host+port/index
- [x] 请求方式：
  - Method="*“
  - Content-Type: "application/json"
  - Auth: Not Required
- [x] 请求参数：

| 参数名称 | 参数类型 | 是否必须 | 说明 |
| :------: | :------: | :------: | :--: |
|    *     |    *     |    *     |  *   |



- [x] 返回参数

| 响应类型 | 响应参数 | 参数说明 |      |
| :------: | :------: | :------: | ---- |
| 成功响应 |  见附表  |  见附表  |      |
| 失败响应 |  见附表  |  见附表  |      |

```json
{"data":
 "{"action":"update",
 "data":"{"timestamp": 1595317771281, 
 "index": 930.92, //指数
 "btc_price": 9324.08, 
 "btc_price_5min": 9349.22,
 "gold_price": 1822.19, 
 "gold_price_5min": 1822.42}",
"message":"success",
"statusCode":1,
"timestamp":1595317771289}",
"action":"update",
"message":"success",
"statusCode":1,//0 for failure 1 for success
"timestamp":1595317771789}
```





### 2、查询历史记录接口

接口说明

- [x] 接口说明:获取历史记录
- [x] 请求地址： ws://host+port/index
- [x] 请求方式：
  - Method="*“
  - Content-Type: "application/json"
  - Auth: Not Required
- [x] 请求参数：

|  参数名称  | 参数类型 | 是否必须 |               说明                |
| :--------: | :------: | :------: | :-------------------------------: |
|   action   |  String  |    Y     | action="history" 用于查询历史记录 |
| timestamp  |   long   |    Y     |           请求的时间戳            |
|   start    |   long   |    Y     |     查询历史记录的起始时间戳      |
|    end     |   long   |    Y     |     查询历史记录的终止时间戳      |
|  pageSize  |   int    |    Y     |      分页参数-最大为50000条       |
| pageNumber |   int    |    Y     |      分页参数-页码-起始值为1      |

```json
---请求实例----
{"action":"history",
 "timestamp":1595315029872,
 "start":1595314969872,
 "end":1595315029872,
 "pageSize":50000,
 "pageNumber":1
}
```



- [x] 返回参数

| 响应类型 | 响应参数 | 参数说明 |      |
| :------: | :------: | :------: | ---- |
| 成功响应 |  见附表  |  见附表  |      |
| 失败响应 |  见附表  |  见附表  |      |

```json
{"action":"history","data":{"number":0,"last":true,"numberOfElements":28122,"size":50000,"totalPages":1,"pageable":{"paged":true,"pageNumber":0,"offset":0,"pageSize":50000,"unpaged":false,"sort":{"unsorted":true,"sorted":false}},"sort":{"unsorted":true,"sorted":false},"content":[{"goldPrice_5min":1520.0,"btcPrice_5min":7114.0,"goldPrice":1521.0,"index":1000.6,"btcPrice":7114.0,"id":1563671,"timestamp":1577891040000},{"goldPrice_5min":1589.0,"btcPrice_5min":9248.0,"goldPrice":1589.0,"index":1153.12,"btcPrice":9248.0,"id":1591792,"timestamp":1580479140000}],"first":true,"totalElements":28122},
    "message":"success",
    "statusCode":1,//0 for failure,1 for success
    "timestamp":1595316447498}
```





### 3、服务器ping

接口说明

- [x] 接口说明:服务器推送的ping信息,5秒一次
- [x] 请求地址：
- [x] 请求方式：
  - Method=*
  - Content-Type: "application/json"
  - Auth: Not Required
- [x] 请求参数：

| 参数名称 | 参数类型 | 是否必须 | 说明 |
| :------: | :------: | :------: | :--: |
|    *     |    *     |    *     |  *   |

- [x] 返回参数

| 响应类型 | 响应参数 | 参数说明 |      |
| :------: | :------: | :------: | ---- |
| 成功响应 |  见附表  |  见附表  |      |
| 失败响应 |  见附表  |  见附表  |      |

```json
{"action":"ping","message":"server ping","statusCode":1,"timestamp":1595317973198}
```

