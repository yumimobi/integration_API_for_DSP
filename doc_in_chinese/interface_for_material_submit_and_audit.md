# API接口

- [API接口](#api%E6%8E%A5%E5%8F%A3)
    - [文档更新记录](#%E6%96%87%E6%A1%A3%E6%9B%B4%E6%96%B0%E8%AE%B0%E5%BD%95)
    - [DSP辅助API服务器根地址](#dsp%E8%BE%85%E5%8A%A9api%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%A0%B9%E5%9C%B0%E5%9D%80)
    - [物料审核API](#%E7%89%A9%E6%96%99%E5%AE%A1%E6%A0%B8api)
        - [提交广告素材api](#%E6%8F%90%E4%BA%A4%E5%B9%BF%E5%91%8A%E7%B4%A0%E6%9D%90api)
            - [原生广告Asset](#%E5%8E%9F%E7%94%9F%E5%B9%BF%E5%91%8Aasset)
            - [原生广告Title](#%E5%8E%9F%E7%94%9F%E5%B9%BF%E5%91%8Atitle)
            - [原生广告Image](#%E5%8E%9F%E7%94%9F%E5%B9%BF%E5%91%8Aimage)
            - [原生广告Data](#%E5%8E%9F%E7%94%9F%E5%B9%BF%E5%91%8Adata)
            - [原生广告Link](#%E5%8E%9F%E7%94%9F%E5%B9%BF%E5%91%8Alink)
        - [返回信息说明](#%E8%BF%94%E5%9B%9E%E4%BF%A1%E6%81%AF%E8%AF%B4%E6%98%8E)
    - [查询审核未通过的广告信息](#%E6%9F%A5%E8%AF%A2%E5%AE%A1%E6%A0%B8%E6%9C%AA%E9%80%9A%E8%BF%87%E7%9A%84%E5%B9%BF%E5%91%8A%E4%BF%A1%E6%81%AF)
        - [返回信息说明](#%E8%BF%94%E5%9B%9E%E4%BF%A1%E6%81%AF%E8%AF%B4%E6%98%8E)
    - [查询广告的审核状态](#%E6%9F%A5%E8%AF%A2%E5%B9%BF%E5%91%8A%E7%9A%84%E5%AE%A1%E6%A0%B8%E7%8A%B6%E6%80%81)
        - [返回信息说明](#%E8%BF%94%E5%9B%9E%E4%BF%A1%E6%81%AF%E8%AF%B4%E6%98%8E)
    - [查询DSP统计信息](#%E6%9F%A5%E8%AF%A2dsp%E7%BB%9F%E8%AE%A1%E4%BF%A1%E6%81%AF)
        - [返回信息说明](#%E8%BF%94%E5%9B%9E%E4%BF%A1%E6%81%AF%E8%AF%B4%E6%98%8E)
        - [StatInfo](#statinfo)
    - [DSP投放设置api](#dsp%E6%8A%95%E6%94%BE%E8%AE%BE%E7%BD%AEapi)
        - [返回信息说明](#%E8%BF%94%E5%9B%9E%E4%BF%A1%E6%81%AF%E8%AF%B4%E6%98%8E)
    - [获取DSP投放设置api](#%E8%8E%B7%E5%8F%96dsp%E6%8A%95%E6%94%BE%E8%AE%BE%E7%BD%AEapi)
        - [返回信息说明](#%E8%BF%94%E5%9B%9E%E4%BF%A1%E6%81%AF%E8%AF%B4%E6%98%8E)

## 文档更新记录

| 版本 | 作者 |    时间    |                  备注                  |
| ---- | ---- | ---------- | -------------------------------------- |
|  0.1 | Cui  | 2015.10.27 | 创建                                   |
|  0.2 | Wei  | 2015.11.24 | 添加DSP统计信息接口                    |
|  0.3 | Wei  | 2016.03.29 | 上传接口中添加广告类型和广告尺寸的参数 |
|  0.4 | Qi   | 2016.03.02 | 添加DSP投放设置及获取接口              |
|  0.5 | Wei  | 2016.09.27 | 添加前审的广告素材提交api              |
|  0.6 | Zhen | 2016.11.09 | 删除upload接口；更改upload2审核状态    |
|  1.0 | Zhen | 2017.03.20 | rst方式构建新文档                      |

## DSP辅助API服务器根地址

    http://dspapi.adx.yumimobi.com/

## 物料审核API

|    方法   | 格式 |  编码 |
| --------- | ---- | ----- |
| HTTP POST | JSON | UTF-8 |

### 提交广告素材api

    | url: /dsp/api/inventory/upload2

```json

    {
        "dsp_token": "d52b426d8d5a4adeb998f1ba0b290014",
        "ad_id": "adid_g72",
        "ad_type": 4,
    	"ad_size":"320x50",
        "client_name": "client_32",
        "target_url": "http://target.com/FfAB",
    	"file_urls":[
    		"http://baidu.com/img/123.jpg"
    	],
        "native": [
            {
                "id": 1,
                "title": {
                    "text": "title01"
                }
            },
            {
                "id": 2,
                "img": {
                    "url": "http://test.com/test_02.jpg",
                    "w": 640,
                    "h": 960
                },
                "link": {
                    "url": "http://test.com/link_02",
                    "type": 2
                }
            },
            {
                "id": 3,
                "data": {
                    "label": "label_01",
                    "value": "http://test.com/lable_01.jpg"
                }
            },
            {
                "id": 4,
                "data": {
                    "label": "label_02",
                    "value": "test_02"
                }
            }
        ]
    }
```

|   字段名称  |  类型  | 必须 |                                                                               描述                                                                               |
| ----------- | ------ | ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| dsp_token   | string | 是   | dsp令牌，可在dsp控制面板，或联系zplay adx业务人员得到                                                                                                            |
| ad_id       | string | 是   | 广告id，由dsp生成                                                                                                                                                |
| ad_type     | int    | 是   | 广告类型，现在支持的类型有0(banner)，1(插屏)，2(开屏)，3(原生)，4(视频)                                                                                          |
| ad_size     | string | 否   | 广告尺寸，例如"320x50"，格式为"宽x高"，可用尺寸参考adx提供的广告尺寸文档，原生广告不需要尺寸信息，其他广告形式需要此信息                                         |
| target_url  | string | 是   | 点击广告后的目标url                                                                                                                                              |
| client_name | string | 否   | 广告主名称                                                                                                                                                       |
| file_urls   | 数组   | 否   | 广告素材文件数组，当广告类型(ad_type)为视频(4)时，需要一个视频素材链接(.mp4结尾)和一个图片素材链接(.jpg或.png或.gif结尾)，原生广告不需要此信息，其他广告形式需要 |
| native      | 数组   | 否   | 原生广告数组，广告类型为原生时，需要此信息，其他广告类型不需要                                                                                                   |

#### 原生广告Asset

| 字段名称 | 类型 | 必须 |                             描述                            |
| -------- | ---- | ---- | ----------------------------------------------------------- |
| id       | int  | 是   | 广告元素ID                                                  |
| title    | 对象 | 否   | 文字元素，同一个asset中，仅能包含title,img,data中的一个     |
| img      | 对象 | 否   | 图片元素，同一个asset中，仅能包含title,img,data中的一个     |
| data     | 对象 | 否   | 其他数据元素，同一个asset中，仅能包含title,img,data中的一个 |
| link     | 对象 | 否   | Link对象，点击地址                                          |

#### 原生广告Title

| 字段名称 |  类型  | 必须 |         描述        |
| -------- | ------ | ---- | ------------------- |
| text     | string | 是   | title元素的内容文字 |

#### 原生广告Image

| 字段名称 |  类型  | 必须 |        描述        |
| -------- | ------ | ---- | ------------------ |
| url      | string | 是   | image元素的URL地址 |
| w        | int    | 否   | 宽度，单位像素     |
| h        | int    | 否   | 宽度，单位像素     |

#### 原生广告Data

| 字段名称 |  类型  | 必须 |      描述      |
| -------- | ------ | ---- | -------------- |
| label    | string | 否   | 数据显示的名称 |
| value    | string | 是   | 数据的内容文字 |

#### 原生广告Link

|   字段名称   |  类型  | 必须 |                                                            描述                                                            |
| ------------ | ------ | ---- | -------------------------------------------------------------------------------------------------------------------------- |
| url          | string | 是   | 点击URL                                                                                                                    |
| clicktracker | array  | 否   | 点击跟踪URL                                                                                                                |
| type         | int    | 否   | 广告动作类型，1:在app内webview打开目标链接，2：在系统浏览器打开目标链接，3：打开地图，4： 拨打电话，5：播放视频，6:App下载 |

> 原生广告定义遵循[OpenRTB Dynamic Native Ads Specification 1.0](http://www.iab.net/media/file/OpenRTB-Native-Ads-Specification-1_0-Final.pdf)标准，请下载。

### 返回信息说明

| 字段名称 |  类型  | 必须 |           描述           |
| -------- | ------ | ---- | ------------------------ |
| ret      | int    | 是   | 0表示成功，其他请参见msg |
| msg      | string | 否   | 失败时，返回详细信息     |

## 查询审核未通过的广告信息

    url: /dsp/api/inventory/denylist

```json

    {
    	"dsp_token":"",
    	"upload_date":"2015-01-01"
    }
```

|   字段名称  |  类型  | 必须 |                                                  描述                                                  |
| ----------- | ------ | ---- | ------------------------------------------------------------------------------------------------------ |
| dsp_token   | string | 是   | dsp令牌，可在dsp控制面板，或联系zplay adx业务人员得到                                                  |
| upload_date | string | 否   | 查询的起始时间，将返回该时间之后所有未审核通过的广告列表；如果该值为空，则返回所有审核未通过的广告列表 |

```json

    {
    	"ret":0,
    	"msg":"",
    	"denied_list" : [
    		{
    			"ad_id":"",
    			"deny_reason":""
    		}
    	]
    }
```

### 返回信息说明

|   字段名称  |  类型  | 必须 |           描述           |
| ----------- | ------ | ---- | ------------------------ |
| ret         | int    | 是   | 0表示成功，其他请参见msg |
| msg         | string | 否   | 失败时，返回详细信息     |
| ad_id       | string | 是   | 广告id，由dsp生成        |
| deny_reason | string | 是   | 拒绝原因                 |

## 查询广告的审核状态

    url: /dsp/api/inventory/query_review_state

```json

    {
    	"dsp_token":"",
    	"ads":[
    		"1" , "2"
    	]
    }
```

|  字段名称 |  类型  | 必须 |                          描述                         |
| --------- | ------ | ---- | ----------------------------------------------------- |
| dsp_token | string | 是   | dsp令牌，可在dsp控制面板，或联系zplay adx业务人员得到 |
| ads       | 数组   | 是   | 要查询的广告id数组                                    |

```json

    {
    	"ret":0,
    	"msg":"",
    	"ads" : [
    		{
    			"ad_id":"",
    			"review_state":0,
    			"deny_reason":""
    		}
    	]
    }
```

### 返回信息说明

|   字段名称   |  类型  | 必须 |                    描述                   |
| ------------ | ------ | ---- | ----------------------------------------- |
| ret          | int    | 是   | 0表示成功，其他请参见msg                  |
| msg          | string | 否   | 失败时，返回详细信息                      |
| ad_id        | string | 是   | 广告id，由dsp生成                         |
| review_state | int    | 是   | 审核状态, 0:待审核，1:审核通过，2：被拒绝 |
| deny_reason  | string | 是   | 拒绝原因                                  |

## 查询DSP统计信息

    url: /dsp/api/inventory/query_stat_info

```json

    {
    	"dsp_token":"",
    	"start_time":"",
        "end_time":""
    }
```

|  字段名称 |  类型  | 必须 |                          描述                         |
| --------- | ------ | ---- | ----------------------------------------------------- |
| dsp_token | string | 是   | dsp令牌，可在dsp控制面板，或联系zplay adx业务人员得到 |
| start_time  | int      | 是        | 要查询的统计信息的起始时间的时间戳，单位为秒                    |
| end_time    | int      | 是        | 要查询的统计信息的结束时间的时间戳，单位为秒                    |

```json

    {
    	"ret":0,
    	"msg":"",
    	"stat_info":StatInfo
    }
```

### 返回信息说明

|  字段名称 |  类型  | 必须 |           描述           |
| --------- | ------ | ---- | ------------------------ |
| ret       | int    | 是   | 0表示成功，其他请参见msg |
| msg       | string | 否   | 失败时，返回详细信息     |
| stat_info | string | 是   | 广告id，由dsp生成        |

### StatInfo

```json

    {
      "query_count":1,
      "bid_count":1,
      "timeout_count":1,
      "error_count":1,
      "win_count":1,
      "display_count":1,
      "click_count":1,
      "consume_amount":1.3
    }
```

|    字段名称    |  类型 | 必须 |     描述     |
| -------------- | ----- | ---- | ------------ |
| query_count    | int   | 是   | 询价次数     |
| bid_count      | int   | 是   | 出价次数     |
| timeout_count  | int   | 是   | 超时次数     |
| error_count    | int   | 是   | 错误次数     |
| win_count      | int   | 是   | 竞价获胜次数 |
| display_count  | int   | 是   | 广告展示次数 |
| click_count    | int   | 是   | 广告点击次数 |
| consume_amount | float | 是   | 消费金额     |

## DSP投放设置api

    url: /dsp/api/setting

    为了保证安全性，dsp投放设置api额外增加签名验证，需要在HTTP Header中额外增加以下信息：

    authorization：{signature}  

    签名算法：  

    {signature} = md5({SecretKey}+{JsonString})

    {SecretKey}：是DSP注册时接受邮件中的“解密秘钥”  

    {JsonString}：是POST的json字符串

```json

    {
    	"dsp_token":"c3438279d331467eb8fd7f731b98e517",
    	"qps":123,
    	"ad_type":[0,1,2,3],
    	"device_type":["phone","pad"],
    	"connection_type":["wifi", "4G"],
    	"os_type":["ios","android"]
    }
```

|     字段名称    |     类型     | 必须 |                                   描述                                  |
| --------------- | ------------ | ---- | ----------------------------------------------------------------------- |
| dsp_token       | string       | 是   | dsp令牌，可在dsp控制面板，或联系zplay adx业务人员得到                   |
| qps             | int          | 否   | qps                                                                     |
| ad_type         | int          | 否   | 广告类型，现在支持的类型有0(banner)，1(插屏)，2(开屏)，3(原生)，4(视频) |
| device_type     | string array | 否   | 设备类型，可选值(phone、pad)                                            |
| connection_type | string array | 否   | 网络连接类型,可选值（wifi、2G、3G、4G, Unknown）                        |
| os_type         | string array | 否   | 操作系统类型 可选值(ios、android)                                       |

### 返回信息说明

| 字段名称 |  类型  | 必须 |           描述           |
| -------- | ------ | ---- | ------------------------ |
| ret      | int    | 是   | 0表示成功，其他请参见msg |
| msg      | string | 否   | 失败时，返回详细信息     |

## 获取DSP投放设置api

    url: /dsp/api/get_setting

```json

    {
    	"dsp_token":"c3438279d331467eb8fd7f731b98e517"
    }
```

|  字段名称 |  类型  | 必须 |                          描述                         |
| --------- | ------ | ---- | ----------------------------------------------------- |
| dsp_token | string | 是   | dsp令牌，可在dsp控制面板，或联系zplay adx业务人员得到 |

### 返回信息说明

|     字段名称    |     类型     | 必须 |                                   描述                                  |
| --------------- | ------------ | ---- | ----------------------------------------------------------------------- |
| ret             | int          | 是   | 0表示成功，其他请参见msg                                                |
| msg             | string       | 否   | 失败时，返回详细信息                                                    |
| qps             | int          | 是   | qps                                                                     |
| ad_type         | int          | 是   | 广告类型，现在支持的类型有0(banner)，1(插屏)，2(开屏)，3(原生)，4(视频) |
| device_type     | string array | 是   | 设备类型，可选值(phone、pad)                                            |
| connection_type | string array | 是   | 网络连接类型,可选值（wifi、2G、3G、4G, Unknown）                        |
| os_type         | string array | 是   | 操作系统类型 可选值(ios、android)                                       |

```json

        {
        	"ret":0,
        	"msg":"",
        	"qps":123,
        	"ad_type":[0,1,2,3],
        	"device_type":["phone","pad"],
        	"connection_type":["wifi", "4G"],
        	"os_type":["ios","android"]
        }
```
