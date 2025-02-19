```
#include<Servo>
Servo servoLeft;
Servo servoRight;

void setup(){
    servoLeft.attach(12);
    servoRight.attach(13);

    servoLeft.writeMicroseconds(1700);
    servoRight.writeMicroseconds(1300);
    delay(2000);

    servoLeft.writeMicroseconds(1300);
    servoRight.writeMicroseconds(1300);
    delay(2000);

    servoLeft.writeMicroscconds(1700);
    servoright.writeMicroscconds(1700);
...
    servoLeft.detach();
    servoRight.detach();
}
void loop(){
}
```

```


```