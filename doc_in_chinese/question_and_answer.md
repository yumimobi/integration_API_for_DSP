# 常见问题

## Q：流量测试，投放过程中为什么没有收到流量？

A：登录玉米 ADX 客户后台，查询以下几项：

1. 竞价请求的地址是否填写；

2. 请求流量的 QPS 是否填写；

3. 广告类型及尺寸是否勾选；

4. 设备类型，网络连接类型，操作系统类型是否勾选。

以上项目 check 完毕，如果还未收到流量，请联系相关运营人员。

## Q：为什么所收到的流量突然少了？

A：请 check 以下项：

1. 登陆后台看超时率是否比较高；

2. 查看 QPS 是否有调整；

3. QPS 根据广告投放进行自动调节，查看投放是否有减少，投放减少 QPS 自动降低

以上项目 check 完毕，如果还未收到流量，请联系相关运营人员。

## Q: 如何判断请求的广告类型是什么？

A: 有两种方法判断：

1. 排除法

- bidrequest 里有 video 对象，就是视频广告。

- 有 native 对象，就是原生广告。

- 两者都不是的时候，看 imp 对象的 instl 标志，为 true，且 IsSplashScreen 扩展为真就是开屏，即 instl=true and extensions[is_splash_screen]=true 开屏；

- instl 为真，但 IsSplashScreen 为 false，则为插屏，即 instl=true and extensions[is_splash_screen]=false 插屏；

- instl 为 false 则是普通 banner， 即 instl=false banner；

2. 读取 BidRequest.Imp.Ext.ad_type 字段，根据该字段的值确定广告位类型，0：banner，1：插屏，2：开屏，3：原生，4：视频；255：unknown。
