const int sensorPin = A0;   
const int fanPin = 13;      

const float BETA = 3950;    

void setup() {
  Serial.begin(9600);
  pinMode(fanPin, OUTPUT);
}

void loop() {
  int analogValue = analogRead(sensorPin);

  
  float celsius = 1 / (log(1 / (1023.0 / analogValue - 1)) / BETA + 1.0 / 298.15) - 273.15;

  int fanSpeed = 0;
  String fanState = "";

  if (celsius < 25) {
    fanSpeed = 0;               
    fanState = "OFF";
  } 
  else if (celsius >= 25 && celsius < 30) {
    fanSpeed = 128;             
    fanState = "50% Speed";
  } 
  else {
    fanSpeed = 255;          
    fanState = "100% Speed";
  }

  analogWrite(fanPin, fanSpeed);

  Serial.print("Temperature: ");
  Serial.print(celsius);
  Serial.print(" °C | Fan: ");
  Serial.println(fanState);

  delay(1000);
}
