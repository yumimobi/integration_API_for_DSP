# 沙盒面板使用指南

沙盒是用于DSP在测试协议使用的工具。

登录地址：http://sandbox.dspcp.adx.yumimobi.com

账号和密码与商务开通的账号、密码一致

## 操作步骤

1. 添加请求接收地址

    ![url setting](/img/url_seeting.png)

2. 创建请求

    ![steps of testing](/img/test_step.png)

    点击第一步，即可进入请求设置界面

    ![create request](/img/new_req.png)

    在这里，可设置广告形式、物料格式；如果要支持广告位定向，可在广告位id处填写，以便测试.

3. 发起请求

    ![step of testing](/img/test_step.png)

    点击第二步，即可发起测试请求

## 说明

1. 在沙盒测试，广告形式需要使用如下判断逻辑：

    bidrequest里有video对象，就是视频广告。有native对象，就是原生广告。两者都不是的时候，看imp对象的instl标志，为true，且IsSplashScreen扩展为真就是开屏；instl为真，但IsSplashScreen为false，则为插屏。instl为false则是普通banner。

    （instl=false banner；instl=true and extensions[is_splash_screen]=false 插屏；instl=true and extensions[is_splash_screen]=true 开屏）

2. 沙盒的面板不显示拓展字段，但对请求和返回解析没有影响。
