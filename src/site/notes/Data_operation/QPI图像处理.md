---
{"dg-permalink":"QPI图像处理","dg-show-local-graph":true,"dg-publish":true,"permalink":"/QPI图像处理/","dgShowLocalGraph":true,"dgPassFrontmatter":true}
---

STS的数据经常会有要测[QPI](../Concept/凝聚态相关概念.md#QPI：)的时候，对QPI的处理也有很多不同的操作方法，可以用不同的软件进行不同的操作。
## GWY处理QPI
1. 打开形貌图
2. 对形貌图进行[[Data_operation/GWY#滤波 1D/2D FFT Filtering\|滤波]]，把晶格滤出来。
3. 用滤出的晶格进行[Affine仿射变化](GWY.md#Affine仿射变化)，先看看数据强度够不够算法自动识别，如果不行就进行一次[插值Scale](GWY.md#插值Scale)。
4. [Merge](GWY.md#Merge)进去一组smx数据。
5. 首先进行[切割数据 Crop data](GWY.md#切割数据%20Crop%20data)，去掉坏点，并保持正方形
6. 然后对这个图片对比形貌图进行[“对齐”Align Rows](GWY.md#“对齐”Align%20Rows)，得到修正过的图片。
7. 再进行一次[切割数据 Crop data](GWY.md#切割数据%20Crop%20data)，把修正时产生的边缘的空像素去掉，并保持正方形。
8. 进行[二维傅里叶变换2D FFT](GWY.md#二维傅里叶变换2D%20FFT)
9. 如果之前有保存蒙版就用，没有就手动先用[蒙版Edit mask](GWY.md#蒙版Edit%20mask)扣一个蒙版出来，目的是去掉噪音的亮点和[高阶布拉格点](../Concept/凝聚态相关概念.md#高阶布拉格点)，之后可以将蒙版导出之后用。
10. 进行[“扣点”](GWY.md#“扣点”Interpolation%20data%20under%20mask%20by%20solution%20of%20Laplace%20equation)
11. 对图片进行一次60°和一次120°的[旋转](GWY.md#对称/旋转)
12. 对这三张图片进行一次（d1+d2+d3)/3的[数学运算](GWY.md#数学运算%20Arithmetic%20operation%20on%20data)，得到三重旋转对称图
13. 对得到的图再进行一次[旋转](GWY.md#对称/旋转)，把图片转正（即布拉格点的连线可以水平）
14. 复制一次图片，然后进行一次垂直[对称](GWY.md#对称/旋转)，然后将两张图进行一次(d1+d2)/2的[数学运算](GWY.md#数学运算%20Arithmetic%20operation%20on%20data)，得到垂直对称图，然后继续复制一次，进行一次水平对称，再进行一次运算，最终得到对称的QPI图。
15. 之后再把得到的QPI图进行一次切割，把外面的一些点去掉，最后再调整一下[Color Bar](GWY.md#”颜色“%20Stretch%20color%20range%20to%20part%20of%20data)，就得到了一张漂亮的QPI图。
完整视频：
![](../素材/VID_20230815_160538.mp4)
另外得到的QPI图还可以再进行额外操作来得到能带图。
1. 在想看的切面方向拉线[切片 Extract profiles along arbitrary lines](GWY.md#切片%20Extract%20profiles%20along%20arbitrary%20lines)，得到的数据进行txt的保存。
2. 用邓师兄写的一个python程序把不同偏压下的txt文件进行一个汇总
3. 导入gwy，再进行画图。
