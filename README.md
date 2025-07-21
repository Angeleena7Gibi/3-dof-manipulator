# 3-DOF Manipulator
Vision-based 3-DOF robotic manipulator that detects PCB vias and performs pick-and-place using Arduino and OpenCV.
# 3-DOF Manipulator - Vision-Based Pick and Place System 

This project implements a 3-DOF robotic arm controlled by an Arduino and triggered using real-time via detection via OpenCV in Python. The system detects four circular vias on a PCB using a webcam, then sends a serial signal to the Arduino to begin a predefined pick-and-place routine.

---

##  Project Overview

- Detects 4 circular vias on a PCB using computer vision.
- Sends a signal (`'1'`) to Arduino via Serial.
- Arduino runs a one-time sequence controlling 3 servos and a vacuum pump using a relay.
- Designed for PCB component pick-and-place applications.

---

##  Hardware Components

| Component       | Description                              |
|----------------|------------------------------------------|
| Arduino Uno     | Microcontroller board                    |
| Servo Motors    | 3x (for base rotation, arm, and vertical lift) |
| Relay Module    | 5V relay to control vacuum suction        |
| Vacuum Pump     | For component pick-up                     |
| USB Webcam      | For vision input                          |
| Jumper Wires    | For connections                          |
| Breadboard / Custom Frame | For mounting and prototyping   |

---

##  File Descriptions

| File                             | Description |
|----------------------------------|-------------|
| `slot_detection_and_communication.py` | Python script to detect vias and send a trigger to Arduino. |
| `actuation.ino`                 | Arduino code for servo movement and vacuum actuation. |

---

##  How the System Works

1. Webcam streams live feed.
2. OpenCV detects circular vias using contour analysis and circularity check.
3. On detecting 4 vias, a serial `'1'` is sent to Arduino.
4. Arduino runs a pre-programmed servo routine:
   - Servo 3 lowers arm
   - Relay activates vacuum pump (pick)
   - Arm moves to placement area
   - Component is placed
   - Arm returns to original position

---



##  Wiring Summary

| Arduino Pin | Connection         |
|-------------|--------------------|
| D9          | Servo 1 (base rotation) |
| D10         | Servo 2 (arm joint) |
| D11         | Servo 3 (vertical lift) |
| D7          | Relay for vacuum pump |

---

## How to Run

### 1. Upload Arduino Code
- Open `actuation.ino` in Arduino IDE.
- Select the correct COM port and board.
- Upload to the Arduino Uno.

### 2. Run Python Script
Make sure the camera is connected and Arduino is on the same port (adjust `COM5` if needed):

```bash
python slot_detection_and_communication.py

