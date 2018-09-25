# QUESTIONS AND ANSWER

## Q: why don't I receive the requests when I'm testing the integration

A：please login YUMI dashboard and check following settings:

1. the URL of request is correct;

2. QPS of request have been filled in;

3. types and sizes of slot are selected;

4. device type, connection type or OS type have been selected.

please contact our account manager if you still not receive the request when the above settings are set correctly.

## Q：why do the requests I received decreased suddenly

A：please login YUMI dashboard and check following settings:

1. whether time-out rate is higher than normal;

2. whether QPS was modified;

3. check whether the responses are decreasing because QPS will decrease automatically according the number of response.

please contact our account manager if you still not receive the request when the above settings are set correctly.

## Q: how to judge which ad_type that request is

A: there are two ways to judge:

1. excluding method

The slot type is rewarded video as long as there has video object in request or is native as long as there has native object in request.

If not, the slot type depends on the parameter instl that is in imp object. If the instl and IsSplashScreen are both true, the slot type is splash; if the instl is true and IsSplashScreen is false, th slot type is interstitial.

if instl is false, the slot type is banner.

2. judge ad_type according the value of parameter `BidRequest.Imp.Ext.ad_type`, 0:banner, 1:interstitial, 2:splash, 3:native, 4:rewarded video; 255:unknown.
