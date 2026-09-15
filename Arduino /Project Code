#include <OneWire.h>
#include <DallasTemperature.h>

#include <Wire.h> 
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// تعريف الدبابيس
#define ONE_WIRE_BUS 2    
#define IR_SENSOR 3
#define buzzer_1 5         
#define buzzer_2 6 
#define LED_YELLOW 7
#define LED_GREEN 8
#define LED_RED 9
#define RELAY_PUMP 10
#define RELAY_FAN 11
#define RELAY_HEATER 12

OneWire oneWire(ONE_WIRE_BUS);
DallasTemperature sensors(&oneWire);


bool isRunning = true ;      // حالة الجهاز (شغال ولا لأ)

void flash() {

digitalWrite(LED_GREEN, 1);
delay(200);
digitalWrite(LED_GREEN, 0);
delay (200);
}

void setup() {
  lcd.init();   
  lcd.backlight();
  Serial.begin(9600);
  pinMode(IR_SENSOR, INPUT);
  pinMode(RELAY_HEATER, OUTPUT);
  pinMode(RELAY_PUMP, OUTPUT);
  pinMode(RELAY_FAN,OUTPUT);
  pinMode(LED_GREEN, OUTPUT);
  pinMode(LED_YELLOW, OUTPUT);
  pinMode(LED_RED, OUTPUT);
  
  pinMode(buzzer_1, OUTPUT);
  pinMode(buzzer_2, OUTPUT);

  sensors.begin();
  Serial.println("System Started...");

  digitalWrite(LED_GREEN, 0);
  digitalWrite(LED_YELLOW, 0);
  digitalWrite(LED_RED, 0);

  digitalWrite(RELAY_PUMP, 1);
  digitalWrite(RELAY_FAN, 1);
  digitalWrite(RELAY_HEATER, 0);

}


void loop() {
  sensors.requestTemperatures();
  float temp = sensors.getTempCByIndex(0);
  int irState = digitalRead(IR_SENSOR);    
  Serial.println(irState);
  // طباعة درجة الحرارة وحالة الحساس للمراقبة
  Serial.print("Temperature: ");
  Serial.print(sensors.getTempCByIndex(0));
  Serial.print("°C  |  ");

  Serial.print((sensors.getTempCByIndex(0) * 9.0) / 5.0 + 32.0);
  Serial.println("°F");
  lcd.setCursor(0,0);
  lcd.print("Temp: ");
  lcd.print(temp);
  lcd.print(" C_    ");

 if (irState == 0 ){
   digitalWrite(LED_GREEN, 0);
   digitalWrite(LED_YELLOW, 0);
   digitalWrite(LED_RED, 1);
   lcd.setCursor(15,0);
   lcd.print("R");
  
  }
 else {
  if ( temp <= 40 ) {
   digitalWrite(LED_GREEN, 1);
   digitalWrite(LED_YELLOW, 0);
   digitalWrite(LED_RED,0);
    
   lcd.setCursor(15,0);
   lcd.print("G");
   lcd.setCursor(0,1);
   lcd.print("Normal     ");
   digitalWrite(RELAY_PUMP, 1); 
   digitalWrite(RELAY_FAN, 1); 
   noTone(5);
   noTone(6);

   }

   else if (temp > 40 && temp <= 45) {

   digitalWrite(LED_YELLOW, 0);
   digitalWrite(LED_RED, 0);
   lcd.setCursor(14,0);
   lcd.print("GF");
   lcd.setCursor(0,1);
   lcd.print("Pre Warning    ");

   flash();
   digitalWrite(RELAY_PUMP, 0); 
   digitalWrite(RELAY_FAN, 0);
   tone(5, 440);
   noTone(6);
   }

  else if (temp >= 45 && temp < 50) {
   digitalWrite(LED_GREEN, 0);
   digitalWrite(LED_YELLOW, 1);
   digitalWrite(LED_RED, 0);

   lcd.setCursor(15,0);
   lcd.print("Y");
   lcd.setCursor(0,1);
   lcd.print("Warning    ");
   digitalWrite(RELAY_PUMP, 0); 
   digitalWrite(RELAY_FAN, 0);
   tone(5, 440);
   noTone(6);
   }
 else if (temp > 50){
   digitalWrite(LED_GREEN, 0);
   digitalWrite(LED_YELLOW, 0);
   digitalWrite(LED_RED, 1); 

   lcd.setCursor(15,0);
   lcd.print("R");
   lcd.setCursor(0,1);
   lcd.print("Danger       ");
   digitalWrite(RELAY_PUMP, 0); 
   digitalWrite(RELAY_FAN, 0);
   noTone(5);
   tone(6, 700);
   }

 }

 if ( temp < 36 ) {
     digitalWrite(RELAY_HEATER, 0);
      }

  else {
    digitalWrite(RELAY_HEATER, 1);
  }

 
 }
