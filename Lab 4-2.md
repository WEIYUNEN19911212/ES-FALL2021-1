### 用七段顯示器, 顯示 . →1→ ... → 9 → 0 → 全滅, 狀態改變的間隔時間為0.5秒

#### 接線圖：
![image](https://user-images.githubusercontent.com/17948436/139261838-55fffbe8-15f4-45f5-aaa2-5ad413d9f927.png)

#### 
```` c
// 七段顯示器製作顯示 . →1→ ... → 9 → 0 → 全滅
byte digits[10][7] = { 
  { 1,1,1,1,1,1,0 },  // = 0
  { 0,1,1,0,0,0,0 },  // = 1
  { 1,1,0,1,1,0,1 },  // = 2
  { 1,1,1,1,0,0,1 },  // = 3
  { 0,1,1,0,0,1,1 },  // = 4
  { 1,0,1,1,0,1,1 },  // = 5
  { 1,0,1,1,1,1,1 },  // = 6
  { 1,1,1,0,0,0,0 },  // = 7
  { 1,1,1,1,1,1,1 },  // = 8
  { 1,1,1,0,0,1,1 }   // = 9
};

void setup() {    
  pinMode(1, OUTPUT);  
  pinMode(2, OUTPUT);
  pinMode(3, OUTPUT);
  pinMode(4, OUTPUT);
  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(8, OUTPUT);
  sevenSegWrite(0); 
}


void sevenSegWrite(byte digit) {
  byte pin = 1;
  for (byte seg = 0; seg < 7; ++seg) {    
    digitalWrite(pin, digits[digit][seg]);
    ++pin;
  }
}

void loop() {
  for (byte digit = 0; digit <= 9; ++digit) {
    delay(500);
    sevenSegWrite(digit == 9?0:digit+1);     
  }
  delay(1000);
}
````
