### 结算价格解析方法

DSP 获取到的结算价格,是经过加密后的结算价格，每个 DSP 有一个唯一的结算价格解密密钥，请联系 Zplay Adx 团队获取,并妥善保管。

#### 约束变量

|          字段         |                                 含义                                 |
| --------------------- | -------------------------------------------------------------------- |
| P\ :sub:`settle`      | 原始价格                                                             |
| P\ :sub:`encrpt`      | 加密的价格                                                           |
| d_key                 | 解密密匙，32字节                                                     |
| i_key                 | 完整性密匙，32字节                                                   |
| time_stamp            | 时间戳                                                               |
| integrity             | 完整性签名                                                           |
| side_word             | 价格加密干扰码，8字节                                                |
| \+                    | 字符串连接                                                           |
| \^                    | 异或                                                                 |
| WebSafeBase64Encode() | 标准base64 编码（RFC2045），替换“+”为“-”；“/”为“_”，会省略填补的字符 |
| WebSafeBase64Decode() | 标准base64 编码（RFC2045），需要替换“-”为“+”；“_”为“/”，并填补占位符 |
| E\ :sub:`enc`         | 加密后的密文                                                         |
| E\ :sub:`src`         | 原始密文                                                             |


#### 解密步骤：

*  原始密文E\ :sub:`src` 右端补齐'=' 直到字符串长度为4的倍数为止

*  用WebSafeBase64Decode解码该字符串，结果应为长度16字节的数据

    数据格式如下:

    | time_stamp(4) | P\ :sub:`encrpt`(8) | integrity(4)

    | 其中time_stamp 为小字节字序的int32 值，是加密价格时的unix time stamp。


*  使用秘钥d_key对time_stamp, 进行如下操作

    | mac = hmac.New(sha1.New, d_key)

    | mac.Write(time_stamp)

    | side_word = mac.Sum(nil)[:8]

*  将P\ :sub:`encrpt` 与side_word进行按字节异或操作， 得到值既为P\ :sub:`settle` , 是小字节字序的float64值， 单位为分

#### 校验步骤


* 将P\ :sub:`settle` 与time_stamp按小字节字序合并为12字节的数据， 用i_key进行如下操作

    | mac = hmac.New(sha1.New, i_key)

    | mac.Write(P\ :sub:`settle` + time_stamp) （并不是数字的相加，而是合并为12字节的数据）

    | result = mac.Sum(nil)[:4]
    
* 将上一步骤得出的结果，与integrity进行比较， 相等表示校验成功，否则失败。

