# Line Following Robot with Obstacle Detection and Robotic Arm

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Arduino](https://img.shields.io/badge/Arduino-Compatible-blue.svg)](https://www.arduino.cc/)
[![Proteus](https://img.shields.io/badge/Proteus-Simulated-green.svg)](https://www.labcenter.com/)

A sophisticated line-following robot with obstacle detection capabilities and an integrated robotic arm for autonomous obstacle removal. Built using ATmega328P microcontroller and tested via Proteus simulation.
<img width="572" height="682" alt="image" src="https://github.com/user-attachments/assets/5e95d1c4-03c1-4a57-87d9-fe4c62e61560" /> 


## 🚀 Project Overview

This project implements an intelligent line-following robot that combines traditional line-following algorithms with advanced obstacle detection and removal capabilities. The robot features dual operating modes, PWM-based motor control, and a servo-controlled robotic arm for autonomous obstacle handling.

### Key Features

- ✅ **Dual Operating Modes**: Line following only vs. Line following with obstacle handling
- ✅ **Intelligent Obstacle Detection**: Ultrasonic sensor with 10cm detection range
- ✅ **Autonomous Obstacle Removal**: Robotic arm with 4 servo motors
- ✅ **Adaptive Motor Control**: PWM-based speed adjustment for curves and straight paths
- ✅ **Visual & Audio Alerts**: LED indicators and buzzer notifications
- ✅ **Proteus Simulation**: Complete circuit simulation before hardware implementation
- ✅ **Mode Switching**: Push-button control with LED status indication
  
<img width="464" height="640" alt="image" src="https://github.com/user-attachments/assets/aa63a148-0546-4e50-a806-159b21dfc08f" />


## 📋 Table of Contents

- [Hardware Components](#-hardware-components)
- [System Architecture](#-system-architecture)
- [Pin Configuration](#-pin-configuration)
- [Installation & Setup](#-installation--setup)
- [Usage](#-usage)
- [Simulation](#-simulation)
- [Project Structure](#-project-structure)
- [Contributing](#-contributing)
- [License](#-license)

## 🔧 Hardware Components

| Component | Quantity | Purpose |
|-----------|----------|---------|
| ATmega328P Microcontroller | 1 | Main controller |
| L298N Motor Driver | 1 | Controls DC motors |
| IR Sensors | 3 | Line detection (Left, Middle, Right) |
| Ultrasonic Sensor (HC-SR04) | 1 | Obstacle detection |
| DC Motors + Wheels | 4 | Movement |
| Robot Arm (4 Servo Motors + PCA9685 Driver) | 1 | Obstacle removal |
| Push Buttons | 2 | Mode switch & reset |
| LEDs (Red, Green, Blue) | 3 | Alerts & mode indication |
| Buzzer | 1 | Obstacle alert |
| 16 MHz Crystal Oscillator | 1 | MCU clock |
| Li-ion Battery Pack | 1 | Power source |
| Dot board | 1 | Circuit assembly |

## 🏗️ System Architecture

### Functional Description

**Line Following Algorithm**
- 3 IR sensors (Left, Middle, Right) detect black lines on white surfaces
- Robot adjusts motor direction based on sensor readings
- PWM control provides smooth speed transitions

**Obstacle Detection System**
- Ultrasonic sensor continuously monitors path ahead
- 10cm detection threshold triggers obstacle handling
- Red LED and buzzer activate upon obstacle detection

**Mode Switching**
- Push button toggles between two operating modes
- **Mode 1**: Line following only (Green LED)
- **Mode 2**: Line following + obstacle handling (Blue LED)

**Mode Switching Circuit**
<img width="389" height="383" alt="image" src="https://github.com/user-attachments/assets/b0444377-e6a8-427a-942f-d757a4283a89" />

**Robotic Arm Integration**
- 4 servo motors controlled via PCA9685 driver
- Autonomous obstacle removal sequence
- Forward movement → Pick/Push → Reset position

## 🔌 Pin Configuration

### Motor Driver (L298N)
```
enA → Pin 16 (PB2/D10) – Motor A Speed Control (PWM)
in1 → Pin 15 (PB1/D9)  – Motor A Direction 1
in2 → Pin 14 (PB0/D8)  – Motor A Direction 2
in3 → Pin 13 (PD7/D7)  – Motor B Direction 1
in4 → Pin 12 (PD6/D6)  – Motor B Direction 2
enB → Pin 11 (PD5/D5)  – Motor B Speed Control (PWM)
```

### IR Sensors
```
Right Sensor  → Pin 23 (PC0/A0)
Middle Sensor → Pin 24 (PC1/A1)
Left Sensor   → Pin 25 (PC2/A2)
```

### Ultrasonic Sensor (HC-SR04)
```
Trigger → Pin 5 (PD3/D3)
Echo    → Pin 4 (PD2/D2)
```

### User Interface
```
Mode Button → Pin 26 (PC3/A3) – with internal pull-up
Red LED     → Pin 6 (PD4/D4)  – Obstacle alert
Green LED   → Pin 18 (PB4/D12) – Mode 1 indicator
Blue LED    → Pin 17 (PB3/D11) – Mode 2 indicator
Buzzer      → Pin 27 (PC4/A4)  – Audio alerts
```

## 🛠️ Installation & Setup

### Prerequisites

- Arduino IDE (latest version)
- Proteus Design Suite (for simulation)
- ATmega328P microcontroller
- Required hardware components (listed above)

### Software Setup

1. **Clone the Repository**
   ```bash
   git clone https://github.com/TMNPThennakoon/Line-Following-With-Obstacle-Detection-Robot.git
   cd Line-Following-With-Obstacle-Detection-Robot
   ```

2. **Open Arduino IDE**
   - Navigate to `LINERBO_simcode/LINERBO_simcode.ino`
   - Select Arduino Uno board
   - Upload the code to your ATmega328P

3. **Proteus Simulation**
   - Open `LINE_ROBOT.pdsprj` in Proteus
   - Load the generated HEX file
   - Run simulation to test functionality

### Hardware Assembly

1. **Circuit Assembly**
   - Follow the pin configuration diagram
   - Assemble components on dot board
   - Ensure proper power supply connections

2. **Calibration**
   - Adjust IR sensor sensitivity
   - Calibrate ultrasonic sensor range
   - Test motor directions and speeds

## 🎮 Usage

### Operating Modes

**Mode 1: Line Following Only**
- Press mode button to activate (Green LED)
- Robot follows black line on white surface
- No obstacle detection active

  <img width="223" height="358" alt="image" src="https://github.com/user-attachments/assets/73f3841b-3130-414a-96d5-675b0a1cd4f3" />


**Mode 2: Line Following + Obstacle Handling**
- Press mode button to activate (Blue LED)
- Combines line following with obstacle detection
- Automatic obstacle removal when detected

<img width="232" height="359" alt="image" src="https://github.com/user-attachments/assets/bb91562b-f6dd-4d8f-a2c3-cf196b8d16a4" />


### Control Features

- **Mode Switching**: Press button to toggle between modes
- **Obstacle Alert**: Red LED + buzzer when obstacle detected
- **Audio Feedback**: Different beep patterns for various events
- **Visual Status**: LED indicators show current mode

## 🖥️ Simulation

### Proteus Simulation Setup

1. **Circuit Design**
   - Complete circuit schematic available in `LINE_ROBOT.pdsprj`
   - All components properly connected and configured

2. **Simulation Features**
   - Real-time sensor readings
   - Motor control visualization
   - Obstacle detection simulation
   - Mode switching demonstration

### Simulation Images

<!-- Add your simulation screenshots here -->

#### Circuit Diagram
<img width="605" height="437" alt="image" src="https://github.com/user-attachments/assets/9ee8ee38-a28c-45b6-8507-05bd30c9eff2" />


#### Proteus Simulation Interface
<img width="902" height="821" alt="image" src="https://github.com/user-attachments/assets/db282dff-acda-4e75-a54d-145d8d8c455f" />


#### Component Layout
![Component Layout](images/component-layout.png)
*Physical component arrangement and connections*

#### Test Results

<img width="337" height="301" alt="image" src="https://github.com/user-attachments/assets/f8b6abd5-67a0-42bc-b8bd-84d85fcbdc0c" />

<img width="325" height="305" alt="image" src="https://github.com/user-attachments/assets/f7a7ad09-c27d-42c7-8a2c-98e1a265d096" />

<img width="250" height="308" alt="image" src="https://github.com/user-attachments/assets/e02a6c68-f911-4479-9884-213e59c91b39" />


## 📁 Project Structure

```
Line-Following-With-Obstacle-Detection-Robot/
├── LINERBO_simcode/
│   ├── LINERBO_simcode.ino          # Main Arduino code
│   ├── build/                        # Compiled HEX files
│   ├── LINE_ROBOT.pdsprj            # Proteus project file
│   ├── LINE_ROBOT_Simulation.jpg    # Simulation screenshot
│   ├── With robot Arm LF robot Circuit.png
│   ├── Sensor .hex file/            # Sensor libraries for Proteus
│   │   ├── InfraredSensors/
│   │   ├── L298MotorDriver/
│   │   └── ultrasonic/
│   └── Project Backups/             # Backup files
├── images/                          # Project images and screenshots
│   ├── simulation/                  # Simulation screenshots
│   ├── hardware/                    # Hardware assembly photos
│   ├── final-output/                # Final project demonstrations
│   └── circuit-diagrams/            # Circuit diagrams and schematics
├── README.md                        # This file
└── LICENSE                          # MIT License
```

### 📸 Image Organization

The project includes a comprehensive image collection organized in the `images/` directory:

- **`images/simulation/`** - Proteus simulation screenshots and test results
- **`images/hardware/`** - Hardware assembly, circuit boards, and component photos
- **`images/final-output/`** - Robot demonstrations and final project videos
- **`images/circuit-diagrams/`** - Circuit schematics and connection diagrams

## 🎯 Key Features Implementation

### Line Following Algorithm
```cpp
int readSensors() {
    int RS = digitalRead(RS_PIN);  
    int MS = digitalRead(MS_PIN);  
    int LS = digitalRead(LS_PIN);
    
    // LOW = black line, HIGH = white
    if (RS == HIGH && MS == HIGH && LS == HIGH) return 0; // Line lost
    if (MS == LOW && LS == HIGH && RS == HIGH) return 1;  // Center
    if (LS == LOW && MS == HIGH) return 2;                // Left
    if (RS == LOW && MS == HIGH) return 3;                // Right
    return 4; // Undefined
}
```

### Obstacle Detection
```cpp
long getDistance() {
    digitalWrite(trigPin, LOW);
    delayMicroseconds(2);
    digitalWrite(trigPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(trigPin, LOW);
    
    long duration = pulseIn(echoPin, HIGH, 20000);
    long distance = duration * 0.034 / 2;
    return distance;
}
```

### PWM Motor Control
- Adaptive speed control for different path conditions
- Slower speeds on sharp turns
- Faster speeds on straight paths
- Smooth transitions between movements

## 📊 Performance Specifications

- **Line Detection**: 3 IR sensors with digital output
- **Obstacle Range**: 2cm - 400cm (ultrasonic sensor)
- **Detection Threshold**: 10cm for obstacle handling
- **Motor Control**: PWM-based speed control
- **Operating Voltage**: 5V (microcontroller), 12V (motors)
- **Response Time**: < 50ms for sensor readings

## 🎥 Demo Videos

<!-- Add your demo video links here -->


https://github.com/user-attachments/assets/ac569c33-360a-4419-949a-fb35a486c8e9


## 📸 Project Images

### Hardware Assembly

#### Custom Arduino Board with ATmega328P

<img width="571" height="526" alt="image" src="https://github.com/user-attachments/assets/b79e6acc-d290-45c1-b653-87b73daad9f0" />


#### Complete Robot Assembly

<img width="417" height="313" alt="image" src="https://github.com/user-attachments/assets/a8e784a8-8701-41d3-aa41-bde5c6810fa5" />


#### Robotic Arm Detail

<img width="246" height="357" alt="image" src="https://github.com/user-attachments/assets/c1d328ca-99ed-478d-8dd8-fa43d6c52d0b" />
<img width="261" height="355" alt="image" src="https://github.com/user-attachments/assets/cbbfd704-750d-4aed-b1d8-c9cbba61160c" />
<img width="430" height="238" alt="image" src="https://github.com/user-attachments/assets/623ce25f-decf-46a5-9339-6190709ff285" />


## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**Nayana Pabasara** 
- Hardware Design & Assembly
- Software Development & Programming
- Circuit Simulation & Testing
- Documentation & Project Management

## 📞 Contact

- **GitHub**: [@TMNPThennakoon](https://github.com/TMNPThennakoon)
- **Project Repository**: [Line-Following-With-Obstacle-Detection-Robot](https://github.com/TMNPThennakoon/Line-Following-With-Obstacle-Detection-Robot)

## 🙏 Acknowledgments

- Arduino community for excellent documentation and support
- Proteus Design Suite for comprehensive simulation capabilities
- Open source hardware community for inspiration and resources
- Educational resources and tutorials that guided the development process

---

**⭐ If you found this project helpful, please consider giving it a star!**

*Built with ❤️ using Arduino IDE and Proteus Design Suite*
