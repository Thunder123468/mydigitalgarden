---
{"dg-permalink":"QPI图像处理","dg-show-local-graph":true,"dg-publish":true,"permalink":"/QPI图像处理/","dgShowLocalGraph":true,"dgPassFrontmatter":true}
---

STS的数据经常会有要测[QPI](../Concept/凝聚态相关概念.md#QPI：)的时候，对QPI的处理也有很多不同的操作方法，可以用不同的软件进行不同的操作。
## GWY处理QPI
1. 打开形貌图
2. 对形貌图进行[[lab/Data_operation/GWY#滤波 1D/2D FFT Filtering\|滤波]]，把晶格滤出来。
3. 用滤出的晶格进行[[lab/Data_operation/GWY#Affine仿射变化\|Affine]]，先看看数据强度够不够算法自动识别，如果不行就进行一次[[lab/Data_operation/GWY#插值Scale\|插值]]。
4. [[lab/Data_operation/GWY#Merge\|Merge]]进去一组sxm数据。
5. 首先进行[[lab/Data_operation/GWY#切割数据 Crop data\|剪切]]，去掉坏点，并保持正方形
6. 然后对这个图片对比形貌图进行[[lab/Data_operation/GWY#“对齐”Align Rows\|对齐]]，得到修正过的图片。
7. 再进行一次[[lab/Data_operation/GWY#切割数据 Crop data\|剪切]]，把修正时产生的边缘的空像素去掉，并保持正方形。
8. 进行[[lab/Data_operation/GWY#二维傅里叶变换2D FFT\|傅里叶变换]]
9. 如果之前有保存蒙版就用，没有就手动先用[[lab/Data_operation/GWY#蒙版\|蒙版功能]]扣一个蒙版出来，目的是去掉噪音的亮点和[[lab/Concept/凝聚态相关概念#高阶布拉格点\|高阶布拉格点]]，之后可以将蒙版导出之后用。
10. 进行[[lab/Data_operation/GWY#“扣点”Interpolation data under mask by solution of Laplace equation\|扣点]]
11. 对图片进行一次60°和一次120°的[[lab/Data_operation/GWY#对称/旋转\|旋转]]
12. 对这三张图片进行一次（d1+d2+d3)/3的[[lab/Data_operation/GWY#数学运算 Arithmetic operation on data\|数学运算]]，得到三重旋转对称图
13. 对得到的图再进行一次[[lab/Data_operation/GWY#对称/旋转\|旋转]]，把图片转正（即布拉格点的连线可以水平）
14. 复制一次图片，然后进行一次垂直[[lab/Data_operation/GWY#对称/旋转\|对称]]，然后将两张图进行一次(d1+d2)/2的[[lab/Data_operation/GWY#数学运算 Arithmetic operation on data\|数学运算]]，得到垂直对称图，然后继续复制一次，进行一次水平对称，再进行一次运算，最终得到对称的QPI图。
15. 之后再把得到的QPI图进行一次切割，把外面的一些点去掉，最后再调整一下[[lab/Data_operation/GWY#”颜色“ Stretch color range to part of data\|color bar]]，就得到了一张漂亮的QPI图。
完整视频：
<div style="width: 500px;height: 380px;margin: 0px auto;">
        <iframe width="500px" height="380px" src="http://player.youku.com/embed/XMzcwNTY3NTM2MA" frameborder=0 allowfullscreen></iframe>
    </div>
![](../素材/VID_20230815_160538.mp4)
另外得到的QPI图还可以再进行额外操作来得到能带图。
1. 在想看的切面方向拉线[[lab/Data_operation/GWY#切片 Extract profiles along arbitrary lines\|切片]]，得到的数据进行txt的保存。
2. 用邓师兄写的一个python程序把不同偏压下的txt文件进行一个汇总
3. 导入gwy，再进行画图。
