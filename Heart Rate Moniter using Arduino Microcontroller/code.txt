#include<LiquidCrystal.h> 
//LiquidCrystal lcd(8,9,10,11,12,13); 
LiquidCrystal lcd(8,9,13,12,11,10); 
int SEN1  = A0; 
int SEN2  = A1; 
int SEN3  = A2; 
int SEN4  = A3; 
String webdata="0000"; 
void setup() 
{ 
lcd.begin(16,2); 
Serial.begin(9600); 
//pinMode(A0,INPUT); 
//pinMode(A1,INPUT); 
//pinMode(A2,INPUT); 
//pinMode(A3,INPUT); 
pinMode(2,OUTPUT); // FROM ONLINE 
pinMode(3,OUTPUT); 
pinMode(4,INPUT); 
pinMode(5,OUTPUT); 
pinMode(6,OUTPUT); // FROM SENSOR VALUE 
pinMode(7,OUTPUT); 
pinMode(A5,OUTPUT); 
lcd.setCursor(0,0); 
lcd.print("HEARTRATE SENSOR"); 
lcd.setCursor(0,1); 
lcd.print("   MONITERING"); 
delay(3000); 
lcd.clear(); 
} 
void loop() 
{ 
//lcd.clear(); 
lcd.setCursor(3,0);// column, row 
lcd.print("HAERTRATE SENSOR");  
lcd.setCursor(0,1); 
lcd.print("   
 "); 
int x = map(analogRead(SEN1),0,1024,50,100); 
String y=""; 
lcd.setCursor(4,1); 
lcd.print(x);  
if(x > 80) 
{ 
digitalWrite(2,HIGH); 
y=" High"; 
lcd.setCursor(10,1); 
lcd.print("HIGH  "); 
} 
else 
{ 
} 
digitalWrite(2,LOW); 
y=" NORMAL "; 
lcd.setCursor(10,1); 
lcd.print("NORMAL "); 
Serial.print("Field1="); 
Serial.print(x); 
Serial.print(y); 
Serial.print("&Field2=00"); 
Serial.println(" "); 
//delay(1000);   
delay(2500); 
} 