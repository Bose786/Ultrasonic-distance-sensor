# Ultrasonic-distance-sensor
void setup() {
  // initialize serial communication:
  Serial.begin(9600);
 
}

void loop()
{
  // establish variables for duration of the ping, 
  // and the distance result in inches and centimeters:
  long duration, inches, cm;

  // The PING))) is triggered by a HIGH pulse of 2 or more microseconds.
  // Give a short LOW pulse beforehand to ensure a clean HIGH pulse:
  
  pinMode(7, OUTPUT);
  digitalWrite(7, LOW);
  delay(200);
  digitalWrite(7, HIGH);
  delay(500);
  digitalWrite(7, LOW);

  pinMode(7, INPUT);
  duration = pulseIn(7, HIGH);
 
  

  // convert the time into a distance
  inches = microsecondsToInches(duration);
  
  
  Serial.print(inches);  // to serially print the data
  Serial.print("in, ");
  
  Serial.println();  
  delay(100);
}

long microsecondsToInches(long microseconds)
{
  return microseconds / 74 / 2;
}
