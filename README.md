line-following-robot-
=====================
AF_DCMotor motor1(1, MOTOR12_64KHZ); // create motor #2, 64KHz pwm
AF_DCMotor motor2(2, MOTOR12_64KHZ); // create motor #2, 64KHz pwm
#define NUM_SENSORS             6  // number of sensors used
#define NUM_SAMPLES_PER_SENSOR  10  // average 10 analog samples per sensor reading

// sensors 0 through 5 are connected to analog inputs 0 through 5, respectively
QTRSensorsAnalog qtra((unsigned char[]) {0, 1, 2, 3, 4, 5}, 
  NUM_SENSORS, NUM_SAMPLES_PER_SENSOR);
unsigned int sensorValues[NUM_SENSORS];

void setup() {
motor1.setSpeed(100); // set the speed to 200/255
motor2.setSpeed(100); // set the speed to 200/255

  delay(1000);
  Serial.begin(9600); // set the data rate in bits per second for serial data transmission
  delay(1000);
}

void loop() {
  qtra.read(sensorValues);
  for (unsigned char i = 0; i < NUM_SENSORS; i++)
  {
    Serial.print(sensorValues[i]);
    Serial.print('\t'); // tab to format the raw data into columns in the Serial monitor
  }
  Serial.println();
motor1.run(FORWARD); // turn it on going forward
motor2.run(FORWARD); // turn it on going forward
delay(0);


if (sensorValues[0] >= 600)
{
  motor1.setSpeed(200);
  motor2.setSpeed(50);
  delay(0);
}
else if (sensorValues[1] >= 600)
{
  motor1.setSpeed(200);
  motor2.setSpeed(50);
  delay(0);
}
else if (sensorValues[2] >= 600)
{
  motor1.setSpeed(200);
  motor2.setSpeed(50);
  delay(0);
}
else if (sensorValues[3] >= 600)
{
  motor1.setSpeed(50);
  motor2.setSpeed(200);
  delay(0);
}
else if (sensorValues[4] >= 600)
{
  motor1.setSpeed(50);
  motor2.setSpeed(200);
  delay(0);
}
else if (sensorValues[5] >= 600)
{
  motor1.setSpeed(50);
  motor2.setSpeed(200);
  delay(0);
}
else
{
motor1.setSpeed(100); // turn it on going forward
motor2.setSpeed(100); // turn it on going forward
delay(0);
}
}
