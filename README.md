# 🤖 Obstacle Avoiding Smart Robot  

An autonomous robot built using **Arduino + Ultrasonic Sensors** to detect and avoid obstacles in real time.  

## 🔧 Features  
- Detects obstacles within a predefined distance (e.g., 30 cm).  
- Automatically changes direction to avoid collision.  
- Compact and low-cost hardware design.  

## 🛠 Tech Stack  
- **Microcontroller:** Arduino Uno  
- **Sensors:** Ultrasonic Sensor (HC-SR04)  
- **Actuators:** DC Motors + Motor Driver (L293D)  
- **Programming Language:** Embedded C (Arduino IDE)  
- **Power Supply:** 9V Battery  

## 📂 Project Structure
Obstacle-Avoiding-Robot/
│── Code/ObstacleAvoider.ino       # Arduino source code
│── CircuitDiagram.png             # Circuit connections
│── Components_List.txt            # List of hardware used
│── README.md                      # Project documentation

## 🚀 Demo  
<img width="642" height="1389" alt="image" src="https://github.com/user-attachments/assets/8ee2c135-8fe8-457c-8a23-86df5807f40d" />
<img width="642" height="1389" alt="image" src="https://github.com/user-attachments/assets/4d826876-5129-41dc-979d-067f26b8ef4a" />
<img width="642" height="1389" alt="image" src="https://github.com/user-attachments/assets/2967954e-425d-45ec-9659-d7403e7100ee" />


## 👨‍💻 Team Contribution  
- **Team Lead:** Sravanth  
- Guided project flow, handled Arduino coding, and final integration.  
- Coordinated with a 4-member team for hardware assembly + testing.  

## 📈 Results  
- Achieved **95% accuracy** in obstacle detection & avoidance during trials.  

## 🌟 Future Enhancements  
- Add Bluetooth / Wi-Fi module for remote control.  
- Implement AI-based path planning.  
- Integrate sensors for edge detection (cliff avoidance).
- 
1.	ObstacleAvoider
    /*
  Project: Obstacle Avoiding Robot
  Platform: Arduino Uno + Ultrasonic Sensor (HC-SR04) + Motor Driver (L293D)
  Description: 
    Detects obstacles using ultrasonic sensor and avoids them by changing direction.
  Team Lead: Sravanth
  Year: 2024
*/

#define trigPin 9
#define echoPin 10
#define motor1 5
#define motor2 6
#define motor3 7
#define motor4 8

long duration;
int distance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(motor1, OUTPUT);
  pinMode(motor2, OUTPUT);
  pinMode(motor3, OUTPUT);
  pinMode(motor4, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  // Send ultrasonic pulse
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2; // convert to cm

  Serial.print("Distance: ");
  Serial.println(distance);

  if (distance < 30) {
    // Obstacle detected → turn right
    digitalWrite(motor1, LOW);
    digitalWrite(motor2, HIGH);
    digitalWrite(motor3, LOW);
    digitalWrite(motor4, HIGH);
    delay(500);
  } else {
    // Move forward
    digitalWrite(motor1, HIGH);
    digitalWrite(motor2, LOW);
    digitalWrite(motor3, HIGH);
    digitalWrite(motor4, LOW);
  }
}
CircuitDiagram.png → circuit diagram image
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/556ef7cf-70d6-443a-8fbe-4e20f1178d71" />

Components_List.txt
1.	Arduino Uno – 1 unit
	•	Microcontroller board used for controlling the robot.
	2.	Ultrasonic Sensor (HC-SR04) – 1 unit
	•	Detects obstacles by measuring distance using sound waves.
	3.	Motor Driver IC (L293D / L298N) – 1 unit
	•	Controls the direction and speed of DC motors.
	4.	DC Motors (BO Motors / Geared Motors) – 2 units
	•	Provides movement to the robot wheels.
	5.	Wheels – 2 units
	•	Attached to DC motors for motion.
	6.	Caster Wheel – 1 unit
	•	Provides balance and free rotation at the front or back.
	7.	Chassis (Robot Frame) – 1 unit
	•	Holds all components together.
	8.	Jumper Wires (Male–Male / Male–Female) – set
	•	For making electrical connections.
	9.	Breadboard / PCB – 1 unit
	•	For assembling the circuit.
	10.	Battery (9V or Li-ion pack) – 1 unit
	•	Power source for the system.
	11.	Battery Holder & Switch – 1 unit
	•	For connecting and safely switching the battery.

