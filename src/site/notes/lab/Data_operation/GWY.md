---
{"dg-permalink":"GWY","dg-publish":true,"dg-show-local-graph":true,"permalink":"/GWY/","dgShowLocalGraph":true,"dgPassFrontmatter":true}
---

## 主菜单
![200](/img/user/lab/素材/20230817162409.png)
打开GWY之后出现的这个小浮窗就是主菜单，里面有所有要用到的工具。
### File菜单
![300](/img/user/lab/素材/20230817162904.png)
#### Open
打开一个文件，可以是数据，也可以是.gwy文件，类似ps的.ps文件。
#### Merge
当我们打开一个文件后，如果再open，其实是打开了另一个文件，并不能把两个文件联系在一起。这时候我们需要merge，将两个文件放在一起，并进行相关操作。

#### Save/Save As
gwy的文件保存和其他一些软件会自动给你设置后缀不同，建议要保存成什么类型一定要在后面加上后缀。比如要保存数据，就保存成txt文件，要保存工程文件，就保存成gwy文件。当然，要保存数据的话并不是在这里进行保存。

### Edit菜单
![300](/img/user/lab/素材/20230817163357.png)
#### Undo/Redo
懂得都懂

#### Color Gradient
数据的color bar颜色设置在这里。我们可以创建新的color bar。
STM blue：
![300](/img/user/lab/素材/mmexport1692261409232.png)


### *Data Process（重要）*
![300](/img/user/lab/素材/20230817163800.png)
几乎所有的数据操作都会在这里进行，有很多功能我也没用过，之后再慢慢更新（2023.8.17）
#### Basic Operations
![300](/img/user/lab/素材/20230817163951.png)
可以对图像进行各种旋转等操作，基本功能其实看名字也能猜出七七八八。
##### 对称/旋转
Flip Diagonally/Horizontally/Vertically 可以对图像直接进行对称，并不会产生一个新的图层。
Rotate by Angle 是比较常用的旋转操作，可以在操作完成后产生一个新的图层。
![400](/img/user/lab/素材/20230817165011.png)

##### 插值Scale
**scale**本质上就是一个坐标映射：由目标图像上的点，在源图上找到对应的点，进而找到插值所需要的点，最后根据插值权重得到最终缩放后的结果。
有时候我们的数据强度不够进行一些其他操作，比如Affine的算法可能检测不到足够的信号强度，这时候我们可以进行scale来放大信号。
![300](/img/user/lab/素材/20230817164737.png)
Scale by ratio进行放大的倍率调整，下面的长和宽就是放大后的像素长宽

#### Correct Data
![300](/img/user/lab/素材/20230817165541.png)
##### 滤波 1D/2D FFT Filtering
我们知道FFT傅里叶变换之后，可以把时域的数据变成频域图像，这样就可以挑选我们需要的频率出来，可以排除噪音。这个功能就是这样的。对图像进行傅里叶变换后，在上面画圈就可以选到我们想要的频率了。
![](/img/user/lab/素材/20230817165806.png)
点击OK之后，就可以获得一个滤出频率的图和扣掉该频率的图（和Output Options选择有关系）
![](/img/user/lab/素材/20230817165959.png)


##### “对齐”Align Rows
我觉得可以把它当作归一化，或者“拉平”，就是可以让图片整体都通过一个拟合把曲线拉成平的：
![](/img/user/lab/素材/20230818155729.png)
![400](/img/user/lab/素材/20230818155804.png)

![](/img/user/lab/素材/20230818155828.png)

#### Distortion
![300](/img/user/lab/素材/20230817165116.png)
##### Affine仿射变化
![](/img/user/lab/素材/20230817165234.png)
我们通常使用Affine来进行晶格的调整，让晶格自动变正。
通常我们获得的Mapping中，会一同把形貌图也保存下来，我们就可以用这个形貌图来进行Affine。
首先通过形貌图的FFT的布拉格点把晶格滤出来，之后我们就可以用这个晶格来Affine其他Mapping图了。
![](/img/user/lab/素材/20230817170612.png)
其中，Correct Lacttice里面，a1是晶格常数，需要看不同材料不同设置，角度也是。<font color="#ff0000">其实一般来说不需要进行设置，让软件自己算就行，这里的单位有bug，其实就是0.543nm，后面的单位有时候会很奇怪，要小心。</font>
Image for ACF中，选择我们滤出来的形貌图，就可以让两个图进行匹配了。处理完成后：（就像进行了一下旋转，多出来一些没用的数据之后要切掉）
![400](/img/user/lab/素材/20230817170845.png)


#### Integeral Transforms
![300](/img/user/lab/素材/20230818160222.png)
##### 二维傅里叶变换2D FFT
这个可以把图像进行一个傅里叶变换并产生一个新的图像。
![300](/img/user/lab/素材/20230818160326.png)
把这三个选上（暂时不知道为啥）
Windowing type就是进行窗函数的选择。

#### Mask
![300](/img/user/lab/素材/20230818160429.png)
这里就是对蒙版进行一些操作。
Mark With可以将之前Extract Mask的蒙版进行匹配（注意一定要大小单位都相同）
![400](/img/user/lab/素材/20230818160556.png)
第一个红圈里进行Mask的选择；第二个红圈可以调整对Mask的边缘羽化。

## 工具栏
![300](/img/user/lab/素材/20230818161039.png)
### View
![300](/img/user/lab/素材/20230818161111.png)
这里可以对窗口进行一个放大缩小。值得注意的的是：再进行的时候必须1：1状态，否则测出来的数据点可能是假的。

### Data Process
![300](/img/user/lab/素材/20230818161214.png)
#### 数学运算 Arithmetic operation on data
![](/img/user/lab/素材/20230818161403.png)
![](/img/user/lab/素材/20230818161440.png)
这里可以对多个图片进行各种数学操作，比如（d1+d2+d3）/ 3这样就可以对三张图进行平均，可以对三张旋转60°的图片进行这种操作来得到三重对称。

#### “拉平” Align rows using various methods
![](/img/user/lab/素材/20230818161613.png)
和菜单里的Align其实是一样的。

#### “扣点”Interpolation data under mask by solution of Laplace equation 
![](/img/user/lab/素材/20230818162342.png)
可以在有蒙版的情况下，把蒙版下面的点通过Laplace算法给抹平：
![300](/img/user/lab/素材/20230818162553.png)![300](/img/user/lab/素材/20230818162612.png)

### Tools
![300](/img/user/lab/素材/20230818161741.png)
#### 切片 Extract profiles along arbitrary lines
![](/img/user/lab/素材/20230818161845.png)
![](/img/user/lab/素材/20230818161912.png)
<font color="#ff0000">切记这里一定要1：1的时候操作！</font>
这个功能可以切出来图片上的一条线。按上下左右可以操控x1y1点，按住shift+上下左右可以操控x2y2。然后点击apply之后就可以获得一个graph，之后就可以再进行保存。

#### 切割数据 Crop data
![](/img/user/lab/素材/20230818162210.png)
可以把图片进行修剪，比如边上有坏点，或者FFT需要一个正方形，都可以剪出来。
![400](/img/user/lab/素材/20230818162301.png)

#### 蒙版Edit mask
![](/img/user/lab/素材/20230818162653.png)
可以进行一个蒙版的画
![](/img/user/lab/素材/20230818162806.png)

#### ”颜色“ Stretch color range to part of data
![](/img/user/lab/素材/20230818162836.png)
就是处理color bar。只要能调整到看清特征就好了。
![300](/img/user/lab/素材/20230818162946.png)
