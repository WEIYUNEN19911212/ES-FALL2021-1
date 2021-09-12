# 實作2-2, RGB LED燈全彩模組, 分別讓LED輪流表現正紅、正綠、正藍，三個顏色，時間間隔1秒鐘。並且觀查LED顏色和波形或是電壓有什麼關連性? 可將個人說明在更新GitHub時一起加入. (互動2), (2021-09-05)

### 接線圖
![image](https://user-images.githubusercontent.com/17948436/132971879-2acb38e5-0b8e-4c78-b4fd-1cb8bdb831ed.png)

### c code
```
int R = 9;
int G = 10;
int B = 11;


void setup()
{
  pinMode(13, OUTPUT);

  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);  


}

void loopFunc(int color,bool lightUp){
  analogWrite(R, 0);
  analogWrite(B, 0);
  analogWrite(G, 0);
  if(lightUp){
    //漸亮
    for (int i = 0; i<= 255; i++)
    {    
      analogWrite(color, i);
      delay(10);
    } 
  }
  else{
    //漸暗
    for (int i = 255; i>= 0; i--)
    {
      analogWrite(color, i);
      delay(10); 
    } 
  }
}

void loop()
{
  loopFunc(R,true);
  delay(500);
  loopFunc(G,true);
  delay(500);
  loopFunc(B,true);
  delay(500);

  loopFunc(R,false);
  delay(500);
  loopFunc(G,false);
  delay(500);
  loopFunc(B,false);
  delay(500);
}
```
