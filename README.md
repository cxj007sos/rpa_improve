![](https://img.shields.io/badge/language-python-orange) ![](https://img.shields.io/badge/platform-win7--x64%7Cwin10--x64-lightgrey)

[![GitHub issues](https://img.shields.io/github/issues/cxj007sos/rpa_improve)](https://github.com/cxj007sos/rpa_improve/issues) [![GitHub license](https://img.shields.io/github/license/cxj007sos/rpa_improve)](https://github.com/cxj007sos/rpa_improve/blob/master/LICENSE)

[![](https://img.shields.io/badge/bilibili-%E5%A4%A7%E7%BE%BD-ff69b4)](https://space.bilibili.com/3410770?)

# 项目背景
2021-11-24 00:35 一位同事给我在微信中转了，B站UP主 [不高兴就喝水](https://space.bilibili.com/412704776 "不高兴就喝水") 的 [办公自动化视频](https://www.bilibili.com/video/BV1T34y1o73U? "5分钟，教你做个自动化软件拿来办公、刷副本、回微信 | 源码公开，开箱即用")

视频中的小程序实现了根据提供的图片，鼠标自动对其进行定位并实现双击、点击和滚轮的操作。

看了这个视频后我倍受鼓舞，就想为什么不再增加一些按键功能让这个程序变得更可用呢，于是我着手了开发。

经过一段时间的开发，此程序可以胜任一些简单的自动化操作了。

&nbsp; 
# 程序介绍

本程序是一个自动化程序，与前辈“按键精灵”相比，用 excel 的 xls 文件来编写自动化程序在某些情况下效率会更高一些。

对新手学习成本也会比较低一些，且绝对纯洁无广告。

源码在安装配置好环境，并下载好依赖包之后，理论上可以跨平台运行在多种系统下。

我仅在win7/Win10上测试可以正常使用，其他操作系统没有测试过。

&nbsp; 

# 安装和使用
&nbsp; 
## 安装

### 本程序必须使用python 3.4 或以上版本，需要先安装和配置python环境。

><font color="#FF0080"> 如何安装和配置python环境</font>：https://www.runoob.com/python3/python3-install.html


### 安装配置完python后，需要继续安装以下依赖包才可以使用：
>pip install pyperclip
pip install xlrd
pip install pyautogui==0.9.50 
pip install opencv-python
pip install pillow

&nbsp; 
注：如果在中国大陆下载特别慢的话可以在 install 后面，增加一个参数-i 国内镜像地址即可。
> 举例：pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pyperclip

|  其他国内镜像地址 |   |
| ------------		 | ------------ |
| 清华  				| https://pypi.tuna.tsinghua.edu.cn/simple|
| 阿里云 			 | http://mirrors.aliyun.com/pypi/simple  |
| 中国科技大学 | https://pypi.mirrors.ustc.edu.cn/simple  |
| 华中理工大学 | http://pypi.hustunique.com   |
| 山东理工大学 |http://pypi.sdutlinux.org   |
| 豆瓣 			 |http://pypi.douban.com/simple|

**注：不会安装和配置python环境也不用担心。已经打包了exe执行程序，可以在windows 7及其以上版本的操作系统中直接运行使用。只是它每次运行都需要拆包，会在 %temp% 文件夹中产生大量的以 MEI_xxx 命名的垃圾文件。并且exe的开启运行速度也比较慢。**

> <font color="#FF0080">（WIN7如果无法运行需要打上补丁，重启后才可以正常使用。）</font>


&nbsp; 
## 使用

 ### 本程序由两个文件组成：

<font color="#FF0080	">**"cmd.xls" ** </font>
 >编写自动化流程的文件。

<font color="#FF0080	">**"大羽改良版.py"**</font>or<font color="#FF0080	">**“大羽改良版.exe”**</font>
> 主程序，编写完自动化流程后运行其来执行。


**注意！这两个文件必须放在同一目录下，才能正常运行。否则会闪退！！**



&nbsp;
## cmd.xls如何编写
**必须按照以下规范编写，否则可能会出现闪退现象。第一行不要删除，是标题行，自动化流程从第二行开始编写。**

>#### 第一列
>指令类型，填写对应功能数字 
1 单击 2 双击 3 右键 【这三条命令后加.1，即1.1\2.1\3.1代表找不到图片就跳过此步，如果不加则会不停扫描】 
 4 输入
5 等待
6 滚轮 
7 热键组合
8 粘贴当前时间(B列必须填写:当前时间) 
9 windows CMD命令模式

>&nbsp;
>####第二列
> 指令内容，填写第一列中对应功能的属性

 >1，2，3 必须填写图片带有路径的全称，且路径和全称中不能有中文。
【图片格式理论上均支持，实际只测试了png\jpg\bmp，其他格式未测试。】
【注意如果同屏有多个相同图标，会默认找到最左上的一个，因此怎么截图，截多大的区域，是个学问。宗旨就是“唯一”】

 >|例如：||
| :------------ | :------------ |
|在同目录下的名为one.jpg的文件 |`one.jpg`|
|在同目录下Image文件夹下的one.png文件| ` .\image\one.png`|
|绝对路径下C盘test文件夹下的one.bmp文件| ` c:\test\one.bmp`|

>&nbsp;
>  4 可以填写任何东西。
 【注意其实这里是复制粘贴，并不是真正的输入。如果想输入请用7号命令】

>&nbsp;
 >5 只能填写正数，可以是小数。
 
>&nbsp;
 >6 只能填写正整数和负整数。		    	【正整数为往上滚，负整数为往下滚】

>&nbsp;
 >7 填写热键组合，每个按键用英文逗号","分开。 当然单个的按键也可以。

 >|例如：||
 | :------------ | :------------ |
 |启动任务管理器| `ctrl,shift,esc,` |
 |输入12345 | `1,2,3,4,5,` |
 |按一下9这个键。 |`9, `  |
>热键组合的名请自行搜索pyautogui库的用法。
【注意：英文中的”,”无法被识别，原因是这个符号被用来分隔其他按键组合了。暂无没有更好的解决办法，如果需要输入英文的","请使用4号命令复制粘贴。】

>&nbsp;
>8 填写任何内容均可，比如“当前时间”or“Now”

>&nbsp;
>9 可以填写任何windows的 CMD\powershell和Linux终端命令，是否能执行就看你填写的是否正确。

>&nbsp;
>#### 第三列
> 重复次数
不填写则默认为执行1次，填写的话只能填写正整数，-1为无限循环。
目前重复次数仅支持 第一列为 1,2,3,7 的指令（分别为：鼠标单击，双击，右键，热键组合。）
其他指令暂不支持。

>&nbsp;
#### 第四列
>备注
可以不填。为了方便后期维护，你可以选择在这里为这条自动化流程添加注释。

&nbsp;
##cmd.xls示范
<font color="#660000">**更多示范请参考实例文件夹里的cmd.xls
示范可能会因为系统，软件，访问网站等诸多环境变量的不同而无法完全正常使用，仅作参考。**</font>
&nbsp;
####示范一：

|指令类型： 1 单击 2 双击 3 右键 【这三条命令后加.1，即1.1\2.1\3.1代表找不到图片就跳过此步，如果不加则会不停扫描】 4 输入 5 等待 6滚轮 7热键组合 8粘贴当前时间(B列必须填写:当前时间) 9 windows CMD命令模式|内容： 图片名称(不能为中文).png、输入内容（实为复制粘贴） 等待时长/秒、滚轮距离（如-200，即为往下滚） 当前时间、windows CMD命令|重复次数 (-1代表一直重复) |备注|
| ------------ | ------------ | ------------ | ------------ |
|1 | 01.png |   |  在屏幕上不断搜索执行程序同目录下 00.png 相同的内容直到找为止，然后对其进行鼠标“单击” |
|2 | c:\test\02.jpg |   |  在屏幕上不断搜索执行 c:\test\02.jpg 相同的内容直到找为止，然后对其进行鼠标“双击” |
|3.1 | .\image\03.bmp |   | 在屏幕上仅搜索一次执行程序同目录image文件夹下 03.bmp  相同的内容，然后对其进行鼠标“右键”。若无法找到相同的图片，则会跳过此步骤执行下一步。  |

&nbsp;
####示范二：

|指令类型： 1 单击 2 双击 3 右键 【这三条命令后加.1，即1.1\2.1\3.1代表找不到图片就跳过此步，如果不加则会不停扫描】 4 输入 5 等待 6滚轮 7热键组合 8粘贴当前时间(B列必须填写:当前时间) 9 windows CMD命令模式|内容： 图片名称(不能为中文).png、输入内容（实为复制粘贴） 等待时长/秒、滚轮距离（如-200，即为往下滚） 当前时间、windows CMD命令|重复次数 (-1代表一直重复) |备注|
| ------------ | ------------ | ------------ | ------------ |
|9 |  start notepad |   |  打开记事本 |
|5 |  0.5 |   |  等待0.5秒 |
|4 |  hello world!! |    |  复制这段文字，并粘贴。即：ctrl+c ctrl+v|
|7 | enter| 50| 执行回车，循环50次|
|8 | Now|   |  粘贴当前时间 |
|6 | 200|   | 鼠标滚轮“向上”滚动200距离 |
|5 |  0.5 |   |  等待0.5秒 |
|6 | -200|   | 鼠标滚轮“向下”滚动200距离 |
&nbsp;



# 注意事项：
使用exe执行文件 "大羽改良版.exe" 在退出程序时，不要直接用鼠标点击右上角的 "X" 进行关闭，需要输入命令 “0.退出程序”。
因为exe会在 %temp% 文件夹中产生大量的以 MEI_xxx 命名的临时文件
0.退出程序 它是在退出之前将在 %temp% 产生的 MEI_xxx 临时垃圾文件全部删除后再退出程序，确保你的系统盘不会被临时文件占满。

使用 "大羽改良版.py"则不会有以上问题。
&nbsp;

#Q&A：
#### 问：有没有视频教程？
#### 答：有的点这里。[python自动化改良版_第二版](https://www.bilibili.com/video/BV1BF411z7sC "python自动化_改良版_第二版|源码from:不高兴就喝水")
&nbsp;

#### 问：为什么会出现闪退或者执行到一半控制台消失？
#### 答：没有正确安装和配置python环境，或者没有正确安装依赖包。可以尝试使用已经打包的exe执行文件。“cmd.xls”和“大羽改良版.py”or“大羽改良版.exe”没有放在同一个目录下。cmd.xls 没有按照规范编写。
&nbsp;

#### 问：流程在控制台中已经显示执行，但是并未执行？
#### 答：可能是两条指令太快计算机没有反应过来。建议在两条流程之间增加一个5号命令，适度增加等待时间。

置顶的徽标有B站的 教程视频


# 鸣谢：
排名部分先后

[不高兴就喝水](https://space.bilibili.com/412704776),[尔茄无双](https://space.bilibili.com/3361089),王建
