# 期中考

## 第一題 什麼是單晶片？
- 中央處理器、儲存器、輸入輸出、計數器、控制單元的集合
- 優點：體積小、低成本、高度整合性、易操作

## 第二題 有關Arduino UNO的規格特色問答
|規格||
|:---|---:|
|微控制器|ATmega|
|數位I/O腳位|14個(其中6個支援PWM輸出)|
|類比輸入腳位|6個|
|D/C Current per I/O Pin|40mA|
|Flash記憶體|32KB|
|SRAM|2KB|
|EEPROM|1KB|
|時脈|16MHZ|

|腳位I/O|輸入Input|輸出Ouput|晶片腳位Pin X|
|:---|:-:|:-:|:-:|
|D3|Digital|Digital,Analog|P3
|D5|Digital|Digital,Analog|P6
|D6|Digital|Digital,Analog|P6
|D9|Digital|Digital,Analog|P9
|D10|Digital|Digital,Analog|P10
|D11|Digital|Digital,Analog|P11

## 第三題 伺服器馬達控制程式設計
```
# include<Servo.h>

Servo myServo;  //創建Servo物件

vois setup(){
    myServo.attach(9);   //將伺服馬達連接到9號腳位
}

void loop(){
    myServo.write(0);   //轉到0度
    delay(1000);        //停1秒
    myServo.write(90);
    delay(1000);
    myServo.write(180)
    delay(1000)
}

```

## 第四題 認證第一關跑馬燈的程式設計
```
const int ledPins[] = {2, 3, 4, 5, 6, 7, 8};    //定義腳位
const int numLeds = sizeof(ledPins)

```


