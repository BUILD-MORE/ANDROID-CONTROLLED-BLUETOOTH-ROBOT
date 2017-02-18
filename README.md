# ANDROID-CONTROLLED-BLUETOOTH-ROBOT
The hardware you require for making this robot is Arduino Uno, Bluetooth module(HC-05), 200 RPM geared DC motor, robot chasis, L293D motor driver wheels, adn some jumper wires.
 the code you need for the software(arduino ide)  and to upload in to your UNO board via serial data cable is as follow....
 
   // Android Phone Controlled Robot
// Successfully Tested on Android App --> 'Arduino Bluetooth 
// Terminal'; it is available free on the Google Play Store
char state;
int flag=0;            // ALL THE UDF ARE DECLAREDHERE
void stp();
void fwd();
void left();
void right();
void back();
void setup()
   {
    pinMode(2,OUTPUT);                  
   
    pinMode(3,OUTPUT);                  

    pinMode(4,OUTPUT);                  
    pinMode(5,OUTPUT);                  
Serial.begin(9600);   // Baud rate set to 9600bps
}
void loop() {
    if(Serial.available() > 0)      // Ckeck for command Recieved
    {    
      state = Serial.read();
      Serial.println(state);  
      flag=0;
    }  
    if (state == 'x')     // Checking Command from User
    {
        stp();
        if(flag == 0)
       {
          Serial.println("Stop");                     // all the UDF are called here from onwards
          flag=1;
       }
    }
    else if (state == 'f')
    {
        fwd();
        if(flag == 0)
        {
          Serial.println("Forward");
          flag=1;
         }
    }
    else if (state == 'b')
    {
        back();
        if(flag == 0)
        {
          Serial.println("Backword");
          flag=1;
        }
    }
    else if (state == 'l')
    {
        left();
        if(flag == 0)
        {
          Serial.println("Left");
          flag=1;
         }
    }
    else if (state == 'r')
    {
        right();
        if(flag == 0)
        {
          Serial.println("Right");
          flag=1;
         }
    }
 
    

 
    
 
Serial.println(state); //loop() ends here                // all the UDF are defined here
 }
void fwd()          // Forward               
{
  digitalWrite(2,HIGH);
  digitalWrite(4,HIGH);
  digitalWrite(5,LOW);
  digitalWrite(3,LOW);
  delay (10);
  digitalWrite(2,LOW);
  digitalWrite(4,LOW);
  
}
void back()          // Backward
{
  digitalWrite(3,HIGH);
  digitalWrite(5,HIGH);
  digitalWrite(2,LOW);
  digitalWrite(4,LOW);
  delay (10);
   digitalWrite(3,LOW);
  digitalWrite(5,LOW);
}
void left()          //LEFT
{
  digitalWrite(2,LOW);
  digitalWrite(4,HIGH);
  digitalWrite(3,HIGH);
  digitalWrite(5,LOW);
  delay (10);
  digitalWrite(3,LOW); 
  digitalWrite(4,LOW);
 }
void right()          // Right
{
  digitalWrite(2,HIGH);
  digitalWrite(4,LOW);
  digitalWrite(3,LOW);
  digitalWrite(5,HIGH);
 delay (10);
 digitalWrite(2,LOW);
 digitalWrite(5,LOW);
}
void stp()            // Robot STops
{
  digitalWrite(2,LOW);
  digitalWrite(3,LOW);
  digitalWrite(4,LOW);
  digitalWrite(5,LOW);
}
