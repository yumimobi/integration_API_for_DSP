# Price decryption method

The price that you will be received is encrypted and you need a key to decrypt the price. Please contact our account manager to get your key. Please keep the key safely when you get it.

## Constraint variable

|          parameter         |                                 description                                 |
| --------------------- | -------------------------------------------------------------------- |
| P\ :sub:`settle`      | origin price                                                             |
| P\ :sub:`encrpt`      | encrypt price                                                           |
| d_key                 | key for decryption, 32 Byte                                                   |
| i_key                 | complete key, 32 Byte                                                   |
| time_stamp            | Unix time                                                               |
| integrity             | complete signature                                                        |
| side_word             | jamming code of price encrypted, 8 Byte                                                |
| \+                    | string concatenation                                                        |
| \^                    | exclusive or                                                                 |
| WebSafeBase64Encode() | standard base64 encoding（RFC2045），replace “+” with “-” and replace “/” with “_”, and will omit the padded character |
| WebSafeBase64Decode() | standard base64 encoding（RFC2045）, replace “-” with “+” and replace “_” with “/”, and fill in character |
| E\ :sub:`enc`         | the string that have encrypted                                                  |
| E\ :sub:`src`         | the string before encryption                                                             |

## Steps of decryption

* 原始密文E\ :sub:`src` 右端补齐'=' 直到字符串长度为4的倍数为止

* 用WebSafeBase64Decode解码该字符串，结果应为长度16字节的数据

    数据格式如下:

    | time_stamp(4) | P\ :sub:`encrpt`(8) | integrity(4)

    | 其中time_stamp 为小字节字序的int32 值，是加密价格时的unix time stamp。

* 使用秘钥d_key对time_stamp, 进行如下操作

    | mac = hmac.New(sha1.New, d_key)

    | mac.Write(time_stamp)

    | side_word = mac.Sum(nil)[:8]

* 将P\ :sub:`encrpt` 与side_word进行按字节异或操作， 得到值既为P\ :sub:`settle` , 是小字节字序的float64值， 单位为分

## 校验步骤

* 将P\ :sub:`settle` 与time_stamp按小字节字序合并为12字节的数据， 用i_key进行如下操作

    | mac = hmac.New(sha1.New, i_key)

    | mac.Write(P\ :sub:`settle` + time_stamp) （并不是数字的相加，而是合并为12字节的数据）

    | result = mac.Sum(nil)[:4]

* 将上一步骤得出的结果，与integrity进行比较， 相等表示校验成功，否则失败。
