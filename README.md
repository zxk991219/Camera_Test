# Camera_Test

## SimpleSample

- SimpleSample是工业相机的C++实例文件，我修改了一些SDK文件以使用OpenCV对摄像头图像进行获取 (line 1576)
- 使用方法：在SimpleSample文件夹下运行sudo make编译后 执行./runSample.sh命令运行
- 问题：line 1591 使用cvCreateImageHeader()前需要将图像位深改为8bit，否则后面cvShowImage会报错：segmentation fault缓冲区溢出
- [参考网页:OpenCV 处理内存中的图像数据](https://blog.csdn.net/b5w2p0/article/details/10973071)

## 曝光模式

|曝光模式|含义|
|:-|:-|
|Off|手动调节曝光时间（曝光量）|
|Once|单次设定曝光时间（不可手动调节）？？？|
|Continuous|连续曝光时间（不可手动调节）？？？|

## 增益

自动增益功能主要包含三个选项：Off，Once 和 Continuous，分别是关闭自动增益，
做一次自动增益和连续做自动增益。自动增益的功能必须与采集配合，也就是说只
有在采集状态下才能做自动增益，如果相机没有执行采集指令，那么自动增益是不
能实现的

相机通常具有一个对传感器的信号进行放大的视频放大器，其放大倍数称为增益。若放大器的增益保持不变，则在高亮度环境下将使视频信号饱合。利用相机的自动增益控制（AGC）电路可以随着环境内外照度的变化自动的调整放大器的增益，从而可以使相机能够在较大的光照范围内工作。teo摄像机能根据实时照度，自动提高摄像机的增益调节亮度，从而在低照度环境下仍能显示较好的图像。

工业相机内有一个将来自 CCD 的信号放大到可以使用水准的视频放大器，其放大即增益，等效于有较高的灵敏度，然而在亮光照的环境下放大器将过载，使视频信号畸变。当开关在 ON 时，在低亮度条件下完全打开镜头光圈，自动增加增益以获得清晰的图像。开关在 OFF时，在低亮度下可获得自然而低噪声的图像。

摄像机输出的视频信号必须达到电视传输规定的标准电平，即,为了能在不同的景物照度条件下都能输出的标准视频信号，必须使放大器的增益能够在较大的范围内进行调节。这种增益调节通常都是通过检测视频信号的平均电平而自动完成的，实现此功能的电路称为自动增益控制电路，简称AGC电路。具有AGC功能的摄像机，在低照度时的灵敏度会有所提高，但此时的噪点也会比较明显。这是由于信号和噪声被同时放大的缘故
