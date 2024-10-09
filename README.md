# IOT

# Arduino1

void setup() {
  // put your setup code here, to run once:

}

void loop() {
   { 
pinMode(10, OUTPUT);
}

  digitalWrite(10, HIGH);
  delay(1500);

  digitalWrite(10, LOW);
  delay(500);
}
# Arduino2
int digitalInput;
void setup()
{
 Serial.begin(9600);
}

void loop()
{
  for(int digitalInput=0; digitalInput<255; digitalInput++)
  {
    Serial.print("Digital Input:");
    Serial.println(digitalInput);
    analogWrite(11, digitalInput);
    analogWrite(9, digitalInput);
    analogWrite(6, digitalInput);
  }
}

# Arduino3 Led RGB

#define R 5
#define G 6
#define B 3
int digitalInput;
void setup()
{
  Serial.begin(9600);
  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);
}

void loop(){
 
  analogWrite(R,255); 
  analogWrite(G,0);
  analogWrite(B,0);
  delay(500);
  Serial.print("Vermelho");
  Serial.println(digitalInput);
  
  analogWrite(B,255); 
  analogWrite(G,0);
  analogWrite(R,0); 
	delay(500);
  Serial.print("Verde");
    Serial.println(digitalInput);
  
    analogWrite(B,0); 
  analogWrite(G,255);
  analogWrite(R,0); 
	delay(500);
  Serial.print("Azul");
    Serial.println(digitalInput);
  
   analogWrite(B,0); 
  analogWrite(G,105);
  analogWrite(R,150); 
	delay(500);
  Serial.print("Roxo");
    Serial.println(digitalInput);
  
    analogWrite(B,105); 
  analogWrite(G,0);
  analogWrite(R,150); 
	delay(500);
  Serial.print("Amarelo");
    Serial.println(digitalInput);
}


# ARDUINO 4 LDR

int FOTO=6;
void setup()
{
 pinMode(3, OUTPUT);
 pinMode(A0, INPUT);
  Serial.begin(9600);
}

void loop(){
  analogWrite(3,HIGH);
 int FOTO= analogRead (A0);
      Serial.println(FOTO);
  if (FOTO <=650){
    digitalWrite(3,HIGH);
  Serial.print("ligado");
       delay(3000);
  digitalWrite(3,LOW);
  Serial.print("desligado");
  }
  }


# ARDUINO 5 LDR + RGB

#define R 3
#define G 5
#define B 6

int LDR = 0;

void setup()
{
  pinMode(A0, INPUT);
  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);
  Serial.begin(9600);

}

void loop()
{
 
  int LDR = analogRead(A0);
 
 
 
  if (LDR<=150){
    analogWrite(R, 255);   // vermelho
    analogWrite(G, 0);
    analogWrite(B, 0);
     Serial.println(LDR);
  }
 
  else if(LDR>150 && LDR<=300){
  analogWrite(R, 0);     // verde
  analogWrite(G, 255);
  analogWrite(B, 0);
    Serial.println(LDR);
  }
 
  else if(LDR>300 && LDR<=450){
  analogWrite(R, 0);     // azul
  analogWrite(G, 0);
  analogWrite(B, 255);
  Serial.println(LDR);

  }
 
  else if (LDR>450 && LDR<=600){
  analogWrite(R, 255);   // amarelo
  analogWrite(G, 255);
  analogWrite(B, 0);
  Serial.println(LDR);
  }
 
  else if (LDR>600 && LDR<=750){
  analogWrite(R, 255);     // laranja
  analogWrite(G, 102);
  analogWrite(B, 0);
      Serial.println(LDR);
  }
 
  else if (LDR>750 && LDR<=900){
  analogWrite(R, 199);     // rosa
  analogWrite(G, 21);
  analogWrite(B, 133);
      Serial.println(LDR);
  }
  else{
     analogWrite(R, 0);     // desligado
  analogWrite(G, 0);
  analogWrite(B, 0);
    Serial.println(LDR);
   
  }
      delay(2000);
}


# ARDUINO 6 BUZZER

#define R 3
#define G 5
#define B 6
  int buzzer =8;
void setup()
{
  pinMode(buzzer, OUTPUT);
  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);
  Serial.begin(9600);
}

void loop()
{
 
  tone(buzzer, 200, 1000);
  analogWrite(R,255); 
  analogWrite(G,0);
  analogWrite(B,0);
  delay(500);
  tone(buzzer, 300, 1000);
  analogWrite(B,255); 
  analogWrite(G,0);
  analogWrite(R,0); 
   delay(500);
  noTone(buzzer);
  tone(buzzer, 400, 1000);
  analogWrite(B,0); 
  analogWrite(G,255);
  analogWrite(R,0); 
   delay(500);
  noTone(buzzer);
  tone(buzzer, 500, 1000);
  analogWrite(B,0); 
  analogWrite(G,105);
  analogWrite(R,150); 
   delay(500);
  noTone(buzzer);
  tone(buzzer, 1000, 1000);
  analogWrite(B,105); 
  analogWrite(G,0);
  analogWrite(R,150); 
   delay(500);
  noTone(buzzer);
  delay(500);
}


# ARDUINO 7 ULTRASOUND

int inches =0;
int cm =0;

long readUltrasonciDistance (int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT);
  digitalWrite(triggerPin,LOW);
  delayMicroseconds(2);
  digitalWrite(triggerPin,HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin,LOW);
  pinMode(echoPin,INPUT);
  return pulseIn(echoPin, HIGH);
}
void setup()
{
  pinMode(4, OUTPUT);
  pinMode(8, OUTPUT);
  pinMode(12, OUTPUT);
  Serial.begin(9600);
}
void loop()
{
cm =0.01723 * readUltrasonciDistance(5,7);
  inches =(cm/2.54);
  Serial.print(inches);
  Serial.print("in,");
  Serial.print(cm);
  Serial.print("cm,");
  delay(100);
  
  if(cm<10) {
    digitalWrite(12,HIGH);
    digitalWrite(8,LOW);
    digitalWrite(4,LOW);
  }
  
  
    if(cm<20 && cm>10) {
      
      digitalWrite(8,HIGH);
      digitalWrite(4,LOW);
      digitalWrite(12,LOW);
    }
  
  
    
    
      if(cm>20) {
   
        digitalWrite(4,HIGH);
        digitalWrite(8,LOW);
        digitalWrite(12,LOW);
        }
   
  
 
  
}
# ARDUINO 8 BUZZER+SENSOR+BOTAO+TEMPERATURA
const int buzzer =2;
int inches =0;
int cm =0;
int botao =0;

long readUltrasonciDistance (int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT);
  digitalWrite(triggerPin,LOW);
  delayMicroseconds(2);
  digitalWrite(triggerPin,HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin,LOW);
  pinMode(echoPin,INPUT);
  return pulseIn(echoPin, HIGH);
}
void setup()
{
  pinMode(8, OUTPUT);
  pinMode(11, INPUT);
  pinMode(A0, INPUT);
  Serial.begin(9600);
}
void loop()
{
  botao = digitalRead(11);
  cm =0.01723 * readUltrasonciDistance(5,7);
  inches =(cm/2.54);
  Serial.print(inches);
  Serial.print("in,");
  Serial.print(cm);
  Serial.print("cm,");
  delay(100);
  
  if(cm<20){
      tone(buzzer,130);
      digitalWrite(8,HIGH);
    
      int SensorTemperatura=analogRead(A0);
    float Tensao=SensorTemperatura*5;
    Tensao/=1024;
    float TemperaturaC=(Tensao-0.5)*100;
      Serial.print(TemperaturaC);
      Serial.println("C,");
      
     } else {
      digitalWrite(8,LOW);
    }
  if (botao==HIGH){
    noTone(buzzer);
    digitalWrite(8,LOW);
  }
 # ARDUINO 9 APP
  const int buzzer =8;
int inches =0;
int cm =0;
int botao =0;

long readUltrasonciDistance (int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT);
  digitalWrite(triggerPin,LOW);
  delayMicroseconds(2);
  digitalWrite(triggerPin,HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin,LOW);
  pinMode(echoPin,INPUT);
  return pulseIn(echoPin, HIGH);
}
void setup()
{
  pinMode(12, OUTPUT);
  pinMode(9, INPUT);
  pinMode(A0, INPUT);
  Serial.begin(9600);
}
void loop()
{
  botao = digitalRead(9);
  cm =0.01723 * readUltrasonciDistance(5,7);
  inches =(cm/2.54);
  Serial.print(inches);
  Serial.print("in,");
  Serial.print(cm);
  Serial.print("cm,");
  delay(100);
  
  if(cm<20){
      tone(buzzer,130);
      digitalWrite(11,HIGH);
    
      int SensorTemperatura=analogRead(A0);
    float Tensao=SensorTemperatura*5;
    Tensao/=1024;
    float TemperaturaC=(Tensao-0.5)*100;
      Serial.print(TemperaturaC);
      Serial.println("C,");
      
     } else {
      digitalWrite(12,LOW);
    }
  if (botao==HIGH){
    noTone(buzzer);
    digitalWrite(12,LOW);
  }
  
}


# ARDUINO 10 LCD + TEMPERATURA

#include<LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
void setup()
{
 lcd.begin(16, 2);
}

void loop()
{
    int SensorTemperatura=analogRead(A0);
    float Tensao=SensorTemperatura*5;
    Tensao/=1024;
    float TemperaturaC=(Tensao-0.5)*100;
      Serial.print(TemperaturaC);
      Serial.println("C,");
  lcd.setCursor(5,0);          
  lcd.print(TemperaturaC);
    lcd.setCursor(11,0);          
  lcd.print("C");
  }

# ARDUINO 11 SEMAFORA + LED

#include <LiquidCrystal.h>

// C++ code
//

#include <Wire.h>
#include <LiquidCrystal_I2C.h>

// DEFINIÇÕES
#define endereco  0x20 // Endereços comuns: 0x3F
#define colunas   16
#define linhas    2

// INSTANCIANDO OBJETOS
LiquidCrystal_I2C lcd(endereco, colunas, linhas);

int counter;

void setup()
{
  pinMode(6, OUTPUT);
  pinMode(2, OUTPUT);
  pinMode(3, OUTPUT);
  pinMode(5, OUTPUT);
  pinMode(4, OUTPUT);
 

  lcd.backlight(); // LIGA A ILUMINAÇÃO DO DISPLAY
  lcd.clear(); // LIMPA O DISPLAY
  lcd.noBacklight(); // DESLIGA A ILUMINAÇÃO DO DISPLAY
}

void loop()
{
  lcd.clear();
  lcd.init(); // INICIA A COMUNICAÇÃO COM O DISPLAY
  lcd.backlight(); // LIGA A ILUMINAÇÃO DO DISPLAY
 
  lcd.clear(); // LIMPA O DISPLAY
  lcd.setCursor(0, 0);
  lcd.print("CARRO GREEN ");
  lcd.setCursor(0, 1);
  lcd.print("PEDESTRE RED ");
  digitalWrite(6, HIGH);
  digitalWrite(4, HIGH);
  delay(3000); // Wait for 3000 millisecond(s)
  digitalWrite(6, LOW);
  lcd.clear(); // LIMPA O DISPLAY
  lcd.setCursor(0, 0);
  lcd.print("CARRO YELLOW ");
  lcd.setCursor(0, 1);
  lcd.print("PEDESTRE RED ");
  digitalWrite(3, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(3, LOW);
  digitalWrite(4, LOW);
  lcd.clear(); // LIMPA O DISPLAY
  lcd.setCursor(0, 0);
  lcd.print("CARRO RED ");
  lcd.setCursor(0, 1);
  lcd.print("PEDESTRE GREEN");
  digitalWrite(5, HIGH);
  digitalWrite(2, HIGH);
  delay(2000); // Wait for 2400 millisecond(s)
  digitalWrite(5, LOW);
  digitalWrite(2, LOW);
  for (counter = 0; counter < 6; ++counter) {
    lcd.clear(); // LIMPA O DISPLAY
    lcd.setCursor(0, 0);
    lcd.print("CARRO GREEN ");
    lcd.setCursor(0, 1);
    lcd.print("PEDESTRE RED");
   digitalWrite(6, HIGH);
  digitalWrite(4, HIGH);
  delay(3000); // Wait for 3000 millisecond(s)
  digitalWrite(6, LOW);
  lcd.clear(); // LIMPA O DISPLAY
  lcd.setCursor(0, 0);
  lcd.print("CARRO YELLOW ");
  lcd.setCursor(0, 1);
  lcd.print("PEDESTRE RED ");
  digitalWrite(3, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(3, LOW);
  digitalWrite(4, LOW);
  lcd.clear(); // LIMPA O DISPLAY
  lcd.setCursor(0, 0);
  lcd.print("CARRO RED ");
  lcd.setCursor(0, 1);
  lcd.print("PEDESTRE GREEN");
  digitalWrite(5, HIGH);
  digitalWrite(2, HIGH);
  }
  digitalWrite(13, LOW);
}

# ARDUINO 12 RFID

#include <SPI.h>
#include <MFRC522.h>
#include<LiquidCrystal_I2C.h>


LiquidCrystal_I2C lcd(0x3F,16,2);

 
#define SS_PIN 10
#define RST_PIN 9
#define LED_G 5 //define green LED pin
#define LED_R 6 //define red LED


MFRC522 mfrc522(SS_PIN, RST_PIN);   // Create MFRC522 instance.

 
void setup()
{
  Serial.begin(9600);
  lcd.init();
  lcd.backlight();
  lcd.clear();


  SPI.begin();      // Initiate  SPI bus
  mfrc522.PCD_Init();   // Initiate MFRC522
 
  pinMode(LED_G, OUTPUT);
  pinMode(LED_R, OUTPUT);

  Serial.println("Aproxime o cartão");
 

}
void loop()
{
  // Look for new cards
  if ( ! mfrc522.PICC_IsNewCardPresent())
  {
    return;
  }
  // Select one of the cards
  if ( ! mfrc522.PICC_ReadCardSerial())
  {
    return;
  }

  String content= "";
  byte letter;
  for (byte i = 0; i < mfrc522.uid.size; i++)
  {
     Serial.print(mfrc522.uid.uidByte[i] < 0x10 ? " 0" : " ");
     Serial.print(mfrc522.uid.uidByte[i], HEX);
     content.concat(String(mfrc522.uid.uidByte[i] < 0x10 ? " 0" : " "));
     content.concat(String(mfrc522.uid.uidByte[i], HEX));
  }

  content.toUpperCase();
  if (content.substring(1) == "B0 F0 11 A4" ) //change here the UID of the card/cards that you want to give access
  {
    digitalWrite(LED_G, HIGH);
    lcd.setCursor(1,0);
    lcd.print("Acesso liberado");
    Serial.println();
    delay(3000);
    digitalWrite(LED_G, LOW);
    lcd.clear();
   
  }
 
 else   {

    digitalWrite(LED_R, HIGH);
    lcd.setCursor(1,0);
    lcd.print("Acesso negado");
    delay(3000);
    lcd.clear ();
    digitalWrite(LED_R, LOW);
   
   
  }
}

# ARDUINO  13 PONTENCIOMETRO

int potenciometro = 0;
int potenciometro_ = 0;
 const int inferior = 512; 
 const int superior = 520; 
#include<LiquidCrystal.h>
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
void setup()
{
  
  pinMode(A0, INPUT);
  pinMode(A1, INPUT);
  Serial.begin(9600);
{
 lcd.begin(16, 2);
}
}
void loop()
{
  potenciometro = analogRead(A0);
  if(potenciometro = superior){
  Serial.print(potenciometro);
  Serial.print("x,");
  }
  potenciometro_ = analogRead(A1);
 if(potenciometro_ = inferior){
  Serial.print(potenciometro_);
  Serial.print("y,");
 }
  lcd.setCursor(0,0);          
  lcd.print("EIXO X:"); 
  lcd.setCursor(2,9);          
  lcd.print(potenciometro); 
  delay(3000);
  lcd.clear();
  lcd.setCursor(0,0);          
  lcd.print("EIXO Y:"); 
  lcd.setCursor(2,9);          
  lcd.print(potenciometro_); 
  delay(3000);
  lcd.clear();
  }
