
### LCD顯示溫度感應器的溫度;若溫度<38 綠LED亮; 若大於38度, 紅色LED亮

#### 接線圖(<38 綠燈亮)
![image](https://user-images.githubusercontent.com/17948436/139274118-8bb2ee15-b51b-43ce-80dd-d8cd604acec3.png)


#### 接線圖(>=38 紅燈亮)
![image](https://user-images.githubusercontent.com/17948436/139274016-26bc42d0-e6df-48df-b50c-3c0ffb5d195c.png)

### code 
```c
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
float tempC, reading,voltage;
int RLED = 9;
int GLED = 8;
void setup() {
  lcd.begin(16, 2);
  pinMode(A1, INPUT); // Read analog voltage level (2^10)
  pinMode(RLED, OUTPUT);
  pinMode(GLED, OUTPUT);
  Serial.begin(9600);	

}

void loop() {
  reading = analogRead(A1);  // read analog level level (2^10)
  voltage = (reading/1024.0) * 5.0;
  tempC = (voltage - 0.5) * 100.0;

  lcd.setCursor(0,0);  
  lcd.print("TMP Sensor Demo");
  //實作
  if(tempC<38)
  {
    digitalWrite(RLED, LOW);
    digitalWrite(GLED, HIGH); 
  }
  else
  {
    digitalWrite(RLED, HIGH);
    digitalWrite(GLED, LOW);
  }

  lcd.setCursor(0,1);
  lcd.print("Tmp:");
  lcd.print(tempC);
  lcd.print(" C");
  delay(500);
  lcd.clear();
  Serial.println(reading);
  Serial.println(voltage);  
}
```
