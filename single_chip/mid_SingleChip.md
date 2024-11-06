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
Servo servoLeft;
Servo servoRight;

void setup(){
    servoLeft.attach(13);
    servoRight.attach(12);
}

void forward(int T){
    servoLeft.writeMicroseconds(1700);
    servoRight.writeMicroseconds(1300);
    delay(T);
}
void turnLeft(int T){
    servoLeft.writeMicroseconds(1300);
    servoRight.writeMicroseconds(1300);
    delay(T);
}
void turnRight(int T){
    servoLeft.writeMicroseconds(1700);
    servoRight.writeMicroseconds(1700);
    delay(T);
}
void backward(int T){
    servoLeft.writeMicroseconds(1300);
    servoRight.writeMicroseconds(1700);
    delay(T);
}

void disableServos(){
    servoLeft.detach();
    servoRight.detach();
}
```

## 第四題 認證第一關跑馬燈的程式設計
```
int LedPin[] = {6, 7, 8, 9, 10, 11, 12 ,13};    //定義腳位
int i;

void setup(){
    for(i=0; i<8; i++){
        pinMode(LedPin[i], OUTPUT); //設定LED腳位為輸出
    }
    pinMode(3, INPUT);              //設定按鈕腳位3為輸入
}
    
void loop(){
       while(digitalRead(3)!=1);

    while(true){
        for(i = 0; i<8; i++){
            digitalWrite(LedPin[i], HIGH);
            delay(1000);
            digitalWrite(LedPin[i], LOW);
        }
        tone(4, 1047, 1000);
        delay(1000);
    }
}


```



