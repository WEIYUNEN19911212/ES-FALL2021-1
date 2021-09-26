# 請使用Arudino, 通過Serial印出9X9乘法表, 計算時亮紅色LED, 綠色LED慢慢變亮亮完成時全亮, 並且紅色LED OFF, 細節可參考以下Demo作法
### 接線圖
![image](https://user-images.githubusercontent.com/17948436/134793396-8d58f139-b4d7-4fbf-9ac4-fe545f9d604f.png)

```c

int ledR = 13;
int ledG = 11;
void setup()
{
  pinMode(ledR, OUTPUT);
  pinMode(ledG, OUTPUT);
  Serial.begin(9600);
}

void loop()
{     
 int brightness = 0;
 for(int y=1;y<=9;y++){
   for(int x=1;x<=9;x++){
     Serial.print(x);
     Serial.print("x");
     Serial.print(y);
     Serial.print("=");
     Serial.println(x*y);

     if(brightness>=255)
     {
       brightness = 255;
       analogWrite(ledR,0);
     }
     analogWrite(ledR,brightness);
     analogWrite(ledG,brightness);
     brightness+=5;
   }
 }
}
```
