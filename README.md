# microbit

使用pycharm编写microbit之前，需要安装 pseudo-microbit

需要添加工具 external tool uflash

参数：

```
name: uflash,
Group: Externam Tools
Description: The micro:bit file flash utility
Program: uflash
Arguments: $FileName$
Working directory: $FileDir$
```

同时 `pip install --no-cache --upgrade uflash`

## 图像显示

microPython 有大量的内置图片可以显示在屏幕上

```python
from microbit import *
display.show(Image.HEART)
```

也可以自行创建图像

物理显示器为5*5的矩阵，以下方法表示出来，位置上面的数字表示亮度（0-9,0表示熄灭）

换行之间需要用冒号 : 隔开，也可以写为 `boat = Image("05050:05050:05050:99999:09990")`

### 动画循环

loop 表示是否永久循环，delay表示两帧动画之间显示的延迟，单位毫

`display.show(Image.ALL_CLOCKS, loop=False, delay=200)`

## 按钮

microbit 有两个按钮，分别是 `button_a`和`button_b`

## 输入和输出

引脚 0 的电线接到有源蜂鸣器的正极，引脚 GND 的电线连接到负极
有源蜂鸣器和无源蜂鸣器的区别是，

- 有源蜂鸣器接通电源就能够发声音
- 无源蜂鸣器需要不断的改变电位

## 连接扬声器或者耳机
耳机插头，耳机插头中间有线圈，用来绝缘，

- 前两个部分表示左右声道，
- 第三个部分表示接地，
- 如果有第四部分，则用来影像或麦克风传输
  将 pin0 接到 耳机插头的第一段或第二段（左右声道），第三段接地

### 创作音乐
传递音符给 microbit，
音符 ：`C#:F, 前面的 C 代表声音，后面的 #（1-8）代表音高，F 表示音长`
A-J 可以发音
```python
 tune = ["C4:4", "D4:4", "E4:4", "C4:4", "C4:4", "D4:4", "E4:4", "C4:4",
		"E4:4", "F4:4", "G4:8", "E4:4", "F4:4", "G4:8"]
```

## 移动
移动 microbit 来让其检测处于什么位置
向上(up)，向下(down)，向左(left)，向右(right)，正面朝上(face up)，正面朝下(face down)
自由落体(freefall)，3g(3g)，6g(6g)，8g(8g)，摇动(shake)

## API
### 引脚
模拟信号和数字信号的区别：数字信号是离散型的，模拟信号是连续性的

`read_digital`: 读取数字信号 1 和 0（高电位或低电位）

`read_analog`：读取模拟信号 0 - 1023

`write_digital()`：写入信号，1 代表启动，0 代表 关闭

`write_analog()`：写入信号，0-1023，1023 代表 3.3 V

