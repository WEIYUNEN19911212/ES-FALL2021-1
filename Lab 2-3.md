# 實作2-3, 讓你的RGB LED燈全彩模組也可會"呼吸"
### 接線圖
![image](https://user-images.githubusercontent.com/17948436/132971267-ba832e3a-1714-454b-97e8-97a18cc894c8.png)


### code
 ```c
int R = 9;
int G = 10;
int B = 11;

int DR = 2;
int DG = 4;
int DB = 7;

void setup()
{
  pinMode(13, OUTPUT);
  
  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);  
  
  pinMode(DR, OUTPUT);
  pinMode(DG, OUTPUT);
  pinMode(DB, OUTPUT);   
}

void loop()
{
  digitalWrite(13, 1); 
  
  delay(1000); 
  
  digitalWrite(DR, 1);
  digitalWrite(DG, 0);
  digitalWrite(DB, 0);
  delay(1000);
  digitalWrite(DR, 0);
  digitalWrite(DG, 1);
  digitalWrite(DB, 0);  
  delay(1000);
  digitalWrite(DR, 0);
  digitalWrite(DG, 0);
  digitalWrite(DB, 1);  
  delay(1000);

  digitalWrite(13, 0); 
  digitalWrite(DR, 0); 
  digitalWrite(DG, 0); 
  digitalWrite(DB, 0); 
  delay(1000);
  
  //漸亮
  for (int i = 0; i<= 255; i++)
  {
  	analogWrite(R, i);
		analogWrite(G, 0);
		analogWrite(B, 0);
    delay(10);
  } 

  //漸暗
  for (int i = 255; i>= 0; i--)
  {
  	analogWrite(R, i);
		analogWrite(G, 0);
		analogWrite(B, 0);
    delay(10); 
  }  
  delay(1000);
}
 ```
