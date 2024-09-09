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
