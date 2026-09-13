# SCOUT
Autonomous wheeled robot for disaster-zone reconnaissance — detects human presence and hazards (e.g. exposed wiring) via onboard AI.
SCOUT is a wheeled, autonomous ground robot built to assist disaster-response efforts by scanning affected areas for human presence and infrastructure hazards such as exposed wiring. Using an onboard camera and AI, it navigates semi-autonomously, avoids obstacles, and streams live footage with real-time alerts. SCOUT does not perform physical rescue operations — its role is limited to detection, navigation, and reporting.

This project was developed as a semester-long embedded systems lab prototype and tested in a controlled, simulated disaster environment rather than a real disaster zone.
Features
Autonomous navigation — obstacle avoidance using ultrasonic sensing
Human detection — onboard AI (TensorFlow Lite) identifies human presence in the camera feed
Hazard detection — flags visual hazards such as exposed wiring
Live video streaming — WiFi-based live feed to a browser dashboard
Real-time alerts — notifies the user the moment a human or hazard is detected
System Architecture

SCOUT uses a two-board modular design:

Board	Responsibility
ESP32-CAM	Camera capture, AI inference (human/hazard detection), WiFi streaming
Arduino Nano (ATmega328P)	Obstacle avoidance sensing, motor driver control, movement

The two boards communicate over serial (UART), splitting "perception" (ESP32-CAM) from "reflexes" (Arduino) — a deliberate design choice for modularity and easier debugging, not a workaround.

Hardware
Component	Purpose
ESP32-CAM module	Camera + AI inference + WiFi
FTDI USB-to-Serial programmer	Uploading code to ESP32-CAM
Arduino Nano (ATmega328P)	Motor and sensor control
DC gear motors (TT motors) x2	Movement
2WD robot chassis kit	Structural base
L298N motor driver	Motor speed/direction control
HC-SR04 ultrasonic sensor	Obstacle detection
18650 Li-ion batteries + holder	Power supply
MQ-2 gas/smoke sensor (optional)	Additional hazard detection

Full bill of materials with cost breakdown is in /docs/SRS.pdf (or link to your SRS doc).

Software / Tools
Arduino IDE
TensorFlow Lite for Microcontrollers (human/hazard detection model)
ESP32 Arduino core (board support)
Getting Started
1. Clone the repo
bash
git clone https://github.com/<your-username>/scout-robot.git
cd scout-robot
2. Set up Arduino IDE
Install Arduino IDE
Add ESP32 board support via Boards Manager
Install required libraries (see /firmware/libraries.txt if included)
3. Upload firmware
Flash esp32cam/ sketch to the ESP32-CAM using the FTDI programmer
Flash arduino_nano/ sketch to the Arduino Nano
4. Power on and connect
Power the robot
Connect to its WiFi stream / dashboard IP shown in Serial Monitor on first boot
Project Status

🚧 In active development as a 10-week semester project. See /docs/SRS.pdf for full requirements, weekly milestones, and test plan.

Limitations
Tested only in a controlled, simulated disaster environment — not validated for real-world disaster-zone deployment
Human/hazard detection accuracy is constrained by the limited processing power of ESP32-CAM
No physical rescue or manipulation capability — detection and reporting only
License

(Add your license here — MIT is a common choice for academic/open projects)

Acknowledgments

Inspired by real-world search-and-rescue robotics research and open-source disaster-response robotics initiatives.
