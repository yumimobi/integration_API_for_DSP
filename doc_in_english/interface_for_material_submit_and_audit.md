# API DOCUMENTATION

- [API DOCUMENTATION](#api-documentation)
    - [Logs](#logs)
        - [domain of API request](#domain-of-api-request)
    - [Material auditing](#material-auditing)
        - [Submit material](#submit-material)
            - [native Asset](#native-asset)
            - [native.title](#nativetitle)
            - [native.img](#nativeimg)
            - [native.data](#nativedata)
            - [native.Link](#nativelink)
        - [response](#response)
    - [get the unapproved material](#get-the-unapproved-material)
        - [response](#response)
    - [get the auditing status of material](#get-the-auditing-status-of-material)
        - [response](#response)
    - [get the statistics](#get-the-statistics)
        - [response](#response)
        - [StatInfo](#statinfo)

## Logs

| version | editor | date       | note                                                            |
| ------- | ------ | ---------- | --------------------------------------------------------------- |
| 0.1     | Cui    | 2015.10.27 | -                                                               |
| 0.2     | Wei    | 2015.11.24 | add API of getting statistics data                              |
| 0.3     | Wei    | 2016.03.29 | add parameters of ad type and ad size in API of material upload |
| 0.4     | Qi     | 2016.03.02 | add API of DSP setting and getting setting                      |

### domain of API request

    http://dspapi.adx.yumimobi.com/

## Material auditing

| method    | format | code  |
| --------- | ------ | ----- |
| HTTP POST | JSON   | UTF-8 |

### Submit material

**url**: /dsp/api/inventory/upload2

```json

    {
        "dsp_token": "d52b426d8d5a4adeb998f1ba0b290014",
        "ad_id": "adid_g72",
        "ad_type": 4,``
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

| parameter   | type   | mandatory | description                                                                                                                                                                                    |
| ----------- | ------ | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| dsp_token   | string | yes       | you can find it on our dashboard or contact our account manager to get it                                                                                                                      |
| ad_id       | string | yes       | advertising ID, is created by DSP                                                                                                                                                              |
| ad_type     | int    | yes       | ads type, including: 0:banner, 1:interstitial, 2:splash, 3:native, 4:rewarded video                                                                                                            |
| ad_size     | string | no        | ads size, eg. "320x50", "width x height", [view available ads](suggested_ad_size.md)                                                                                                           |
| target_url  | string | no        | the URL that should goto when users tap the ads                                                                                                                                                |
| client_name | string | no        | advertiser name                                                                                                                                                                                |
| file_urls   | array  | no        | material, using this array when ad types are banner, interstitial, splash and rewarded video. if ad type is rewarded video, you need upload a video(.mp4) as well an image(.jpg, .png or .gif) |
| native      | array  | no        | native array, using this array only when ad type is native                                                                                                                                     |

#### native Asset

| parameter | type   | mandatory | description                                                        |
| --------- | ------ | --------- | ------------------------------------------------------------------ |
| id        | int    | yes       | material ID                                                        |
| title     | object | no        | only includes a title in an asset object                           |
| img       | object | no        | only includes an img in an asset object                            |
| data      | object | no        | other element of material, only includes a data in an asset object |
| link      | object | no        | the URL that should goto when users tap the native ads             |

#### native.title

| parameter | type   | mandatory | description      |
| --------- | ------ | --------- | ---------------- |
| text      | string | yes       | content of title |

#### native.img

| parameter | type   | mandatory | description                 |
| --------- | ------ | --------- | --------------------------- |
| url       | string | yes       | URL of image                |
| w         | int    | no        | image width, unit is pixel  |
| h         | int    | no        | image height, unit is pixel |

#### native.data

| parameter | type   | mandatory | description     |
| --------- | ------ | --------- | --------------- |
| label     | string | no        | name of data    |
| value     | string | yes       | content of data |

#### native.Link

| parameter    | type   | mandatory | description                                                                                                                                    |
| ------------ | ------ | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| url          | string | yes       | the URL that should goto when users tap the native ads                                                                                         |
| clicktracker | array  | no        | the tracking URLs when users tap the native ads                                                                                                |
| type         | int    | no        | how to open the url, 1: use webview to open in app, 2: use built-in browser to open, 3: open map; 4: open dial; 5: play video; 6: download app |

> the native ads comply with [OpenRTB Dynamic Native Ads Specification 1.0](http://www.iab.net/media/file/OpenRTB-Native-Ads-Specification-1_0-Final.pdf).

### response

| parameter | type   | mandatory | description                                      |
| --------- | ------ | --------- | ------------------------------------------------ |
| ret       | int    | yes       | result, 0: success, see msg for other situations |
| msg       | string | no        | return detailed info when response failed        |

## get the unapproved material

**url:** /dsp/api/inventory/denylist

```json

    {
        "dsp_token":"",
        "upload_date":"2015-01-01"
    }
```

| parameter | type | mandatory | description |
| --------- | ---- | --------- |-- |
| dsp_token   | string | yes  | you can find it on our dashboard or contact our account manager to get it  |
| upload_date | string | no  | the start date for checking, will return all of unapproved material since upload date. it means all materials have been approved if return null.  |

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

### response

| parameter | type | mandatory | description |
| --------- | ---- | --------- |-- |
| ret         | int    | yes  | result, 0: success, see msg for other situations |
| msg         | string | no  | return detailed info when response failed      |
| ad_id       | string | yes  | advertising ID, is created by DSP         |
| deny_reason | string | yes  |                  |

## get the auditing status of material

**url:** /dsp/api/inventory/query_review_state

```json

    {
        "dsp_token":"",
        "ads":[
            "1" , "2"
        ]
    }
```

| parameter | type   | mandatory | description                                                               |
| --------- | ------ | --------- | ------------------------------------------------------------------------- |
| dsp_token | string | yes       | you can find it on our dashboard or contact our account manager to get it |
| ads       | array  | yes       | array of advertising ID that you want to query                            |

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

### response

| parameter    | type   | mandatory | description                                                      |
| ------------ | ------ | --------- | ---------------------------------------------------------------- |
| ret          | int    | yes       | result, 0: success, see msg for other situations                 |
| msg          | string | no        | return detailed info when response failed                        |
| ad_id        | string | yes       | advertising ID, is created by DSP                                |
| review_state | int    | yes       | auditing status, 0: waiting to audit, 1: approval, 2: unapproved |
| deny_reason  | string | yes       |                                                                  |

## get the statistics

**url:** /dsp/api/inventory/query_stat_info

```json

    {
        "dsp_token":"",
        "start_time":"",
        "end_time":""
    }
```

| parameter  | type   | mandatory | description                                                               |
| ---------- | ------ | --------- | ------------------------------------------------------------------------- |
| dsp_token  | string | yes       | you can find it on our dashboard or contact our account manager to get it |
| start_time | int    | yes       | unix time of start date, unit is second                                   |
| end_time   | int    | yes       | unix time of end date, unit is second                                     |

```json

    {
        "ret":0,
        "msg":"",
        "stat_info":StatInfo
    }
```

### response

| parameter | type   | mandatory | description                                      |
| --------- | ------ | --------- | ------------------------------------------------ |
| ret       | int    | yes       | result, 0: success, see msg for other situations |
| msg       | string | no        | return detailed info when response failed        |
| stat_info | string | yes       | advertising ID, is created by DSP                |

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

| parameter      | type  | mandatory | description       |
| -------------- | ----- | --------- | ----------------- |
| query_count    | int   | yes       | amount of query   |
| bid_count      | int   | yes       | amount of bid     |
| timeout_count  | int   | yes       | amount of timeout |
| error_count    | int   | yes       | amount of error   |
| win_count      | int   | yes       | amount of win     |
| display_count  | int   | yes       | amount of display |
| click_count    | int   | yes       | amount of click   |
| consume_amount | float | yes       | amount of consume |
