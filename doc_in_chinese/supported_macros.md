# 目前支持的宏

|            字段           |                                         含义                                         |
| ------------------------- | ------------------------------------------------------------------------------------ |
| {AUCTION_BID_ID}          | 竞价ID                                                                               |
| {AUCTION_BID_PRICE}       | 最终结算价格，该价格是被加密的，解密方法请参见[结算价格解析方法](/price_decryption_method.md) |
| {AUCTION_BID_PRICE_NOENC} | 最终结算价格，明文                                                                   |
| {AUCTION_IMP_ID}          | 曝光id                                                                               |
| {AUCTION_IP}              | 用户ip                                                                               |
| {AUCTION_DID_SHA1}        | 请参见[设备](#)didsha1字段                                                           |
| {AUCTION_DPID_SHA1}       | 请参见[设备](#)dpidsha1字段                                                          |
| {AUCTION_IMEI}            | 明文Imei号                                                                           |
| {AUCTION_IMSI}            | 明文Imsi号                                                                           |
| {AUCTION_ANDROID_ID}      | 明文Android Id                                                                       |
| {AUCTION_IDFA}            | 明文Idfa                                                                             |
| {AUCTION_OS}              | 设备类型，ios或android                                                               |
| {AUCTION_APP_ID}          | 应用ID                                                                               |
| {AUCTION_TIMESTAMP}       | GMT unix timestamp, 单位为秒                                                         |
| {AUCTION_CLICK_URL}       | 广告点击跳转URL                                                                      |
| {AUCTION_RANDOM_NUM}      | 随机数，用来保证url不会被客户端缓冲                                                  |

## 上报地址宏替换信息

> 客户端触发上报信息时，会替换点击坐标宏变量，单位为像素。可支持的宏坐标如下：

|           宏变量            |  类型 |      说明     |
| --------------------------- | ----- | ------------- |
| YUMI_ADSERVICE_CLICK_DOWN_X | int32 | 点击落下X坐标 |
| YUMI_ADSERVICE_CLICK_DOWN_Y | int32 | 点击落下Y坐标 |
| YUMI_ADSERVICE_CLICK_UP_X   | int32 | 点击离开X坐标 |
| YUMI_ADSERVICE_CLICK_UP_Y   | int32 | 点击离开Y坐标 |
