### 什麼是4X4鍵盤? 我們在哪裡有看到這樣的裝置呢? 要如何控制?


#### 接線圖
![image](https://user-images.githubusercontent.com/17948436/139567164-48df35d5-83b7-4d7e-9e5c-cecdfdcc0b86.png)


#### code
``` c
// For Embedded System course, VNU, Fall 2021 

#include <Keypad.h>
#include <LiquidCrystal.h>
// 5:RS, 4:E, 3:DB4, 2:DB5, A4:DB6, A5: DB7
// LCD若只顯示文字，只須使用4-bit模式即可 (LCD腳位DB0, DB1, DB2, DB3就不用接了。)
LiquidCrystal lcd(5, 4, 3, 2, A4, A5);

const byte ROWS = 4; // 4列數(橫的)
const byte COLS = 4; // 4行數(直的)
char keys[ROWS][COLS] = {
  {'1','2','3','A'},
  {'4','5','6','B'},
  {'7','8','9','C'},
  {'*','0','#','D'}
};

byte rowPins[ROWS] = {A0, A1, 11, 10}; //定義列的腳位
byte colPins[COLS] = {9, 8, 7, 6}; //定義行的腳位

int LCDCol = 0;
int LCDRow = 0;

Keypad keypad = Keypad( makeKeymap(keys), rowPins, colPins, ROWS, COLS );

void setup(){
  Serial.begin(9600);
  lcd.begin(16, 2);
  lcd.setCursor(LCDCol, LCDRow);
}

void loop(){
  char key = keypad.getKey(); //讀取 Keypad 的輸入

  //實作
  if (key){
    lcd.print(key);
    LCDCol++;
    if(LCDCol > 15){
      ++LCDRow;
      LCDCol = 0;
      if(LCDRow> 1){
        LCDRow = 0;
        lcd.clear();
      }
      lcd.setCursor(LCDCol, LCDRow);
    }

    Serial.println(LCDCol);


  } // end if
} // end loop
```
