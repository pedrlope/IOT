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

#include <Wire.h> 
#include <LiquidCrystal_I2C.h>

#define endereco 0x3F  
#define colunas 16
#define linhas 2

LiquidCrystal_I2C lcd(endereco, colunas, linhas);

const int inferior = 512; 
const int superior = 520;

void setup() { 
 pinMode(2, INPUT); 
 pinMode (A0, INPUT);
 pinMode (A1, INPUT); 
Serial.begin(9600);

lcd.init(); // INICIA A COMUNICAÇÃO COM O DISPLAY
lcd.backlight(); // LIGA A ILUMINAÇÃO DO DISPLAY
}

void loop() { lcd.clear();

int POTENCIOMETRO_X = analogRead(A0);
int POTENCIOMETRO_Y = analogRead(A1);
int button = digitalRead(2);

if (POTENCIOMETRO_X > 540){
Serial.print("X: ");
Serial.println(POTENCIOMETRO_X);
delay(1000);
}
if (POTENCIOMETRO_Y > 540){
Serial.print("Y: ");
Serial.println(POTENCIOMETRO_Y);
delay(1000);
}


if ((POTENCIOMETRO_X > superior && POTENCIOMETRO_X < 1023) && 
    (POTENCIOMETRO_Y >= inferior && POTENCIOMETRO_Y < 1023)) {
    lcd.setCursor(0, 0);
    lcd.print("PARA FRENTE");
    Serial.print("para frente ");

} 
else if ((POTENCIOMETRO_X < inferior) && (POTENCIOMETRO_Y >= inferior && POTENCIOMETRO_Y < 1023))
{
    lcd.setCursor(0, 0);
    lcd.print("PARA TRAZ");
    Serial.print("para traz ");
} else if (POTENCIOMETRO_Y > superior + 100) {
    lcd.setCursor(0, 0);
    lcd.print("DIREITA");
    Serial.print("direita  ");
} else if (POTENCIOMETRO_Y < inferior - 100) {
    lcd.setCursor(0, 0);
    lcd.print("ESQUERDA");
    Serial.print("esquerda  ");
} else {
    lcd.setCursor(0, 0);
    lcd.print("PARADO");
    Serial.print("parado  ");
}

if (button == HIGH) {
    lcd.setCursor(0, 1);
    lcd.print("CLIQUE");
}

delay(3000); // Espera por 3000 milissegundos
}
if (button == HIGH) {
    lcd.setCursor(0, 1);
    lcd.print("CLIQUE");
}

delay(3000); // Espera por 3000 milissegundos
}

# ARDUINO 14 OLED

#include <Wire.h> //Biblioteca para uso do protocolo I2C;
#include <Adafruit_GFX.h> //Biblioteca para manipulação gráfica no display;
#include <Adafruit_SH1106.h> //Biblioteca para operação do driver de controle do display;

#include <Fonts/FreeMono9pt7b.h> //Fonte para alteração do texto;
#include <Fonts/FreeSansBoldOblique9pt7b.h> //Fonte para alteração do texto;
#include <Fonts/FreeMonoOblique9pt7b.h> //Fonte para alteração do texto;

#define OLED_RESET -1 //Em displays que não possuem pino RESET, é dado o valor -1;

Adafruit_SH1106 display(OLED_RESET); //Declaração da tela com o nome "display";

void setup() {
  Serial.begin(9600);
  display.begin(SH1106_SWITCHCAPVCC, 0x3C); //Inicialização do display com a biblioteca e endereço de hardware do display;
}

void loop() {

  display.clearDisplay(); //Comando para limpar a tela;
  display.setFont(&FreeMonoOblique9pt7b); //Comando para definir a fonte que será utilizada;
  display.setTextColor(WHITE); //Comando para definir a cor do texto;
  display.setTextSize(1); //Comando para definir tamanho od
  display.setCursor(10, 22); //Definição de onde o texto será escrito. Lembre se que: linha, coluna;
  display.print("Calculator"); //Texto a ser escrito;

  display.setFont(&FreeMono9pt7b);
  display.setCursor(13, 47);
  display.print("9 + 9 x 9");

  display.display(); //Mostrar informações na tela;


  delay(3000);

  display.clearDisplay(); //Comando para limpar a tela;

  display.setCursor(0, 20); //Definição de onde o texto será escrito. Lembre se que: linha, coluna;
  display.print("90, acertou!"); //Texto a ser escrito;

  display.setCursor(5, 50); //Definição de onde o texto será escrito. Lembre se que: linha, coluna;
  display.print("162, errou!"); //Texto a ser escrito;
  
  display.display(); //Mostrar informações na tela;
  delay(3000);
  display.clearDisplay(); //Comando para limpar a tela;

  display.fillTriangle(90, 40, 105, 22, 120, 40, WHITE); //Desenhar triângulo preenchido (pos x1, pos y1, pos x2, pos y2, pos x3, pos y3, cor);
  display.display(); //Mostrar informações na tela;
  delay(3000);
}


# 15 ARDUINO REFLETANCIA

#include <Wire.h> //Biblioteca para uso do protocolo I2C;
#include <Adafruit_GFX.h> //Biblioteca para manipulação gráfica no display;
#include <Adafruit_SH1106.h> //Biblioteca para operação do driver de controle do display;


#include <Fonts/FreeMono9pt7b.h> //Fonte para alteração do texto;
#include <Fonts/FreeSansBoldOblique9pt7b.h> //Fonte para alteração do texto;
#include <Fonts/FreeMonoOblique9pt7b.h> //Fonte para alteração do texto;


#define OLED_RESET -1 //Em displays que não possuem pino RESET, é dado o valor -1;


Adafruit_SH1106 display(OLED_RESET); //Declaração da tela com o nome "display";


#define pinSensor1 7


void setup() {
  pinMode(pinSensor1, INPUT);
  display.begin(SH1106_SWITCHCAPVCC, 0x3C); //Inicialização do display com a biblioteca e endereço de hardware do display;
  Serial.begin(9600);
}

void loop()
{
  bool estadoSensor1 = digitalRead(pinSensor1);

  display.clearDisplay(); //Comando para limpar a tela;
  display.setFont(&FreeMonoOblique9pt7b); //Comando para definir a fonte que será utilizada;
  display.setTextColor(WHITE); //Comando para definir a cor do texto;
  display.setTextSize(1); //Comando para definir tamanho od
  
  if (estadoSensor1) {
    display.setCursor(15, 38); //Definição de onde o texto será escrito. Lembre se que: linha, coluna;
    display.print("Obstaculo");
    Serial.println("Obstaculo");

  }
  
  else {
    display.setCursor(15, 25); //Definição de onde o texto será escrito. Lembre se que: linha, coluna;
    display.println(" Nenhum ");
    display.setCursor(15, 50); //Definição de onde o texto será escrito. Lembre se que: linha, coluna;
    display.println("Obstaculo");
    Serial.println("Nada");
  }

 display.display();
}
