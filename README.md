# iot

# TEMP USING THINGSPEAK
```
#include "ThingSpeak.h"
#include <ESP8266WiFi.h>

//----------- Enter you Wi-Fi Details---------//
char ssid[] = "staff"; //SSID
char pass[] = "pass123$"; // Password
//-------------------------------------------//

WiFiClient  client;

unsigned long myChannelNumber = 1723172; // Channel ID here
const int FieldNumber = 1;
const char * myWriteAPIKey = "TW1I6WILHE3MAKCE"; // Your Write API Key here

void setup()
{
  Serial.begin(115200);
  WiFi.mode(WIFI_STA);
  ThingSpeak.begin(client);
}
void loop()
{
  if (WiFi.status() != WL_CONNECTED)
  {
    Serial.print("Attempting to connect to SSID: ");
    Serial.println(ssid);
    while (WiFi.status() != WL_CONNECTED)
    {
      WiFi.begin(ssid, pass);
      Serial.print(".");
      delay(5000);
    }
    Serial.println("\nConnected.");
  }
  int ADC;
  float temp = (analogRead(A0) * 3.3/1023) * 100;

  Serial.print("Temperature = ");
  Serial.print(temp);
  Serial.println(" *C");
  delay(1000);
  ThingSpeak.writeField(myChannelNumber, FieldNumber, temp, myWriteAPIKey);
  delay(1000);
}

```
![image](https://user-images.githubusercontent.com/82636710/170914967-49dd326e-e34f-4627-96df-68c0615a86d8.png)


# TEMPERATURE

```
int val;
int tempPin=1;
void setup(){
  Serial.begin(9600);
}
void loop(){
  val=analogRead(tempPin);
  float mv=(val/1024.0)*5000;
  float cel=mv/10;
  float farh=cel*9/5+32;
   Serial.print("temperature=");
   Serial.print(cel);
   Serial.print("*C");
   Serial.println();
   Serial.print("temperature=");
   Serial.print(farh);
   Serial.print("*F");
   Serial.println();
  delay(1000);
}
```
![image](https://user-images.githubusercontent.com/82636710/170915500-16fa9921-a7c5-4c9c-92a6-02efb515b401.png)


# ULTRASONIC SENSOR

```
// C++ code
//
int echoPin=2;
int trigPin=3;
long duration;
int distance;
void setup(){
  Serial.begin(300);
}
void loop(){
  digitalWrite(trigPin,LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin,HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin,LOW);
  duration=pulseIn(echoPin,HIGH);
  distance=duration*0.034/2;
  Serial.print("Distance:");
  Serial.print(distance);
  Serial.print("cm");
  Serial.println();
  delay(1000);
}
```

![image](https://user-images.githubusercontent.com/82636710/170916307-3ee70007-fa82-48b0-8e58-b70449285b93.png)

# LED

```
const int LED1=9;
const int LED2=10;
void setup()
{
  pinMode(LED1, OUTPUT);
  pinMode(LED2,OUTPUT);
}

void loop()
{
  digitalWrite(LED1, HIGH);
  delay(1000); 
  digitalWrite(LED1, LOW);
  digitalWrite(LED2,HIGH);
  delay(1000); 
  digitalWrite(LED2,LOW);
}
```

![image](https://user-images.githubusercontent.com/82636710/170915745-8e26bc9e-bc7e-47e6-8fb9-075261dce789.png)

# PIR SENSOR

```
// C++ code
#include <Servo.h>
int sensorState=0;
Servo servo1;
void setup()
{
  pinMode(7,INPUT);
  servo1.attach(11);
}

void loop()
{
  sensorState=digitalRead(7);
  if(sensorState==HIGH){
    servo1.write(360);
  }
  else{
    servo1.write(90);
  }
}
```
![image](https://user-images.githubusercontent.com/82636710/170915523-665a2580-47b7-4c36-89a2-568f0386ecf3.png)


# LED USING MIT

```
char inputByte;
void setup() {
 Serial.begin(9600);
 pinMode(13,OUTPUT);
}
void loop() {
while(Serial.available()>0){
  inputByte= Serial.read();
  Serial.println(inputByte);
  if (inputByte=='1'){
  digitalWrite(13,HIGH);
  }
  else if (inputByte=='0'){
  digitalWrite(13,LOW);
  } 
  }
}
```
![image](https://user-images.githubusercontent.com/82636710/170915189-4c0f16c7-b8f1-4b09-a706-29e0b16b5ad2.png)
