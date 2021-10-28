### ### Lab 4-4 整合超音波感測器 + LCD: 參考之前的實作, 完成以下任務:

1. **將超音波感測器傳回的距離, 在LCD上面顯示,** 
2. **同時也和之前的實作一樣, 在序列輸出.** 
3. **另外, 當物體的距離小於150cm時, 則亮紅色LED, 否則亮綠色LED**


#### 接線圖：
![image](https://user-images.githubusercontent.com/17948436/139267951-973c88bf-692b-4395-a511-8ff97e982094.png)

#### code
````c
/*
Developed for Embedded System Course, VNU by Horace. Fall 2021
*/

#include <LiquidCrystal.h> //LCD library

#define echo 7
#define trig 7

float  duration; // time taken by the pulse to return back
float  dd; // oneway distance travelled by the pulse
int RLED = 9;
int GLED = 8;
LiquidCrystal lcd(12, 11, 5, 4, 3, 2); 

void setup() {
  pinMode(RLED, OUTPUT);
  pinMode(GLED, OUTPUT);
  Serial.begin(9600);
  lcd.begin(16, 2);

}

void loop() { 

  time_Measurement();
  dd = duration * 0.01723;   
  lcd.clear();
  lcd.setCursor(0, 0);
  Serial.print("Distance, cm: ");
  Serial.print(dd);
  Serial.println();
  /*
		待完成
*/

  if(dd<150){
    digitalWrite(RLED, HIGH);
    digitalWrite(GLED, LOW);
  }
  else{
    digitalWrite(RLED, LOW);
    digitalWrite(GLED, HIGH);
  }
}

void time_Measurement()
{ //function to measure the time taken by the pulse to return back
  pinMode(trig, OUTPUT);
  digitalWrite(trig, LOW);
  delayMicroseconds(2);  
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);
  pinMode(echo, INPUT);  
  duration = pulseIn(echo, HIGH);
}
````
