---
title: 你奶奶都能学会的显示器超频指北
tags:
  - 超频
  - 显示器
  - 教程
category: 奇奇怪怪的教程
date: 2021-09-02 16:04:37
---


## 前言 ##

**超频有风险，操作需谨慎**
**超频有风险，操作需谨慎**
**超频有风险，操作需谨慎**

*超频可能会导致显示器寿命缩短，屏幕色彩准确度下降等问题，甚至可能丢失保修，如果不能接受这些风险请不要进行操作！如果您继续阅读并进行操作，则意味着您已经理解超频可能对显示器产生的危害，并愿意自行承担所有操作带来的后果！*

*本文为通用的显示器超频方案（Windows平台），理论上适用于所有显卡，如果你希望使用显卡控制面板添加自定义分辨率，可以参考本文中部分内容并自行操作。*

## 准备 ##

你需要的软件有：

- [aida64](https://www.aida64.com/downloads/latesta64xe) 用来获取显示器的相关信息
- [Custom Resolution Utility (CRU)](https://www.monitortests.com/forum/Thread-Custom-Resolution-Utility-CRU) 用来创建自定义分辨率、刷新率

*注：如果下载缓慢或者打不开，请自行在网络上寻找相关资源或/和科学上网。*

## 获取显示器信息 ##

打开 `aida64` ，查看`显示设备`-`显示器`，并在显示其名称中选中你要超频的显示器

![everest](/static/monitor-overclocking/aida64.png)

你需关注的就是其中的 `水平扫描频率` 和 `垂直扫描频率`
其中`垂直扫描频率`最大值决定了你显示器能够超频的`极限刷新率`，超过这个值基本上不用考虑了，可能会存在花屏黑屏等问题。
`水平扫描频率`在稍后会讲解

## 创建自定义分辨率 ##

![CRU](/static/monitor-overclocking/CRU1.png)

打开 `Custom Resolution Utility`，在左上角选中你要超频的显示器，然后点击右侧`Detailed resolutions`下方的`Add`按钮

![CRU](/static/monitor-overclocking/CRU2.png)

在新弹出的页面中，左上角`Timing`选择`Exact reduced`，下方`Refresh rate`中输入你想要超频到的刷新率（不可超过前文中的`垂直扫描频率`最大值，超过肯定是没法正常显示的）
输入中你会发现下方`Horizontal`的数值在改变。还记得前面的`水平扫描频率`吗？如果输入刷新率后`Horizontal`的数值小于前面`水平扫描频率`的最大值，恭喜你，这个刷新率`有可能`是可以使用的！
但是如果`Horizontal`的数值大于`水平扫描频率`最大值，你的显示器就无法完美支持在这个分辨率和刷新率下运行，建议降低分辨率或刷新率后再尝试。（当然你如果一定要继续我也拦不住你呀ಥ_ಥ）

*注：可能是由于四舍五入等问题，实际上显示器的`水平扫描频率`和软件中看到的数值存在微小偏差*

调整完成后点击`OK`保存

## 测试自定义分辨率 ##

创建完成后，运行CRU软件目录下的 `restart64.exe` 重启显卡驱动即可在显示设置中看到新的刷新率。
*注：32位操作系统请运行 `restart.exe`*

选中新的刷新率后，显示器有可能会出现花屏等问题，不要惊慌(￣y▽,￣)╭ ，能辨认屏幕就先恢复到先前的刷新率，不能看清也只需要等待15秒即可恢复。稍后我们将开始微调分辨率中的一些数据来让显示器稳定运行在该刷新率。

如果你的显示器看起来一切正常，恭喜你可以跳过下一步啦！

如果`Horizontal`大于显示器`水平扫描频率`，应用该分辨率后可能出现屏幕上下黑边，显示区域模糊的问题，必须降低刷新率或分辨率解决。

## 微调自定义刷新率 ##

![CRU](/static/monitor-overclocking/CRU3.png)

再次打开 `CRU`，选中先前创建的分辨率刷新率，点击`Edit`。

![CRU](/static/monitor-overclocking/CRU4.png)

将图中的红线标注的两处数值适当调大（例如我原本是24和12，调整为36和18），但是注意调整后下方`Horizontal`不可大于`水平扫描频率`。然后点`OK`保存，再次运行 `restart64.exe` 重启显卡驱动，然后在显示设置中设置新的刷新率。

如果设置为新的刷新率后显示正常，可以进行下一步。如果出现花屏等问题说明`Horizontal`偏小，需要再次调大上图红线处数值。如果出现像素模糊，画面被压缩等问题说明`Horizontal`偏大，可以尝试将红线处数值调小。

当显示器能完美正常显示图像时就可以开始下一步啦！

## 检查跳帧问题 ##

部分显示器在设置了一个较高的刷新率后仍正常显示，但是会出现跳帧问题，即显卡输出给显示器的帧显示器并没有显示就丢掉了。这种情况下显示器很可能没有工作在你设定的刷新率下。

让我们打开 [UFO Test](https://www.testufo.com/frameskipping)
同时准备一个手机或者任何能拍照的设备。
*多屏用户注意：由于软件限制，你可能需要将超频的显示器暂时设置为主显示器*

进入后点击红圈中的全屏按钮

![UFO test](/static/monitor-overclocking/UFOTEST.png)

待屏幕中心的蓝色提示消失后使用手机或其它设备拍摄屏幕。（如果有可能，建议使用专业模式，降低iso，延长快门时间）

![成功样本](/static/monitor-overclocking/good_example.jpg)

拍摄出的照片若像上图，白色色块相连接，说明显示器能够在超频后的刷新率下正常显示。恭喜你，显示器超频完成啦！享受高刷新率的屏幕吧！（显示器坏了别找我）
如果白色色块中间出现没有亮起的黑色区域，说明你的屏幕并不能真正工作在该刷新率下，出现了跳帧问题。你很可能需要降低刷新率从头来过，或者……干脆换个显示器吧！(≧∀≦)ゞ