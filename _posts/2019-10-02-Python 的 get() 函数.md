---
layout: post
title: Python 的 get() 函数
subtitle: 
date: 2019-10-02 21:49:00
author: Yizhev
catalog: true
archive: ture
  - 
tags:
  - 日常
  - 程序
---

```    python
counts = dict() 
names = ['bob', 'dyan', 'rachel', 'ross', 'bob', 'rachel', 'rachel'] 
for name in names: 
    counts[name] = counts.get(name, 0) + 1 
    print(counts)
```

```python
**输出结果：**
{'bob': 2, 'dyan': 1, 'rachel': 3, 'ross': 1} [Finished in 0.1s]
```

  * **至于这个程序怎么运行：**
  * loop 1:
    * counts is blank
    * counts[bob] = counts.get(bob, 0) + 1
    * 后面的counts一看里面没有bob，返回0
    * 前面的counts就进去一个{‘bob':1}
  * loop 2:
    * counts目前里面有一个bob，计数为1
    * counts[dyan] = counts.get(dyan, 0) + 1
    * 后面的counts其实此时有一个bob,但没有dyan
    * 同样，再加进去一个{dyan':1}
    * 此时的dict里有两个名字
    * 名字作为key，1作为value
  * loop 3:
    * counts目前里面有一个bob和dyan，计数都为1
    * counts[rachel] = counts.get(rachel, 0) + 1
    * 后面的counts其实此时有一个bob和dyan,但没有rachel
    * 那就和上面一样加进去
  * loop 4:
    * 和loop 3 一样再加ross
    * 加完之后就有四个key和对应的value了
  * loop 5：
    * 再一次遇到bob，程序变为
    * counts[bob] = counts.get(bob, 0) + 1
    * 此时bob可以再counts里找到，那么就返回bob这给key对应的value
    * 即为loop 1的最后一段value=1
    * 那么counts.get(bob, 0)返回的值为1, 于是就有了1+1=2，又将2 赋值给了counts[bob]
    * counts[bob] = 2 的意思就是再counts里将key为bob 的value变为2
    * 此处为直接赋值，而非累加。
    * 这个也可以从返回的dict里看出。
    * 之后依次进行 loop 6 和 loop 7
  * 到输出结果。
  * 结束
