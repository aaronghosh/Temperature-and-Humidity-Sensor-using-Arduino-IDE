#include "DHT.h"
#include <Wire.h> 
#include <LiquidCrystal_I2C.h>
#define DHTPIN 2
#define DHTTYPE DHT11
LiquidCrystal_I2C lcd(0x27, 16, 2);
int led1 = 13;
int led2 = 12;
DHT dht(DHTPIN, DHTTYPE);
void setup() {
  Serial.begin(9600);
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  dht.begin(); // initialize the sensor
  
}
void loop() {
  // wait a few seconds between measurements.
  delay(2000);
  // read humidity
  float humi  = dht.readHumidity();
  // read temperature as Celsius
  float tempC = dht.readTemperature();
  // read temperature as Fahrenheit
  float tempF = dht.readTemperature(true);
  // check if any reads failed
  if (isnan(humi) || isnan(tempC) || isnan(tempF)) {
    Serial.println("Failed to read from DHT sensor!");
  } else {
    Serial.print("Humidity: ");
    Serial.print(humi);    
    Serial.print("%");
    Serial.print("  |  "); 
    Serial.print("Temperature: ");
    Serial.print(tempC);
    Serial.print("C ~ ");
    Serial.print(tempF);
    Serial.println("F");
    lcd.begin();
    // Turn on the blacklight and print a message.
    lcd.backlight();
    lcd.print("temperature  "); lcd.print(tempC);
    lcd.setCursor(0, 1);
    lcd.print("humidity  ");
    lcd.print(humi);
    delay(1000);
    if(tempC > 30.00) 
    {   digitalWrite(led2,LOW);
        digitalWrite(led1, HIGH); 
    } else 
    { 
      digitalWrite(led1, LOW);
      digitalWrite(led2, HIGH); 
    }
