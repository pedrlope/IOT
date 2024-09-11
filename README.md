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
