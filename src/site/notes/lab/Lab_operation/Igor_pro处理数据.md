---
{"dg-permalink":"Igor pro 处理数据","dg-publish":true,"dg-show-local-graph":true,"permalink":"/Igor pro 处理数据/","dgShowLocalGraph":true,"dgPassFrontmatter":true}
---

![](/img/user/lab/素材/20230522154403.png)
命令窗口（类比终端）：快捷键CTRL+J唤出

## QPI图像处理：
在命令窗口中输入：<span style="background:rgba(5, 117, 197, 0.2)">make/o/n=(256,256,7) map</span>，创建一个新的名为map的3维数组，它的xy有256个点，一共7层。具体的大小需要根据测量数据来修改。
<span style="background:rgba(5, 117, 197, 0.2)">make</span>：创建一个新的变量
<span style="background:rgba(5, 117, 197, 0.2)">/o</span>：覆盖
<span style="background:rgba(5, 117, 197, 0.2)">/n</span>：新建？

![300](/img/user/lab/素材/20230522154718.png)
点击Initialize，进行数据导入。

之后在命令行中输入<span style="background:rgba(5, 117, 197, 0.2)">layer=x（x是想看的层）</span>，选择map中的对应的层。和python等一样，数组都是从0开始计数的；然后点击Display dI/dV Map，打开这个图层，并自动赋予它一个新的变量名称，比如map2d，可以在打开的窗口上看到。
举例：
![300](/img/user/lab/素材/20230522155213.png)
![400](/img/user/lab/素材/20230522155326.png)
这是两个自定义的窗口，里面有各种函数，可以快速进行各种操作。（当前2023年5月22日，未来窗口的功能等有可能会发生改变）这里两个窗口一个是4重对称，一个是6重对称，根据需要来进行不同的选择。

首先点击Load Data，将刚刚打开的map中的一层Load进去。点击Display可以打开这个图层。
然后点击FFT，进行傅里叶变换。
之后点击Choose Bragg Peaks，可以选择布拉格点，依次选择挨着的布拉格点，以此来进行修正。
![300](/img/user/lab/素材/20230522160001.png)
注意如果数据信号较弱，布拉格点可能比较不清晰，可以导入同一次测量中的形貌图（一般是第一张图）来进行选择。选择的布拉格点会保存下来。

之后点击Matrix Transformation就可以将晶格修正了。
然后分别点击Fold Symmetry和Mirror Symmetry就可以进行对称操作，得到漂亮的QPI数据。
![300](/img/user/lab/素材/20230522160216.png)

## Dispersion操作
师兄对代码进行了改进，点击右侧窗口中的Dispersion-6就可以直接对所有的图层进行对称化操作，然后对这些QPI图像获得中线的Dispersion图像。
![](/img/user/lab/素材/20230522160706.png)
Dispersion图像可以理解为把所有QPI图像叠起来，然后从竖着切开，这样就可以得到色散关系的图像。