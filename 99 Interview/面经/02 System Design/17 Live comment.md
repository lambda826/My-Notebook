![](https://raw.githubusercontent.com/lambda826/My-Notebook/master/999%20Resource/Live%20Commenting.png)

Notification
push model - connection is maintained
pull model - users send request

viewer-content
write locally, read globally
	Because of our unique situation, we settled on the completely opposite approach: “write locally, read globally.” This meant deploying distributed storage tiers that only handled writes locally, then less frequently collecting information from across all of our data centers to produce the final result. For example, when a user loads his News Feed through a request to our data center in Virginia, the system writes to a storage tier in the same data center, recording the fact that the user is now viewing certain pieces of content so that we can push them new comments. When someone enters a comment, we fetch the viewership information from all of our data centers across the country, combine the information, then push the updates out. In practice, this means we have to perform multiple cross-country reads for every comment produced. But it works because our commenting rate is significantly lower than our viewing rate. Reading globally saves us from having to replicate a high volume of writes across data centers, saving expensive, long-distance bandwidth.

write globally, read locally


https://engineering.fb.com/2011/02/07/core-data/live-commenting-behind-the-scenes/
https://dev.to/kutanti/designing-live-commenting-in-youtube-facebook-instagram-live-stream-video-4bec


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwOTkxNTUzMDksLTE5NDY4NzI0NTAsLT
QyNzc4MzY1MCwxOTcxODk3MjUxLDE5MzA5NDk0OTEsLTE4Njg4
Nzk1MzIsNzMwOTk4MTE2XX0=
-->