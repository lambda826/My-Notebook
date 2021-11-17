如果只有几台physical machine，员工需要提交job到machine来run，如何设计infrastructure。然后后面问如果machine越来越多，需求越来越多怎么办，然后如果有人想run at once，有人想schedule time to ‍‍‌‌‍‌‌‌‍‍‌‍‌‍‌‌‍‌run，怎么handle，然后如果job提交到一半，服务器炸了，怎么保证transactional（这个地方问得很细，需要吧handle的逻辑都说清楚），然后怎么避免single point of failure。 这轮整体上是一个由简到难的design，涉及到很多东西，比如autoscaling，distributed system structure等等

<!--stackedit_data:
eyJoaXN0b3J5IjpbODQ5NzIyNDIyXX0=
-->