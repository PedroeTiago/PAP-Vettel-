 //Motor A
 int enableA = 10;
 int pinA1 = 2;
 int pinA2 = 3;
 //Motor B
 int enableB = 9;
 int pinB1 = 4;
 int pinB2 = 5;

 int sensor=A0;

 int trigPin = 13;
 int echoPin = 12;
 
void setup() {
Serial.begin (9600);
 //configurar os pins
  pinMode (enableA, OUTPUT);
  pinMode (pinA1, OUTPUT);
  pinMode (pinA2, OUTPUT);
  
  pinMode (enableB, OUTPUT);
  pinMode (pinB1, OUTPUT);
  pinMode (pinB2, OUTPUT);
  
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
}

void right()
{ 
  digitalWrite(pinA1, HIGH);
  digitalWrite(pinA2, LOW);
}

void left()
{
  digitalWrite(pinB1, LOW);
  digitalWrite(pinB2, HIGH);
}
  
void straight()
{
  digitalWrite(pinA1, HIGH);
  digitalWrite(pinA2, LOW);
  digitalWrite(pinB1, LOW);
  digitalWrite(pinB2, HIGH);
}

void loop() {
  long duration, distance;
  digitalWrite(trigPin, LOW);  
  delayMicroseconds(2); 
  digitalWrite(trigPin, HIGH);

  delayMicroseconds(10); 
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distance = (duration/2) / 29.1;

  digitalWrite (enableA, HIGH);
  digitalWrite (enableB, HIGH);
   
 //ligar motor A
  if (distance > 4) { 
  digitalWrite(13, HIGH);
  delay(1000);
  digitalWrite(13, LOW);
  if( analogRead(sensor<400))
  {
      straight();
  }
      else if( analogRead(sensor<400))
      {
            left();
      }
            else if( analogRead(sensor>400))
            {
                  right();
    
             }
   }else {
      digitalWrite (enableA, LOW);
      digitalWrite (enableB, LOW);
 }
 }
