# Reference
[Grokking the System Design Interview - Designing Pastebin](https://www.educative.io/courses/grokking-the-system-design-interview/3jyvQ3pg6KO)
[system-design-primer - pastebin](https://github.com/donnemartin/system-design-primer/tree/master/solutions/system_design/pastebin)

---

# Introduction
## What is Pastebin?
Pastebin like services enable users to store plain text or images over the network (typically the Internet) and generate unique URLs to access the uploaded data.
Such services are also used to share data over the network quickly, as users would just need to pass the URL to let other users see it.

## Key Words
Tiny URL
Read heavy

---

# Requirements
## **Functional**
* (**Write**) Paste/upload the text.
* (**Write**) Generate a unique key (TinyURL) for accessing the data.
* (**Read**) When users access a key (TinyURL), the service should return the content.
* (**Clean up**) Links will expire after a default/specific timespan.

## **Non-Functional**
* Highly available
* Low latency

---

# Estimation
## **Traffic**
* Read : Write = 10 : 1
* 1 Million new URL per day (Write)
* Write Operation Per Sec = 1M / (24 * 3600) = ~ 10/s
* QPS = (Read/Write ratio) * (Write Operation Per Sec) = 10* 10= 100/s

## **Storage**
* Assume we store paste for 6 Months
* Total URL to store = (1M per day) * 30 * (6 Month) = ~200M
* Assume each entry takes 10 MB
* Total Storage 10MB * 200M = 2PB (without replica)

---

# High Level Design
![Pastebin](https://img-blog.csdnimg.cn/ecf8128ab3e04baa9f5e7364cc33bb36.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16)

[Draw IO source](https://app.diagrams.net/#G1QDCn_a2GQOuDEpGrKCEZ_Sy_0jvfmo5Q)

---

# Follow-up
How to enssure unique keys?
* Generating keys offline and store them in the database.

How to improve performance?
* Preload part of keys in to service memory.
* Apply hash based sharding on keys.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0MDc2NDE2OTldfQ==
-->