# 微信朋友圈高性能复杂度分析



## 背景信息

https://www.yicai.com/news/100920319.html *2021-01-19*

> 张小龙披露微信最新数据：目前有 10.9 亿用户打开微信，3.3 亿用户进行了视频通话；有 **7.8 亿用户进入朋友圈，1.2 亿用户发表朋友圈**，其中照片 6.7 亿张，短视频 1 亿条；有 3.6 亿用户读公众号文章，4 亿用户使用小程序。

https://www.phdmedia.com/phd-insight-wechat-infographic/ *2019-03-26*

一天内微信使用量分布图：

![](https://github.com/yifeisg/thinking-in-architecture/blob/main/week02/wechat_usage_during_a_day.jpg)

为了便于计算，我们将上面的折线图粗略转化为以下直方图：

![](https://github.com/yifeisg/thinking-in-architecture/blob/main/week02/wechat_usage_histogram.jpg)

假设 7.8 亿用户平均每人每天进入 3 次朋友圈，则朋友圈平均每天一共有 23.4 亿次访问。

其中， 峰值出现于 8pm - 9pm，在这 1 小时里一共发生了总访问量的大约 8.5%，也就是约 2 亿次访问。

假设特殊时期（如除夕）朋友圈访问量是平时均值的 5 倍，则此时每小时约有 10 亿次访问。

假设这些访问量平均分布于这一小时中的每一秒，则折合到每一秒，看朋友圈的 **QPS 约为 28 万**。

在同样的假设前提下，按照此方法对发表朋友圈的用户做出估算，可以得到发朋友圈的 **TPS 约为 3.5 万**。

