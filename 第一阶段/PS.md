# PS

- 名称：图片的名字，可以定义，也可以后期修改
- 预设：系统给了一定的画布大小方案，不过一般我们会写自定义
- 宽度和高度：单位都用”像素”，值可以自行定义
- 分辨率：图像的清晰程度，分辨率越高，图像在同单位里越清晰
  - 72-96：电子屏幕
  - 150：制作大型喷绘图像：易拉宝，X展架
  - 300：印刷品-宣传单，MD
- 颜色模式：
  - RGB（red,green,blue）色彩三元素， 彩色屏幕
  - CMYK，印刷四色
  - 位图，黑白色，图像中只有黑色和白色（连灰色都没有）
  - 灰度，灰色深浅（有浅灰到深灰）的图像
  - 背景颜色：白色和透明色的选择
  - 

## 图像的调整

绿色版：alt+滚轮

查看图片的位置：空格+鼠标拖动





## 图片的规格

**图片分类**

- 位图
  - 无损压缩
  - 有损压缩
  
- 矢量图

  

#### 位图（ps）

由像素点组成的图像

特点：放大会失真，变模糊

颜色比较丰富

常见的位图：jpg,png,gif



### 矢量图（ai）

由点（非像素）构成的图像

特点；永远不会失真

颜色比较单一-256色

**位图的图像类型**

| 图片类型                       | 描述                     |
| ------------------------------ | ------------------------ |
| JPEG（存储类型）/JPG（扩展名） | 有损压缩，默认压缩比40:1 |
| png（扩展名）                  | 无损压缩，透明图片       |
| gif（扩展名）                  | 无损压缩，动图（帧图）   |



### 矢量图的图像类型

SVG，SWF

用途：在印刷和打印制作环节



## 选区

删除选区ctrl+D

选区选择正方形/正圆：shift+鼠标拖动

确定中心点的选择：alt+鼠标拖动

shift+alt+鼠标拖动：确定中心的正图像

图像在复制，粘贴后会自行添加一个图层



## 图章仿制工具

### 去水印

按住alt键取一个原颜色，然后在需要覆盖图像的位置拖动鼠标（单击鼠标）就可以覆盖颜色



### 图像修补

需要选择没有固定纹理或纯色图片进行修补

无固定纹理的一切图：沙滩，水面，火，天空，岩石



## 钢笔

钢笔工具本意是用来绘制一个鼠标移动轨迹。可以用其完成选区的绘制



### 贝塞尔曲线

贝塞尔曲线是钢笔工具的绘制路径，由三个点组成（开始点，中间点，结束点），开始点和中间点之间可以绘制一个直线/曲线，而中间点和结束点之间会自动生成一个直线/曲线

可以前后连接完成一个指定的绘制路径

**ctrl+回车，可以变为选区**

可以按住**ctrl**，然后直接调整钢笔工具的锚点，以此来改变贝塞尔曲线的弧度和位置

如果只需要绘制一半的弧度，则需要在绘制完中心点时：按住**alt**，鼠标单击中心点。这样便可结束后续的半个弧度，重新开始



## 切片

在一张完整的网站效果图上（psd）可以对于一些无法使用代码生成的图片进行单独的切割并保存

对准需要单独保存的图片进行划分，保存为web格式

**注意：**切片过程中需要把透明图片和非透明图片在预览的时候就设定好

如果是图标或符号，则需要再次制作为雪碧图

**操作：**如果需要完成png图像的操作。则需要先把图像的背景图层隐藏掉

存储时需要选择“所有用户切片”，就能够正常导出保存了。



## pxCook

像素大厨是针对PSD原稿进行的图像位置的标注。方便后期精确制作页面

可以根据工具栏提供的功能标注图像

注意：psd图像是可以智能标注，而普通图像（JPG）只能手动标注

最终对于一个前端工程师最舒服的四大内容

- 网站PSD原稿
- 网站所要用到的切片图片
- 有标注位置和尺寸的标注图
- 有雪碧图或精灵图