---
{"dg-permalink":"LoadLock Chamber","dg-publish":true,"dg-show-local-graph":true,"permalink":"/LoadLock Chamber/","dgShowLocalGraph":true,"dgPassFrontmatter":true}
---

## LLC介绍
LLC是我们超高真空和大气的中转站，可以理解为空间站里准备出仓的地方。这里通过一个闸板阀和超高真空隔离，是传入和拿出样品的前哨战。
对LLC的操作可以分为以下几种：
1. [[lab/Lab_operation/LoadLock Chamber#放入样品\|#放入样品]]
2. 拿出样品
3. 不操作时的情况[[lab/Lab_operation/LoadLock Chamber#关闭分子泵&机械泵\|#关闭分子泵&机械泵]]

## 放入样品
当我们想从大气放入样品进入设备的时候，需要经过LLC。
首先我们需要检查：
1. 里面没有没传入超高真空的样品
2. 分子泵机械泵有没有关闭
3. LLC的真空度情况。如果LLC内是高真空，则需要进行[[lab/Lab_operation/LoadLock Chamber#充气（vent）\|#充气（vent）]]，使得它快速变成大气。具体判断手法就是用手轻轻尝试抬起把手松开的盖子，如果打不开就是较好的真空。
4. 检查闸板阀、离子规、黑色针阀是否关闭。
闸板阀：![1693299232386.jpg|300](/img/user/lab/%E7%B4%A0%E6%9D%90/1693299232386.jpg)

操作步骤：
1. [[lab/Lab_operation/LoadLock Chamber#关闭分子泵&机械泵\|#关闭分子泵&机械泵]]
2. 进行[[lab/Lab_operation/LoadLock Chamber#充气（vent）\|#充气（vent）]]
3. 打开盖子
4. 放入样品
5. 关上盖子
6. 根据情况[[lab/Lab_operation/LoadLock Chamber#开启分子泵&机械泵\|#开启分子泵&机械泵]]
7. 打开[[lab/Lab_operation/离子规使用方法\|离子规]]
8. 观察气压，等到10e-7
9. 打开闸板阀，将样品传入PC
10. <font color="#ff0000">关闭闸板阀</font>
### 充气（vent）
充气之前，<font color="#ff0000">请务必检查闸板阀是否关闭和离子规是否停止！！</font>[[lab/Lab_operation/离子规使用方法\|离子规使用方法]]
因为离子规在氧含量高的情况下容易将钨灯丝烧断。

操作步骤：
1. 打开盖子上的把手
2. 打开一般打开阀门
3. 略微打开阀门2
4. 等待盖子松动
5. 关闭两个阀门。

## 拿出样品
拿出样品几乎和放入样品一样，不过多赘述。

## 关闭分子泵&机械泵
当我们把样品传入LLC之后，就要关掉LLC里的各种设备了，减少震动。
关闭LLC的离子规[[lab/Lab_operation/离子规使用方法\|离子规使用方法]]
![300](/img/user/lab/素材/IMG_20230821_180251.jpg)
关闭气阀（点击CLOSE，听到很尖锐的一声）
![300](/img/user/lab/素材/IMG_20230821_180314.jpg)
关闭分子泵（点击STOP，可以看到ROT.SPEED在逐渐从100减少）
![300](/img/user/lab/素材/IMG_20230821_180254.jpg)
关闭机械泵（红色的）
![300](/img/user/lab/素材/IMG_20230821_180336.jpg)
关闭分子泵的操作面板：
![300](/img/user/lab/素材/IMG_20230821_180355.jpg)

## 开启分子泵&机械泵
开启整套泵组的时候有一些讲究。我们可以发现，泵组连接LLC的地方有一个气阀，它的作用就是为了隔绝LLC和分子泵，让泵组停掉的时候LLC还能保持一个较好的真空度。不过因此当分子泵启动的时候，假如气阀两侧气压不一样，很容易在开启针阀的时候把分子泵冲停。因此需要分情况合理操作。另外我们还要<font color="#ff0000">杜绝气体从泵组一侧流向LLC一侧</font>，因此需要确保LLC一侧气压永远大于等于泵组。
### LLC中完全大气时（标准操作)
1. 此时泵组内有一定真空度，直接打开针阀
2. 开启机械泵
3. 等一段时间？后开启分子泵
4. 分子泵满转后开启LLC的离子规
此时的气压：
![1693299195181.jpg](/img/user/lab/%E7%B4%A0%E6%9D%90/1693299195181.jpg)
### LLC中有10<sup>-2</sup>左右的负气压时
如果说按照标准操作，我们应当先进行[[lab/Lab_operation/LoadLock Chamber#充气（vent）\|#充气（vent）]]，让LLC完全变成大气，但我们可以进行快捷操作来节省这个时间：
1. 直接打开机械泵和分子泵
2. 等到分子泵转速20%左右的时候打开气阀
3. 等分子泵满转的时候开启LLC的离子规
此时的气压：
![1693299159947.jpg](/img/user/lab/%E7%B4%A0%E6%9D%90/1693299159947.jpg)