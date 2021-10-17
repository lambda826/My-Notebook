# Reference
[Grokking the System Design Interview - Designing a URL Shortening service like TinyURL](https://www.educative.io/courses/grokking-the-system-design-interview/m2ygV4E81AR)

# Introduction
URL shortening is used to create shorter aliases for long URLs.
We call these shortened aliases “short links.”
Users are redirected to the original URL when they hit these short links.

## Key Words
Read heavy
Base64 encoding
Shard on TinyURL


# Requirements

## **Functional**
(**Write**) Given a URL, our service should generate a shorter and unique alias of it.
(**Read**) When users access a short link, our service should redirect them to the original link.
(**Clean up**) Links will expire after a default/specific timespan.

## **Non-Functional**
Highly available
Low latency


# Estimation
## **Traffic**
* Read : Write = 100 : 1
* 500M new URL per Month (Write)
* Write Operation Per Sec = 500M / (30 * 24 * 3600) = ~ 200 URL/s
* QPS = (Read/Write ratio) * (Write Operation Per Sec) = 100 * 200 = 20K/s

## **Storage**
* Assume we store URLs for 6 Months
* Total URL to store = (500M per Month) * (6 Month) = 3B
* Assume each entry takes 100 Bytes
* Total Storage 3B * 100 Bytes = 0.3b * 1KB = 0.3 TB (without replica)


# High Level Design
![在这里插入图片描述](https://img-blog.csdnimg.cn/657324cb418d416d9c541685732df532.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
[Draw IO source](https://drive.google.com/file/d/1PjE7Zju74thAiUTQulFoHAwmXsRlMAtv/view?usp=sharing)

# Follow-up
How to enssure unique generated Tiny URL?
* Generating Tiny URLs offline and store them in the database. Grab a TinyURL whenever there is a request for generation.

How to improve performance?
* Preload part of keys in to service memory.
* Apply hash based sharding on Tiny URL.
* Add cache for retrieving original URL given Tiny URL.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU5NDc3MTg2NCwxNzY4MjEwNTY1XX0=
-->