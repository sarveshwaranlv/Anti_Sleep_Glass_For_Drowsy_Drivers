# Anti_Sleep_Glass_For_Drowsy_Drivers

*/

// these constants won't change:
const int xPin = 2;    // X output of the accelerometer
const int yPin = 3;    // Y output of the accelerometer

void setup() {
  // initialize serial communications:
  Serial.begin(9600);
  // initialize the pins connected to the accelerometer as inputs:
  pinMode(xPin, INPUT);
  pinMode(yPin, INPUT);
}

void loop() {
  // variables to read the pulse widths:
  int pulseX, pulseY;
  // variables to contain the resulting accelerations
  int accelerationX, accelerationY;

// read pulse from x- and y-axes:
  pulseX = pulseIn(xPin, HIGH);
  pulseY = pulseIn(yPin, HIGH);

// convert the pulse width into acceleration
  // accelerationX and accelerationY are in milli-g's:
  // Earth's gravity is 1000 milli-g's, or 1 g.
  accelerationX = ((pulseX / 10) - 500) * 8;
  accelerationY = ((pulseY / 10) - 500) * 8;

// print the acceleration
  Serial.print(accelerationX);
  // print a tab character:
  Serial.print("\t");
  Serial.print(accelerationY);
  Serial.println();

delay(100);
}
