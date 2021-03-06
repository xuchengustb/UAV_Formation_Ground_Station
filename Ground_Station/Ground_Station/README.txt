Attention：本Qt工程测试使用系统为Windows7、Windows8.1和Windows10，使用的Qt Creator版本为Qt Creator 3.4.2 (opensource).
           Qt Creator编辑文本格式为UTF-8
Author：郑泽丰、张晓武
Date：2016-2017

****飞行器编队上位机开发技术报告****

--------------------------------------------------
#进度
1. 完成界面基本布局

#知识点
1. 堆栈窗口的使用
2. 停靠窗口的使用
3. 控件的自动缩放与固定比例

V0.0
2016.12.29 郑泽丰
---------------------------------------------------
#进度
1.完成串口功能部分实现，能够正常收发数据

#知识点
1. 弹出警告窗口

V0.1
2016.12.30 郑泽丰
---------------------------------------------------
#进度
1. 解决了十六进制和字符的发送和接收问题
2. 解决了串口关闭后无法再次打开的问题（原因是串口点击关闭之后并
   没有杀死进程，重新打开时发现已经被打开，所以失败。解决方法是
   关闭串口时把打开的串口进程杀死）
3. 解决十六进制输入时，用户输入非法字符的问题，提高代码容错性，
   利用正则表达限制输入的字符
4. 自动搜索串口号

#知识点
1. QString与QByteArray的相互转换
2. char*与QByteArray的相互转换
3. QString提取子字符串，转换成十六进制，替代空格
4. 正则表达式的使用

#问题
1. 串口发送函数发送的是char型，发送十六进制时有问题
2. 停靠窗口关闭之后没法再打开

V0.2
2016.12.31 郑泽丰
------------------------------------------------------
#进度
1. 解决了停靠窗口关闭之后无法再打开的问题
2. 地图窗口添加了鼠标焦点坐标显示
3. 解决串口发送函数发送十六进制时，接收出现错误的问题，但原因未知
4. 整合飞行器编队协议

#知识点
1. widget添加菜单栏，并添加动作

#问题
1. 串口拔出后，重新插入时没有显示出串口号

V0.3
2017.1.2 郑泽丰 张晓武
------------------------------------------------------
#进度
1. 完成通信协议整合并测试成功

#知识点

#问题
1. 耦合程度高，通信协议与通信收发耦合，界面与具体功能实现耦合
2. 串口拔出后，重新插入时没有显示出串口号

V0.4.0
2017.1.3 郑泽丰 张晓武
-------------------------------------------------------
#进度
1. 修改串口页面的默认参数设置，波特兰默认为115200，发送和接收默
   认为16进制，以方便调试。
2. 增加文件关系文件，便于后续开发人员了解本工程
3. 修复bug，串口发送输入框，发送16进制时，输入过行（\n）非法
4. 格式化串口接收十六进制时的显示形式，便于查看
5. 串口拔出后，重新插入时,刷新后显示出串口号

#知识点

#问题
1. 界面程序和具体实现程序耦合

V0.4.1
2017.1.3 郑泽丰
--------------------------------------------------------
#进度
1. 修改Javascript，实现地图定时画出飞行器的当前位置。
2. 地图清除所有标记
3. 地图上选择目标点

#知识点
1. Javascript添加和取消监听

#问题
1. 清除某一个点
2. 将所有目标点传回QT
3. 状态显示
4. 飞行器目标高度的设置

V0.5.0
2017.1.4 郑泽丰 张晓武
--------------------------------------------------------
#进度
1. 解决bug，多次点击选择目标点会出现多个标志
2. 清除单个目标点

#知识点
1. 自定义信号

#问题
1.

V0.6.0
2017.1.5 郑泽丰
--------------------------------------------------------
#进度
1. 状态显示页显示当前坐标、目标坐标以及待设置目标坐标，并定时刷新
2. 开始任务
3. 起飞、降落、暂停按键

#知识点
1. QString与数值之间的转换
2. QTabelWidget的使用

#问题
1. 中途拔掉串口后，关闭串口程序崩溃
2. 待设置高度的读取和显示问题。状态页应该只刷新读取，地图页负责从
   地图读取数据
3. 地图返回数据错误

V0.7.0
2017.1.6 郑泽丰
--------------------------------------------------------
#进度
1. 为状态显示也添加颜色，便于区分
2. 添加控件提示，方便用户使用本上位机

#知识点
1. QComboBox信号使用
2. QTabelWidget设置单元格长宽

#问题
1.

V0.7.1
2017.1.6 郑泽丰
---------------------------------------------------------
#进度
1. 解决bug，地图传回数据错误
2. 测试起飞、降落、暂停、设置目标点和执行任务
3. 显示飞行器连接状态
4. 解决bug，设置目标点时飞行器接收到的数据错误

#知识点
1. QTextEdit滚屏

#问题



V0.7.2
2017.1.7 郑泽丰 张晓武
---------------------------------------------------------
#进度
1. 调整地图初始中心位置
2. 美化界面
3. 添加程序图标

#知识点
1. 添加资源文件

#问题



V0.7.2
2017.1.8 郑泽丰
---------------------------------------------------------
#进度
1. 修改BUG，删除地图标志时，未删除线
2. 起飞降落后，没法重新起飞
3.

#知识点
1.

#问题
1. 程序运行久了之后内存越来越大，最后崩溃（定时画图导致）
2. 通信中断，猜测是固件原因


V0.8.0
2017.1.9 郑泽丰 张晓武
----------------------------------------------------------
#进度
1. 找到内存不断增加的原因。QT向JS发出画点请求，JS则申请内存来创建动
   态数组，但是没有释放，所以内存一直增长。如果清楚标记的话，内存不变，
   但是，JS会先使用已申请的内存，不够了再继续申请。
2. 修改状态显示页输出显示，进行详细状态显示
3. 输出飞行日志

#知识点
1. Qt文件的创建与输出

#问题
1.


V0.8.1
2017.1.10 郑泽丰 张晓武
----------------------------------------------------------
#进度
1. 添加到达目标点显示

#知识点
1.

#问题
1.


V0.8.2
2017.1.11 郑泽丰 张晓武
----------------------------------------------------------
#进度
1. 解决bug，软件运行后，占用内存不断增加，清除标记后内存不释放问题。

#知识点
1. javascript动态数组，赋值null之后自动回收内存。

#问题
1. 通信有问题，修改了重发延时时间和跳过机制。


V0.8.3
2017.2.28 郑泽丰 张晓武
----------------------------------------------------------
#进度
1. 缩短通信数据，从36个字节减少至29个字节。

#知识点
1. 通信模块自动打包机制，每29个字节打包发送，剩余字节另外发送，容易导致
   校验错误。

#问题
1.


V0.8.4
2017.3.2 郑泽丰 张晓武
----------------------------------------------------------
#进度
1. 飞行记录改为通信检查完毕之后就记录

#知识点
1.

#问题
1.


V0.8.5
2017.3.30 郑泽丰 张晓武
----------------------------------------------------------
#进度
1. 添加编队飞行，地图选择领航者的目标位置

#知识点
1.

#问题
1.


V0.8.6
2017.3.31 郑泽丰 张晓武
----------------------------------------------------------
#进度
1. 修改飞行数据Matlab画图脚本reapear_matlab.m，同时画出三维图和三视图。

#知识点
1.

#问题
1.


V0.8.6
2017.4.11 郑泽丰
----------------------------------------------------------
#进度
1. 添加CVT算法，完成自动生成队形
2. 修改画轨迹的方法，不适用谷歌地图提供的画线功能，使用画点

#知识点
1. 谷歌地图提供删除指定标记的功能
2. 谷歌地图画线需要占用大量的内存，改成画点则大幅减少了运行时所需内存

#问题
1. 解决了之前上位机运行久之后内存爆掉的问题


V0.8.7
2017.4.13 郑泽丰
----------------------------------------------------------
