 #include <Wire.h> 
#include <LiquidCrystal_I2C.h>

// إعداد الشاشة (العنوان غالباً 0x27 وابعادها 16x2)
LiquidCrystal_I2C lcd(0x27, 16, 2);

const int pirPin = 3;    // طرف الحساس
const int buzzerPin = 9; // طرف البازر
int pirState = LOW;      // حالة الحساس في البداية

void setup() {
  pinMode(pirPin, INPUT);
  pinMode(buzzerPin, OUTPUT);
  
  lcd.begin();
  lcd.backlight();
  
  // رسالة ترحيبية عند التشغيل
  lcd.setCursor(0, 0);
  lcd.print("System Active...");
  delay(2000);
  lcd.clear();
}

void loop() {
  int motion = digitalRead(pirPin); // قراءة الحساس

  if (motion == HIGH) {
    // لو فيه حركة
    digitalWrite(buzzerPin, HIGH); // تشغيل الإنذار
    
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("HEY! I SEE YOU!"); // الجملة الحلوة
    lcd.setCursor(0, 1);
    lcd.print("Motion Detected!");
    
    delay(500); // تنبيه سريع
    digitalWrite(buzzerPin, LOW);
    delay(500); 
    
    pirState = HIGH;
  } else {
    // لو مفيش حركة
    digitalWrite(buzzerPin, LOW);
    
    if (pirState == HIGH) {
      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print("Scanning...");
      pirState = LOW;
    }
  }
}
