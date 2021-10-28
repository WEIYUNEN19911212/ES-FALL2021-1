# 實作2-4 analogRead(), 1024解析度 (i.e.,10-bit): 可變電阻 + 序列監視器與輸出

### 接線圖
![image](https://user-images.githubusercontent.com/17948436/132971463-d458db73-535d-48dd-af77-1d85a0b7d2bd.png)


### c code
```c
int sensorValue = 0;

void setup()
{
  pinMode(A0, INPUT);
  Serial.begin(9600);

}

void loop()
{
  // read the input on analog pin 0:
  sensorValue = analogRead(A0);
  // print out the value you read:
  Serial.println(sensorValue);
  delay(10); 
}
```
