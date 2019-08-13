# JOSN 请求和返回示例

> 示例只适用于 json 协议，系统默认对接都是 pb 协议，如果要使用以下示例，请在对接前予以说明（否则，下方对接示例不可用）

- [JOSN 请求和返回示例](#josn-%E8%AF%B7%E6%B1%82%E5%92%8C%E8%BF%94%E5%9B%9E%E7%A4%BA%E4%BE%8B)
	- [banner](#banner)
		- [banner 请求示例](#banner-%E8%AF%B7%E6%B1%82%E7%A4%BA%E4%BE%8B)
		- [banner 返回示例](#banner-%E8%BF%94%E5%9B%9E%E7%A4%BA%E4%BE%8B)
		- [banner 深度唤醒返回示例, 其他广告形式和这个类似](#banner-%E6%B7%B1%E5%BA%A6%E5%94%A4%E9%86%92%E8%BF%94%E5%9B%9E%E7%A4%BA%E4%BE%8B-%E5%85%B6%E4%BB%96%E5%B9%BF%E5%91%8A%E5%BD%A2%E5%BC%8F%E5%92%8C%E8%BF%99%E4%B8%AA%E7%B1%BB%E4%BC%BC)
	- [插屏](#%E6%8F%92%E5%B1%8F)
		- [插屏请求示例](#%E6%8F%92%E5%B1%8F%E8%AF%B7%E6%B1%82%E7%A4%BA%E4%BE%8B)
		- [插屏返回示例](#%E6%8F%92%E5%B1%8F%E8%BF%94%E5%9B%9E%E7%A4%BA%E4%BE%8B)
    - [插屏视频返回示例](#插屏视频返回示例)
	- [原生](#%E5%8E%9F%E7%94%9F)
		- [原生请求示例](#%E5%8E%9F%E7%94%9F%E8%AF%B7%E6%B1%82%E7%A4%BA%E4%BE%8B)
		- [原生返回示例](#%E5%8E%9F%E7%94%9F%E8%BF%94%E5%9B%9E%E7%A4%BA%E4%BE%8B)
	- [激励视频](#%E6%BF%80%E5%8A%B1%E8%A7%86%E9%A2%91)
		- [激励视频adm返回示例](#激励视频返回adm参数示例)
    - [激励视频请求示例](#激励视频请求示例)
    - [激励视频返回示例](#激励视频返回示例)

## banner

### banner 请求示例

```json
{
  "id": "0bum3G1CQfE440EQrP0tUPoy3MGFhC",
  "imp": [
    {
      "id": "1",
      "banner": {
        "w": 640,
        "h": 100,
        "pos": 0
      },
      "instl": false,
      "tagid": "zapf49b17bbd2a551e478a485a3a82e052fd6f5652c",
      "bidfloor": 130,
      "bidfloorcur": "CNY",
      "ext": {
        "inventory_typs": [1, 2, 4, 5],
        "ad_type": 0,
        "tag_name": "广告位名称"
      }
    }
  ],
  "app": {
    "id": "1000481",
    "name": "国内-安卓-消灭星星官方正版",
    "ver": "4.5.1",
    "bundle": "com.brianbaek.popstar"
  },
  "device": {
    "dnt": false,
    "ua": "Dalvik/2.1.0(Linux;U;Android5.1.1;vivoY31ABuild/LMY47V)",
    "ip": "223.104.171.147",
    "geo": {
      "lat": 27.970472,
      "lon": 116.34153,
      "country": "CHN",
      "region": "北京",
      "city": "北京",
      "type": 2,
      "ext": {
        "accu": 0
      }
    },
    "didsha1": "5d3b81d9b4fc532586410026835dc35f93697695",
    "dpidsha1": "558d608a909c114d03536b28300e48d98dcd0abb",
    "make": "vivo",
    "model": "vivoY31A",
    "os": "android",
    "osv": "5.1.1",
    "w": 540,
    "h": 960,
    "ppi": 240,
    "connectiontype": 6,
    "devicetype": 4,
    "macsha1": "4c647a8d9efd629cd238c9c0dc3c7928b1aa8671",
    "ext": {
      "plmn": "46002",
      "imei": "862262030529799",
      "imsi": "460029329554417",
      "mac": "9c:a5:c0:cb:0a:e7",
      "android_id": "b130955d7ef56ed4",
      "adid": "",
      "orientation": 1
    }
  },
  "ext": {
    "version": 1,
    "need_https": false
  }
}
```

### banner 返回示例

```json
{
  "id": "0bts0K1CQgtF0zJA6R1ZzppG4CJ3b4",
  "seatbid": [
    {
      "bid": [
        {
          "id": "27170321175320259213",
          "impid": "27170321175320259213",
          "price": 0.1,
          "adid": "ac990ea25bca7474c2553679e3dd33c6",
          "w": 640,
          "h": 100,
          "iurl": "http://img.pxene.com/dav/65d106ff-2cb9-4ae7-a2d8-897fe3f05f64/image/37f5e37fb84945bcb4f29bdb6dbce990.jpg",
          "adm": "",
          "ext": {
            "clkurl": "http://e.cn.mozhen.com/r/k=2038947&p=75Y7B&dx=__IPDX__&rt=2&ns=183.16.2.121&ni=__IESID__&v=__LOC__&xa=__ADPLATFORM__&ro=sm&mo=0&m479b824d9a1fd&m2=b2196f839dae8187e6b2c1931ca847f6&m4=__AAID__&m5=__IDFA__&m6=__MAC1__&m6a=__MAC__&o=http://site.pxene.com/minisiteWap/Accord_3h/",
            "imptrackers": [
              "http://sapi.wobile.com/phone/notify.php?act=show&log=dspid%3D101%26uniplayid%3D1636400010%26rid%3D27170321175320259213%26adiplay.6%3D1%26slotd%3Dbanner%26ads%3D640x100%26sdkv%3D6%26ts%3D14900900%26ip%3D183.16.2.121",
              "http://open.aview.cn/agent/openDisplay.do?st=0&uuidEncType=0&sv=0&b4790f0cc46f1fdd6facee9bc1845&aid=SDK201616090411451r7ykol3qo7e0ou&ro=1&ca=0",
              "http://ip2.pxene.comapid=d2495550-d1a0-4fde-81d4-fdc634451a36&depid=e1aa0807c3d23e49311b73a3580dd77a&nw=1&os=2&tp=1&reqip=183.16.2.121&gp=1156440300&mb=3&op=1&md=MI+3",
              "http://g.cn.miaozhen.com/x/k=2038947&p=75Y7B&dx=__IPDX__&rt=2&ns=183.16.2.1__IESID__&v=__LOC__&xa=__ADPLATFORM__&mo=0&m0=__OPE006479b824d9a1fd&m2=b2196f839dae8187e6b2c1931ca847f6&m4=__AAID__&m5=__IDFA__&m6=__MAC1__&m6a=__MAC__&o="
            ],
            "clktrackers": [
              "http://api.wanzhu.SDK201616090411451r7ykol3qo7e0ou%26wzid%3D1010009%26pkg%3Dcom.zplay.migupopstar.mi%26did%3D5c8ade2b7a03613126opt%3D46000%26plt%3D1%26slotid%3Dbanner%26ax100%26sdkv%3D6%26ts%3D1490090000%26ip%3D183.16.2.121",
              "http://open.advew.cn/aid=SDK201616090411451r7ykol3qo7e0ou&ro=1&ca=0",
              "http://cl2.pxene.com/ic?adx=14&bid=20170321-175320_bidreq_130-1030-NGzw-591&mtype=c&mapid=d2495550-d1a0-4fde-81d4-fdc6344dtype=97&appi23e49311b73a3580dd77a&nw=1&os=2&tp=1&reqip=183.16.2.121&gp=1156440300&mb=3&op=1&md=MI+3&url="
            ],
            "title": "",
            "desc": "",
            "action": 1,
            "html_snippet": "",
            "inventory_type": 1
          }
        }
      ]
    }
  ]
}
```

### banner 深度唤醒返回示例, 其他广告形式和这个类似

```json
{
  "id": "0bts0K1CQgtF0zJA6R1ZzppG4CJ3b4",
  "seatbid": [
    {
      "bid": [
        {
          "id": "27170321175320259213",
          "impid": "27170321175320259213",
          "price": 0.1,
          "adid": "ac990ea25bca7474c2553679e3dd33c6",
          "w": 640,
          "h": 100,
          "iurl": "http://img.pxene.com/dav/65d106ff-2cb9-4ae7-a2d8-897fe3f05f64/image/37f5e37fb84945bcb4f29bdb6dbce990.jpg",
          "adm": "",
          "ext": {
            "clkurl": "taobao://item.taobao.com/item.htm?id=44014690052",
            "imptrackers": [
              "http://sapi.wobile.com/phone/notify.php?act=show&log=dspid%3D101%26uniplayid%3D1636400010%26rid%3D27170321175320259213%26adiplay.6%3D1%26slotd%3Dbanner%26ads%3D640x100%26sdkv%3D6%26ts%3D14900900%26ip%3D183.16.2.121",
              "http://open.aview.cn/agent/openDisplay.do?st=0&uuidEncType=0&sv=0&b4790f0cc46f1fdd6facee9bc1845&aid=SDK201616090411451r7ykol3qo7e0ou&ro=1&ca=0",
              "http://ip2.pxene.comapid=d2495550-d1a0-4fde-81d4-fdc634451a36&depid=e1aa0807c3d23e49311b73a3580dd77a&nw=1&os=2&tp=1&reqip=183.16.2.121&gp=1156440300&mb=3&op=1&md=MI+3",
              "http://g.cn.miaozhen.com/x/k=2038947&p=75Y7B&dx=__IPDX__&rt=2&ns=183.16.2.1__IESID__&v=__LOC__&xa=__ADPLATFORM__&mo=0&m0=__OPE006479b824d9a1fd&m2=b2196f839dae8187e6b2c1931ca847f6&m4=__AAID__&m5=__IDFA__&m6=__MAC1__&m6a=__MAC__&o="
            ],
            "clktrackers": [
              "http://api.wanzhu.SDK201616090411451r7ykol3qo7e0ou%26wzid%3D1010009%26pkg%3Dcom.zplay.migupopstar.mi%26did%3D5c8ade2b7a03613126opt%3D46000%26plt%3D1%26slotid%3Dbanner%26ax100%26sdkv%3D6%26ts%3D1490090000%26ip%3D183.16.2.121",
              "http://open.advew.cn/aid=SDK201616090411451r7ykol3qo7e0ou&ro=1&ca=0",
              "http://cl2.pxene.com/ic?adx=14&bid=20170321-175320_bidreq_130-1030-NGzw-591&mtype=c&mapid=d2495550-d1a0-4fde-81d4-fdc6344dtype=97&appi23e49311b73a3580dd77a&nw=1&os=2&tp=1&reqip=183.16.2.121&gp=1156440300&mb=3&op=1&md=MI+3&url="
            ],
            "title": "",
            "desc": "",
            "action": 7,
            "html_snippet": "",
            "inventory_type": 1,
            "fallback_url": "http://e.cn.mozhen.com/r/k=2038947&p=75Y7B&dx=__IPDX__&rt=2&ns=183.16.2.121&ni=__IESID__&v=__LOC__&xa=__ADPLATFORM__&ro=sm&mo=0&m479b824d9a1fd&m2=b2196f839dae8187e6b2c1931ca847f6&m4=__AAID__&m5=__IDFA__&m6=__MAC1__&m6a=__MAC__&o=http://site.pxene.com/minisiteWap/Accord_3h/",
            "fallback_action": 2
          }
        }
      ]
    }
  ]
}
```

## 插屏

### 插屏请求示例

```json
{
  "id": "0bum1K1CQfE62Ae9r23W91zl4bip18",
  "imp": [
    {
      "id": "1",
      "banner": {
        "w": 720,
        "h": 1080,
        "pos": 0
      },
      "instl": true,
      "tagid": "zapf7e40c242176f01fd5db1af86146a6de00dde23b",
      "bidfloor": 800,
      "bidfloorcur": "CNY",
      "ext": {
        "is_splash_screen": true,
        "inventory_types": [1,2,3,4,5,7],
        "ad_type": 1,
        "tag_name": "广告位名称"
      }
    }
  ],
  "app": {
    "id": "1007875",
    "name": "QueryViolations",
    "ver": "",
    "bundle": "cn.eclicks.wzsearch"
  },
  "device": {
    "dnt": false,
    "ua": "Mozilla/5.0(Linux;Android6.0.1;OPPOR9sBuild/MMB29M;wv)AppleWebKit/537.36(KHTML,likeGecko)Version/4.0Chrome/46.0.2490.76MobileSafari/537.36",
    "ip": "117.173.83.146",
    "geo": {
      "lat": 31.359089,
      "lon": 103.49656,
      "country": "CHN",
      "region": "四川",
      "city": "成都",
      "type": 2,
      "ext": {
        "accu": 0
      }
    },
    "didsha1": "88206dfa4841569b3b61f27a3775d030cd6104c2",
    "dpidsha1": "1592348a810c27d651b5ef8290e50e7514da2502",
    "make": "",
    "model": "OPPOR9s",
    "os": "android",
    "osv": "6.0.1",
    "w": 1080,
    "h": 1920,
    "ppi": 480,
    "connectiontype": 2,
    "devicetype": 4,
    "macsha1": "c1976429369bfe063ed8b3409db7c7e7d87196d9",
    "ext": {
      "plmn": "46001",
      "imei": "864083031808612",
      "imsi": "",
      "mac": "02:00:00:00:00:00",
      "android_id": "705cce10d9d051a8",
      "adid": "",
      "orientation": 1
    }
  },
  "ext": {
    "version": 1,
    "need_https": false
  }
}
```

### 插屏返回示例

```json
{
    "id": "0bsZ061CQfE403tMax38YlB71cvWlH",
    "seatbid": [
        {
            "bid": [
                {
                    "id": "3e56c4f0b81b470196f671c96e1be5d9",
                    "impid": "1",
                    "price": 1100,
                    "adid": "370",
                    "nurl": "http://dsptracke.ad-ex.com/winnotice?requestid=0bsZ061CQfE403tMax38YlB71cvWlH&adgr104.108.146&app_name=VLife&material_type=banner",
                    "adomain": [
                        "http://www.adidas.com.cn/"
                    ],
                    "bundle": "",
                    "iurl": "http://res.ad-mex1.com/dspres/upload/20170307/88b58192-c86a-43dc-a4c2-69a5bd84f820.jpg",
                    "cid": "18",
                    "crid": "370",
                    "w": 640,
                    "h": 960,
                    "ext": {
                        "imptrackers": [
                            "http://g.cn.miazhen.com/x/k=2039081&p=75VMG&dx=__IPDX__&rt=2&ns=223.104.108.146&ni=__IESID__&v=__LOC__&xa=__ADPLATFORM__&mo=0&m0=__OPENUDID__&m0a=__DUID__&m1=bbd424977f85c210&m1a=__ANDROIDID__&m2=0f11e9b670e033f52da2e3a910523cf0&m4=__AAID__&m5=__IDFA__&m6=__MAC1__&m6a=__MAC__&o=",
                            "http://dsptrack.ad-me.com/adImp?requestid=0bsZ061CQfE403tMax38YlB71cvWlvlife&ip=223.104.108.146&app_name=VLife&material_type=banner&price={AUCTION_BID_PRICE}"
                        ],
                        "clktrackers": [
                            "http://e.cn.miazhen.com/r/k=2039081&p=75VMG&dx=__IPDX__&rt=2&ns=__IP__&ni=__IESID__&v=__LOC__&xa=__ADPLATFORM__&vo=32d0b8d2a&vr=2&o=http%3A%2F%2Fad.yoho.cn%2Fhtml5%2F2017%2F02%2Fadidas%2Findex.html",
                            "http://dsptrackhp=223.104.108.146&app_name=VLife&material_type=banner"
                        ],
                        "clkurl": "http://ad.yoho1.cn/html5/2017/02/adidas/index.html",
                        "inventory_type": 1
                    }
                }
            ]
        }
    ]
}
```

### 插屏视频返回示例

```json
{
    "id": "0bsZ061CQfE403tMax38YlB71cvWlH",
    "seatbid": [
        {
            "bid": [
                {
                    "id": "3e56c4f0b81b470196f671c96e1be5d9",
                    "impid": "1",
                    "price": 1100,
                    "adid": "370",
                    "nurl": "http://dsptrack.ad-ex.com/winnotice?requestid=0bsZ061CQfE403tMax38YlB71cvWlH&adgr104.108.146&app_name=VLife&material_type=banner",
                    "adomain": [
                        "http://www.adidas.com.cn/"
                    ],
                    "bundle": "",
                    "iurl": "http://res.ad-mex.com/dspres/upload/20170307/88b58192-c86a-43dc-a4c2-69a5bd84f820.jpg",
                    "cid": "18",
                    "crid": "370",
                    "w": 640,
                    "h": 960,
                    "adm": "<VAST version=\"3.0\"><VAST version=\"2.0\"><Ad id=\"12345\"><InLine><AdSystem version=\"1.0\">samplechange</AdSystem><AdTitle><![CDATA[Sample VAST]]></AdTitle><Impression>http://sample.com</Impression><Description><![CDATA[A sample VAST feed]]></Description><Creatives><Creative sequence=\"1\" id=\"1\"><Linear><Duration>00:00:30</Duration><TrackingEvents><Tracking event=\"start\">https://start.1</Tracking><Tracking event=\"complete\">https://complete.1</Tracking></TrackingEvents><VideoClicks><ClickThrough><![CDATA[http://click.1]]></ClickThrough></VideoClicks><MediaFiles><MediaFile delivery=\"progressive\" bitrate=\"256\" width=\"640\" height=\"480\" type=\"video/mp4\"><![CDATA[http://sample.com/video.mp4]]></MediaFile></MediaFiles></Linear></Creative></Creatives></InLine></Ad></VAST>",
                    "ext": {
                        "imptrackers": [
                            "http://g.cn.miazhen.com/x/k=2039081&p=75VMG&dx=__IPDX__&rt=2&ns=223.104.108.146&ni=__IESID__&v=__LOC__&xa=__ADPLATFORM__&mo=0&m0=__OPENUDID__&m0a=__DUID__&m1=bbd424977f85c210&m1a=__ANDROIDID__&m2=0f11e9b670e033f52da2e3a910523cf0&m4=__AAID__&m5=__IDFA__&m6=__MAC1__&m6a=__MAC__&o=",
                            "http://dsptrack.ad-mex.com/adImp?requestid=0bsZ061CQfE403tMax38YlB71cvWlvlife&ip=223.104.108.146&app_name=VLife&material_type=banner&price={AUCTION_BID_PRICE}"
                        ],
                        "clktrackers": [
                            "http://e.cn.miazhen.com/r/k=2039081&p=75VMG&dx=__IPDX__&rt=2&ns=__IP__&ni=__IESID__&v=__LOC__&xa=__ADPLATFORM__&vo=32d0b8d2a&vr=2&o=http%3A%2F%2Fad.yoho.cn%2Fhtml5%2F2017%2F02%2Fadidas%2Findex.html",
                            "http://dsptrackhp=223.104.108.146&app_name=VLife&material_type=banner"
                        ],
                        "clkurl": "http://ad.yoho1.cn/html5/2017/02/adidas/index.html",
                        "inventory_type": 3
                    }
                }
            ]
        }
    ]
}
```

## 原生

### 原生请求示例

```json
{
  "id": "39mqjw1CLysK1DEPnF0bRCBk1J5pAa",
  "imp": [
    {
      "id": "1",
      "banner": {
        "w": 448,
        "h": 252,
        "pos": 0
      },
      "tagid": "zap89a83f01f05a7fd761428593a13dd4093c3a5216",
      "bidfloor": 100,
      "bidfloorcur": "CNY",
      "native": {
        "RequestOneof": {
          "RequestNative": {
            "layout": 6,
            "assets": [
              {
                "id": 1,
                "required": true,
                "AssetOneof": {
                  "Title": {
                    "len": 10
                  }
                }
              },
              {
                "id": 3,
                "required": true,
                "AssetOneof": {
                  "Img": {
                    "type": 3,
                    "w": 448,
                    "h": 252
                  }
                }
              },
              {
                "id": 2,
                "required": false,
                "AssetOneof": {
                  "Img": {
                    "type": 2,
                    "w": 100,
                    "h": 100
                  }
                }
              },
              {
                "id": 4,
                "required": true,
                "AssetOneof": {
                  "Data": {
                    "type": 2,
                    "len": 25
                  }
                }
              }
            ]
          }
        }
      },
      "ext": {
        "inventory_types": [6],
        "ad_type": 3,
        "tag_name": "广告位名称"
      }
    }
  ],
  "app": {
    "id": "1007557",
    "name": "快手看片",
    "ver": "",
    "bundle": "com.kandian.vodapp"
  },
  "device": {
    "dnt": true,
    "ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/56.0.2924.87 Safari/537.36",
    "ip": "127.0.0.1",
    "didsha1": "4a73c601fe3127dda8a51ec1e4bc874409e58459",
    "dpidsha1": "d0c6d45541dbf207df6f029dd60255ebc9ccff22",
    "make": "CHM-TL00H",
    "model": "CHM-TL00H",
    "os": "android",
    "osv": "4.4.4",
    "w": 720,
    "h": 1280,
    "ppi": 0,
    "connectiontype": 2,
    "devicetype": 1,
    "macsha1": "",
    "ext": {
      "plmn": "46000",
      "imei": "866329025824802",
      "imsi": "",
      "mac": "",
      "android_id": "e2f7602bff92ced8",
      "adid": "",
      "orientation": 2
    }
  },
  "ext": {
    "version": 1,
    "need_https": false
  }
}
```

### 原生返回示例

```json
{
  "id": "0bts0B1CMf2R43Vd873UcMC705VRrv",
  "seatbid": [
    {
      "bid": [
        {
          "id": "0bts0B1CMf2R43Vd873UcMC705VRrv",
          "adid": "2017030911271377610",
          "impid": "zapdd13a671432d4a653e372fa03b3c68971f788a12",
          "price": 1000,
          "AdmOneof": {
            "AdmNative": {
              "assets": [
                {
                  "id": 3,
                  "img": {
                    "url": "http://img.momocdn.com/ad/F4/17/F417956B-85EF-4CA2-A033-EA8FF0897B54_L.jpg"
                  }
                },
                {
                  "id": 2,
                  "img": {
                    "url": "http://img.momocdn.com/ad/F4/17/F417956B-85EF-4CA2-A033-EA8FF0897B54_L.jpg"
                  }
                },
                 {
                  "id": 4,
                  "data": {
                    "value": "掌游的玉米广告描述信息"
                  }
                },
                {
                  "id": 1,
                  "title": {
                    "text": "掌游天下落地页"
                  }
                }
              ],
              "link": {
                "url": "http://www.baidu.com"
              }
            }
          },
          "ext": {
            "action": 1,
            "imptrackers": [
              "http://test.openad.immomo.com/dsp/zplay/display?tid=0bts0B1C703Hy7Db8DW7Iz8tcp-5SEntL-ansRbe2UqKcPDg7IYFd8s"
            ],
            "clktrackers": [
              "http://test.openad.immomo.com/dsp/zplay/click?tid_PkEvBy4_DRRyZSWEcd6vhogizqCBoLUBPegSZW-rOyicZKz77x-zIgV"
            ],
            "inventory_type": 6
          },
          "nurl": "http://test.openad.immomo.com/dsp/zplay/win?tid=0bts0B1CMf2R43Vd873UE3HvFKz77x-zIgV&price={AUCTION_BID_PRICE}"
        }
      ]
    }
  ]
}
```

## 激励视频

### 激励视频返回adm参数示例

> 视频请求的 inventory_type=3；需要返回 vast 视频和展示图片两部分，展示图片可在 iurl 或者 html_snippet 返回。这里简单给出 adm 的 vast 示例，

```xml
	<VAST>
	  <Ad id="14921137">
	    <InLine>
	      <AdSystem><![CDATA[ yodao dsp ]]></AdSystem>
	      <AdTitle><![CDATA[ video ad ]]></AdTitle>
	      <Description><![CDATA[ video ad ]]></Description>
	      <Creatives>
	        <Creative id="14921137" AdID="14921137" sequence="1">
	          <Linear>
	            <Duration>00:00:12</Duration>
	            <MediaFiles>
	              <MediaFile id="14921137"><![CDATA[ http://live.us.sinaimg.cn/002qTVxrjx074BMTTYSI010401000rFi0k01.mp4 ]]></MediaFile>
	            </MediaFiles>
	            <TrackingEvents>
	              <Tracking event="start"><![CDATA[ http://q105x.cop.yodao.com:8090/impplay.s?ext=Ch4wYnNKZjYxQzU3Wnc0OH%2F%2F%2F%2FwGiAQRXSUZJwgEkYjM1MTM5NDYtOWRmNy00MDhjLTg1YTAtN2M3NzFhMGVlMTJj0gEA2gEFNS4wLjE%3D&event_type=205&play_percent=0.0 ]]></Tracking>
	              <Tracking event="complete"><![CDATA[ http://qt105x.corp.yodao.com:8090/impplay.s?ext=Ch4wYnNKZjYxQzU3Wnc0OHJ4NlUwellINDIyQnFmdDYQyvQPGMO6HiDTnqQCKLHbjgcwdDoOMTA2LjM4LjEyMC4xMTRA%2BeO8lYUrSAFSBDEzNzhaIGJlN2I5MmEt_type=205&play_percent=1.0 ]]></Tracking>
	            </TrackingEvents>
	          </Linear>
	        </Creative>
	      </Creatives>
	    </InLine>
	  </Ad>
	</VAST>
```


### 激励视频请求示例

```json
{
  "id": "0bum1K1CQfE62Ae9r23W91zl4bip18",
  "imp": [
    {
      "id": "1",
      "instl": false,
      "tagid": "zapf7e40c242176f01fd5db1af86146a6de00dde23b",
      "bidfloor": 800,
      "bidfloorcur": "CNY",
      "video":{
        "mimes":["video/mp4"],
        "protocols":[3],
        "minduration": 5,
        "maxduration": 15,
        "w": 640,
        "h": 960,
        "pos": 7,
      },
      "ext": {
        "is_splash_screen": false,
        "inventory_types": [3],
        "ad_type": 4,
        "tag_name": "激励视频广告位名称"
      }
    }
  ],
  "app": {
    "id": "1007875",
    "name": "QueryViolations",
    "ver": "",
    "bundle": "cn.eclicks.wzsearch"
  },
  "device": {
    "dnt": false,
    "ua": "Mozilla/5.0(Linux;Android6.0.1;OPPOR9sBuild/MMB29M;wv)AppleWebKit/537.36(KHTML,likeGecko)Version/4.0Chrome/46.0.2490.76MobileSafari/537.36",
    "ip": "117.173.83.146",
    "geo": {
      "lat": 31.359089,
      "lon": 103.49656,
      "country": "CHN",
      "region": "四川",
      "city": "成都",
      "type": 2,
      "ext": {
        "accu": 0
      }
    },
    "didsha1": "88206dfa4841569b3b61f27a3775d030cd6104c2",
    "dpidsha1": "1592348a810c27d651b5ef8290e50e7514da2502",
    "make": "",
    "model": "OPPOR9s",
    "os": "android",
    "osv": "6.0.1",
    "w": 1080,
    "h": 1920,
    "ppi": 480,
    "connectiontype": 2,
    "devicetype": 4,
    "macsha1": "c1976429369bfe063ed8b3409db7c7e7d87196d9",
    "ext": {
      "plmn": "46001",
      "imei": "864083031808612",
      "imsi": "",
      "mac": "02:00:00:00:00:00",
      "android_id": "705cce10d9d051a8",
      "adid": "",
      "orientation": 1
    }
  },
  "ext": {
    "version": 1,
    "need_https": false
  }
}
```

### 激励视频返回示例

```json
{
    "id": "0bsZ061CQfE403tMax38YlB71cvWlH",
    "seatbid": [
        {
            "bid": [
                {
                    "id": "3e56c4f0b81b470196f671c96e1be5d9",
                    "impid": "1",
                    "price": 1100,
                    "adid": "370",
                    "nurl": "http://dsptrack.ad-ex.com/winnotice?requestid=0bsZ061CQfE403tMax38YlB71cvWlH&adgr104.108.146&app_name=VLife&material_type=video",
                    "bundle": "",
                    "iurl": "http://res.ad-mex.com/dspres/upload/20170307/88b58192-c86a-43dc-a4c2-69a5bd84f820.jpg",
                    "cid": "18",
                    "crid": "370",
                    "w": 640,
                    "h": 960,
                    "adm": "<VAST version=\"3.0\"><VAST version=\"2.0\"><Ad id=\"12345\"><InLine><AdSystem version=\"1.0\">samplechange</AdSystem><AdTitle><![CDATA[Sample VAST]]></AdTitle><Impression>http://sample.com</Impression><Description><![CDATA[A sample VAST feed]]></Description><Creatives><Creative sequence=\"1\" id=\"1\"><Linear><Duration>00:00:30</Duration><TrackingEvents><Tracking event=\"start\">https://start.1</Tracking><Tracking event=\"complete\">https://complete.1</Tracking></TrackingEvents><VideoClicks><ClickThrough><![CDATA[http://click.1]]></ClickThrough></VideoClicks><MediaFiles><MediaFile delivery=\"progressive\" bitrate=\"256\" width=\"640\" height=\"480\" type=\"video/mp4\"><![CDATA[http://sample.com/video.mp4]]></MediaFile></MediaFiles></Linear></Creative></Creatives></InLine></Ad></VAST>",
                    "ext": {
                        "imptrackers": [
                            "http://g.cn.miazhen.com/x/k=2039081&p=75VMG&dx=__IPDX__&rt=2&ns=223.104.108.146&ni=__IESID__&v=__LOC__&xa=__ADPLATFORM__&mo=0&m0=__OPENUDID__&m0a=__DUID__&m1=bbd424977f85c210&m1a=__ANDROIDID__&m2=0f11e9b670e033f52da2e3a910523cf0&m4=__AAID__&m5=__IDFA__&m6=__MAC1__&m6a=__MAC__&o=",
                            "http://dsptrack.ad-mex.com/adImp?requestid=0bsZ061CQfE403tMax38YlB71cvWlvlife&ip=223.104.108.146&app_name=VLife&material_type=banner&price={AUCTION_BID_PRICE}"
                        ],
                        "clktrackers": [
                            "http://e.cn.miazhen.com/r/k=2039081&p=75VMG&dx=__IPDX__&rt=2&ns=__IP__&ni=__IESID__&v=__LOC__&xa=__ADPLATFORM__&vo=32d0b8d2a&vr=2&o=http%3A%2F%2Fad.yoho.cn%2Fhtml5%2F2017%2F02%2Fadidas%2Findex.html",
                            "http://dsptrackhp=223.104.108.146&app_name=VLife&material_type=banner"
                        ],
                        "clkurl": "http://ad.yoho1.cn/html5/2017/02/adidas/index.html",
                        "inventory_type": 3
                    }
                }
            ]
        }
    ]
}
```
