const int pinIRa1 = A1;

const int pinIRa = A0;


#define trig3 13
#define echo3 12
#define trig2 10
#define echo2 11
#define trig1 8
#define echo1 9
#define enA 5
#define enB 6
#define in1 2
#define in2 3
#define in3 4
#define in4 7
void setup() {
Serial.begin(9600);
delay(1000);
 pinMode(enA, OUTPUT);
 pinMode(enB, OUTPUT);
  pinMode(in1, OUTPUT);
  pinMode(in2, OUTPUT);
  pinMode(in3, OUTPUT);
  pinMode(in4, OUTPUT);
pinMode(trig1,OUTPUT);   
    pinMode(echo1,INPUT); 
    pinMode(trig2,OUTPUT);   
    pinMode(echo2,INPUT); 
      pinMode(trig3,OUTPUT);   
    pinMode(echo3,INPUT);   
   pinMode(pinIRa,INPUT);
   pinMode(pinIRa1,INPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  int cbtr = digitalRead(pinIRa1);
  int cbp = digitalRead(pinIRa);
 unsigned long duration1;  // biến đo thời gian
    int distance1;           // biến lưu khoảng cách
    
    /* Phát xung từ chân trig */
    digitalWrite(trig1,LOW);   // tắt chân trig
    delayMicroseconds(2);
    digitalWrite(trig1,HIGH);   // phát xung từ chân trig
    delayMicroseconds(5);   // xung có độ dài 5 microSeconds
    digitalWrite(trig1,LOW);   // tắt chân trig
    
  
    duration1 = pulseIn(echo1,HIGH);  
  
    distance1 = int(duration1 / 2 / 29.412);
    unsigned long duration2;  // biến đo thời gian
    int distance2;           // biến lưu khoảng cách
    
    /* Phát xung từ chân trig */
    digitalWrite(trig2,LOW);   // tắt chân trig
    delayMicroseconds(2);
    digitalWrite(trig2,HIGH);   // phát xung từ chân trig
    delayMicroseconds(5);   // xung có độ dài 5 microSeconds
    digitalWrite(trig2,LOW);   // tắt chân trig
    
  /* Tính toán thời gian */
   // Đo độ rộng xung HIGH ở chân echo. 
    duration2 = pulseIn(echo2,HIGH);  
   // Tính khoảng cách đến vật.
    distance2 = int(duration2 / 2 / 29.412);
    unsigned long duration3;  // biến đo thời gian
    int distance3;           // biến lưu khoảng cách
    
    /* Phát xung từ chân trig */
    digitalWrite(trig3,LOW);   // tắt chân trig
    delayMicroseconds(2);
    digitalWrite(trig3,HIGH);   // phát xung từ chân trig
    delayMicroseconds(5);   // xung có độ dài 5 microSeconds
    digitalWrite(trig3,LOW);   // tắt chân trig
    
  
    duration3 = pulseIn(echo3,HIGH);  
  
    distance3 = int(duration3 / 2 / 29.412);
  /* In kết quả ra Serial Monitor */
    
    if(cbtr == 1 ){
      
     
     lui();
     delay(800);
     xoay();
     delay(700);
    }
    else if(cbtr == 1 && cbp == 1 ){
      
  lui();
     delay(800);
     xoay();
     delay(700);
    }
    else  if(cbp == 1 ){
     
    
      lui();
     delay(800);
     xoay();
     delay(700);
    }
     else if(distance1<=20 && distance2>20 && distance3>20 ){
      at();
    }
    else if(distance1>20 && distance2<=20 && distance3>20 ){
           
      traig();
      delay(250);
    }
    else if(distance1>20 && distance2>20 && distance3<=20 ){
     
      phaig();
Phương
Phương Hoàng Văn
delay(250);
    }
    
    else if(cbtr == 0 &&  cbp == 0) {

    tien();
    }
}
void tien()
{
  /*The pin numbers and high, low values might be different depending on your connections */
  digitalWrite(in1, LOW);
  digitalWrite(in2, HIGH);
  digitalWrite(in3, LOW);
  digitalWrite(in4, HIGH);
  
  analogWrite(enA,  150); 
  analogWrite(enB,  150); 
}
void lui()
{
  /*The pin numbers and high, low values might be different depending on your connections */
  digitalWrite(in1, HIGH);
  digitalWrite(in2, LOW);
  digitalWrite(in3, HIGH);
  digitalWrite(in4, LOW);
  
  analogWrite(enA,  130); 
  analogWrite(enB,  130); 
}
void xoay(){
    digitalWrite(in1, LOW);
  digitalWrite(in2, HIGH);
  digitalWrite(in3, HIGH);
  digitalWrite(in4, LOW);
  
  analogWrite(enA,  150); 
  analogWrite(enB,  150); 
}
void phai()
{
  /*The pin numbers and high, low values might be different depending on your connections */
  digitalWrite(in1, LOW);
  digitalWrite(in2, HIGH);
  digitalWrite(in3, LOW);
  digitalWrite(in4, LOW);
  
  analogWrite(enA,  180); 
  analogWrite(enB,  180); 
}
void trai()
{
  /*The pin numbers and high, low values might be different depending on your connections */
  digitalWrite(in1, LOW);
  digitalWrite(in2, LOW);
  digitalWrite(in3, LOW);
  digitalWrite(in4, HIGH);
  
  analogWrite(enA,  180); 
  analogWrite(enB,  180); 
}
void dung()
{
  /*The pin numbers and high, low values might be different depending on your connections */
  digitalWrite(in1, LOW);
  digitalWrite(in2, LOW);
  digitalWrite(in3, LOW);
  digitalWrite(in4, LOW);
  
  analogWrite(enA,  0); 
  analogWrite(enB,  0); 
}
void traig()
{
  /*The pin numbers and high, low values might be different depending on your connections */
  digitalWrite(in1, HIGH);
  digitalWrite(in2, LOW);
  digitalWrite(in3, LOW);
  digitalWrite(in4, HIGH);
  
  analogWrite(enA,  200); 
  analogWrite(enB,  200); 
}
void phaig()
{
  /*The pin numbers and high, low values might be different depending on your connections */
  digitalWrite(in1, LOW);
  digitalWrite(in2, HIGH);
  digitalWrite(in3, HIGH);
  digitalWrite(in4, LOW);
  
  analogWrite(enA,  200); 
  analogWrite(enB,  200); 
}
void at()
{
  /*The pin numbers and high, low values might be different depending on your connections */
  digitalWrite(in1, LOW);
  digitalWrite(in2, HIGH);
  digitalWrite(in3, LOW);
  digitalWrite(in4, HIGH);
  
  analogWrite(enA,  250); 
  analogWrite(enB,  250); 
}
