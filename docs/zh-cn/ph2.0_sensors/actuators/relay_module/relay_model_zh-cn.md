# 继电器模块

![Relay Module](picture/relay_module.png)

## 概述

继电器（Relay）是一种电控制开关，其工作原理基于电磁感应。继电器通常包括一个电磁线圈和一组触点。它具有控制系统（又称输入回路）和被控制系统（又称输出回路）之间的互动关系。通常应用于自动化的控制电路中，用小电流去控制大电流运作的一种“自动开关” ，在电路中起着自动调节、安全保护、转换电路等作用。特别适合于单片机控制强电装置。

当PH2.0接口引脚S输入低电平或者悬空时，继电器断开，即右侧3号引脚（Normally Closed，NC），2号引脚（COM）连通，红色信号灯Signal熄灭；当当PH2.0接口引脚S输入低电平时，继电器断开，右侧1引脚（Normally Open，NO），2号引脚（COM）连通，红色信号灯Signal亮起。

## 工作原理

![relay_principle](./picture/relay_principle.gif)

**电磁线圈**： 继电器内部包含一个电磁线圈，通常由绕制在绝缘芯片上的细导线组成。当通过线圈通电时，产生电磁场。

**磁性吸引**： 电磁场会使继电器中的铁芯（或磁性材料）受到磁性吸引，导致铁芯在电磁力的作用下移动。

**触点操作**： 铁芯的移动会导致机械部分的运动，最终使触点（开关）发生动作。继电器通常有常开（Normally Open，NO）和常闭（Normally Closed，NC）两组触点。

**常闭触点**： 在继电器未通电时处于闭合状态，当电磁线圈通电时，触点打开。

**常开触点**： 在继电器未通电时处于打开状态，当电磁线圈通电时，触点闭合。

**电气隔离**： 继电器的主要作用之一是提供电气隔离。通过电磁原理，可以在控制信号与被控制电路之间提供隔离，从而使得不同电路之间的电流不会相互影响。

<a href="zh-cn/ph2.0_sensors/actuators/relay_module/HK4100F-DC3V-SHG_datesheet.pdf" target="_blank">点击查看继电器规格书</a>

## 原理图

![relay_module_sch](picture/relay_module_sch.png)

<a href="zh-cn/ph2.0_sensors/actuators/relay_module/relay_module_sch.pdf" target="_blank">点击查看原理图</a>

## 模块参数

* 供电电压：3 ~ 5V
* 连接方式：PH2.0 3pin接口
* 模块尺寸：38.4*22.4mm
* 触发方式：兼容3V ~ 5V高电平触发
* 工作温度：-25℃ ~ +70℃
* 电器参数：
  - 交流：‌250VAC / 3A
  - 直流：‌30VDC / 3A
  - 线圈电阻：约 ‌45Ω (±10%)
  - ‌线圈功率‌：约200mW
  - 动作时间：最大6ms
  - 释放时间‌：最大 ‌4ms
* 安装方式：M4螺钉兼容乐高插孔

| 引脚名称 | 描述           |
| -------- | -------------- |
| V        | 3 ~ 5V电源输入 |
| G        | GND地线        |
| S        | 信号引脚       |

## 机械尺寸

![relay_assembly](./picture/relay_assembly.png)

<a href="zh-cn/ph2.0_sensors/actuators/relay_module/relay_module_3d.zip" download>下载继电器模块3D文件</a>

## 示例程序

```c
const kRealyPin = A3             // 设置继电器端口为A3

void setup() {
    pinMode(kRealyPin, OUTPUT);  // 设置继电器端口为输出模式
}
void loop() {
    digitalWrite(kRealyPin, HIGH);  // 设置继电器端口为高电平
    delay(2000);
    digitalWrite(kRealyPin, LOW);
    delay(2000);
}
```
