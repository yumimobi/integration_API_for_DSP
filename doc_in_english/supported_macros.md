# AVAILABLE MACROS

|            parameter           |                                         description                                         |
| ------------------------- | ------------------------------------------------------------------------------------ |
| {AUCTION_BID_ID}          | auction ID                                                                               |
| {AUCTION_BID_PRICE}       | billable price by encrypted, view [decrypted method](price_decryption_method.md) |
| {AUCTION_BID_PRICE_NOENC} | billable price by non-encrypted                                                                   |
| {AUCTION_IMP_ID}          | impression id                                                                               |
| {AUCTION_IP}              | user ip                                                                               |
| {AUCTION_DID_SHA1}        | device ID encrypted using SHA1, in Android device, the value should be IMEI; in CDMA device, the value should be meid; in iOS device, the value should be null                                                           |
| {AUCTION_DPID_SHA1}       | in Android device, the value should be ANDROID ID encrypted by SHA1; in iOS device, the value is ADID(also called by IDFA) encrypted by SHA1, such as "8a319e9fdf05dd8f571b6e0dc2dc2a8263a6974b"                                                          |
| {AUCTION_IMEI}            | imei by non-encrypted                                                                        |
| {AUCTION_IMSI}            | imsi by non-encrypted                                                                           |
| {AUCTION_ANDROID_ID}      | Android Id by non-encrypted                                                                      |
| {AUCTION_IDFA}            | idfa by non-encrypted                                                                             |
| {AUCTION_OS}              | operation system, iOS or Android                                                               |
| {AUCTION_APP_ID}          | application ID                                                                               |
| {AUCTION_TIMESTAMP}       | GMT unix timestamp, unit is second                                                         |
| {AUCTION_CLICK_URL}       | jumping URL when user taps the ads                                                                     |
| {AUCTION_RANDOM_NUM}      | random number, to make sure that URL don't is cached by client server.                                                  |

## coordinate macros in tracking URL

> the following macros will be substituted when the tracking URL is reported from client server. the unit of macros is pixel.

|           marco            |  type |      description     |
| --------------------------- | ----- | ------------- |
| YUMI_ADSERVICE_CLICK_DOWN_X | int32 | x-coordinate of               |
| finger pressing             |
| YUMI_ADSERVICE_CLICK_DOWN_Y | int32 | y-coordinate of               |
| finger pressing            |
| YUMI_ADSERVICE_CLICK_UP_X   | int32 | x-coordinate of finger rising |
| YUMI_ADSERVICE_CLICK_UP_Y   | int32 | y-coordinate of finger rising |
