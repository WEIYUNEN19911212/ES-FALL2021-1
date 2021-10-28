###  LCD顯示"Hello" + 你的英文名字 (e.g., "Hello Horace")
#### 接線圖：
![image](https://user-images.githubusercontent.com/17948436/139263193-b49e308d-3aaa-489e-936e-707ec5b9b74d.png)

#### code
```` c
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  lcd.begin(16, 2);
  lcd.print("hello, Juncheng Liu!");
}

void loop() {
  lcd.setCursor(0, 1);
  lcd.print(millis() / 1000);
}
 
````
