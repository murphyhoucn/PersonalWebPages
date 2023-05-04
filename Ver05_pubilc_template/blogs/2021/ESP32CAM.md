![image-20211116225204943](https://gitee.com/murphyhou/picgo/raw/master/ESP/image-20211116225204943.png)

![image-20211116225239847](https://gitee.com/murphyhou/picgo/raw/master/ESP/image-20211116225239847.png)

<img src="https://gitee.com/murphyhou/picgo/raw/master/ESP/image-20211116225315992.png" alt="image-20211116225315992" style="zoom:150%;" />

![image-20211116225355894](https://gitee.com/murphyhou/picgo/raw/master/ESP/image-20211116225355894.png)

![image-20211116225431044](https://gitee.com/murphyhou/picgo/raw/master/ESP/image-20211116225431044.png)

<img src="https://gitee.com/murphyhou/picgo/raw/master/ESP/%E5%BC%95%E8%84%9A%20(2).png" alt="引脚 (2)" style="zoom:150%;" />

![image-20211116225450167](https://gitee.com/murphyhou/picgo/raw/master/ESP/image-20211116225450167.png)




![注意](https://gitee.com/murphyhou/picgo/raw/master/ESP/%E6%B3%A8%E6%84%8F.png)

![image-20211116225548324](https://gitee.com/murphyhou/picgo/raw/master/ESP/image-20211116225548324.png)

![img](https://gitee.com/murphyhou/picgo/raw/master/ESP/ESP32-CAM-FTDI-programmer-5V-supply.png)









# LED1

RST按钮旁边有一个板载红色LED。该LED内部连接到GPIO 33。您可以使用此LED指示正在发生的事情。例如，如果连接了Wi-Fi，则LED为红色，反之亦然。

![image-20211118175859160](https://gitee.com/murphyhou/picgo/raw/master/ESP/image-20211118175859160.png)

<img src="https://gitee.com/murphyhou/picgo/raw/master/ESP/ESP32-CAM-AI-Thinker-Module-Red-LED-built-in.jpg" alt="ESP32-CAM-AI-Thinker-Module-Red-LED-built-in" style="zoom:150%;" />

``` C
void setup() {
  pinMode(33, OUTPUT);
  //digitalWrite(33, HIGH);// 不亮
  digitalWrite(33, LOW);// 亮
}

void loop() {

}
```



# FLASH LED

DATA1 /手电筒  GPIO 4

![image-20211118175931265](https://gitee.com/murphyhou/picgo/raw/master/ESP/image-20211118175931265.png)

![image-20211118180134693](https://gitee.com/murphyhou/picgo/raw/master/ESP/image-20211118180134693.png)

```C

void setup() {
  pinMode(4, OUTPUT);
  digitalWrite(4,LOW);//不亮
  //digitalWrite(4,HIGH);//亮
}

void loop() {
}
```

