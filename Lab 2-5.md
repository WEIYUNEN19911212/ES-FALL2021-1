# 實作2-5 按下按鍵, Green LED亮 & Red LED滅; 放開按鍵
### 接線圖
![image](https://user-images.githubusercontent.com/17948436/134792208-025ad442-d66c-444e-b9ee-250df28ec14c.png)
```c
int ledPinG = 13 ;
int ledPinR = 8 ;
int buttonPin = 2 ;
void setup()
{
  pinMode(ledPinG, OUTPUT);
  pinMode(ledPinR, OUTPUT);
  pinMode(buttonPin, INPUT);
  Serial.begin(11500);

}

void loop()
{ 
Serial.print(digitalRead(buttonPin)) ;
  if(digitalRead(buttonPin) == 1)
  {
    digitalWrite(ledPinR, LOW);
    digitalWrite(ledPinG, HIGH);
  }
  else{
  digitalWrite(ledPinR, HIGH);
  digitalWrite(ledPinG, LOW);
  }
}
```
