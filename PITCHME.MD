# 如题

## 目的
- 获取数据
1. 温度
1. 湿度

## demo需要的硬件
- ESP8266开发板*1，预计TB售价20块不到
- DHT11 温湿度传感器*1，预计TB售价3块
- 实验用的面包板*2和面包线几根
- 5k 欧姆的电阻一个，（按照DHT11的手册推荐使用）

## 组装方法
如下图

![](http://oi16bpd89.bkt.clouddn.com/201709092325_611.png)

实物图

![](http://oi16bpd89.bkt.clouddn.com/201709092327_154.png)

这里比较好理解，电源供给从8266的3.3V连接带DHT11的vcc，地线从8266的GND连接到DHT11的GND，然后在本次说明中，dht11的data线和ESP8266的D2口（GPIO4）相连，这里的5K电阻是参考了DHT11文档中推荐的连接用上的、

## 读取温湿度的Code


```
import dht
import machine
from time import sleep

d = dht.DHT11(machine.Pin(4))
d.measure()

while True:
    sleep(1)
    print ("temp is [%s]" % str(d.temperature()))
    print ("hum is [%s]" % str(d.humidity()))
    print ("\r")
    sleep(1)
```

再次附上8266的PIN脚图


![](http://oi16bpd89.bkt.clouddn.com/pinpin.png)

