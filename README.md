# Hand Gesture Controlled Arduino Robot

A computer vision-powered robotic vehicle controlled through hand gestures using MediaPipe, OpenCV, and Arduino with wireless NRF24L01 communication.

## Overview

This project enables intuitive control of an Arduino-based robot using hand gestures captured via webcam. The system uses MediaPipe for real-time hand tracking and gesture recognition, then transmits control signals wirelessly to the robot using NRF24L01 modules.

## Features

- **Real-time Hand Tracking**: Uses MediaPipe's hand landmark detection
- **Wireless Control**: NRF24L01 modules for reliable communication
- **Four Control Gestures**: Forward, Stop, Spin Left, Spin Right
- **Visual Feedback**: Live webcam display with gesture overlay

## Hardware Requirements

- 2x Arduino boards (Uno/Nano recommended)
- 2x NRF24L01 wireless transceiver modules
- Motor driver (L298N or similar)
- DC motors and wheels for robot chassis
- Power supply (batteries for robot)
- Webcam for gesture capture

## Software Requirements

- Python 3.10.9
- Required Python libraries:
  ```bash
  pip install mediapipe opencv-python pyserial
  ```

## System Architecture

### Transmitter (Computer + Arduino 1)
- Python script captures hand gestures via webcam
- Processes hand landmarks using MediaPipe
- Sends commands to Arduino via serial port
- Arduino transmits commands wirelessly via NRF24L01

### Receiver (Arduino 2 + Robot)
- Receives wireless commands via NRF24L01
- Controls motor driver based on received gestures
- Drives robot motors accordingly

## Hardware Setup

### Vehicle and Receiver
<img width="543" alt="Vehicle and Receiver Setup" src="https://github.com/BenMcMillen/HandGestureRobot/assets/105152944/56a93c03-a0f9-412e-8d62-3976551c252f">

### Arduino Transmitter
<img width="539" alt="Arduino and Transmitter" src="https://github.com/BenMcMillen/HandGestureRobot/assets/105152944/629f8d0e-30fe-410d-9d7d-539171d935fa">

## Installation & Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/BenMcMillen/HandGestureRobot.git
   cd HandGestureRobot
   ```

2. **Install Python dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure serial port**
   - Connect Arduino to your computer
   - Identify the serial port (e.g., `COM3` on Windows, `/dev/ttyUSB0` on Linux)
   - Update the port in `fingersensor.py`:
     ```python
     ser = serial.Serial('YOUR_PORT_HERE', 9600)
     ```

4. **Upload Arduino sketches**
   - Upload transmitter code to Arduino 1
   - Upload receiver code to Arduino 2

5. **Run the application**
   ```bash
   python fingersensor.py
   ```

## Hand Gesture Controls

### Forward
<img width="513" alt="Forward gesture" src="https://github.com/BenMcMillen/HandGestureRobot/assets/105152944/6c41f4a0-0c86-4ee0-8703-0f07a1e00a8f">

All fingers extended upward - robot moves forward

### Stop
<img width="518" alt="Stop gesture" src="https://github.com/BenMcMillen/HandGestureRobot/assets/105152944/0d2a066b-cb20-4e65-894c-ea06d265a1df">

Closed fist - robot stops

### Spin Left
<img width="516" alt="Spin left gesture" src="https://github.com/BenMcMillen/HandGestureRobot/assets/105152944/26e32372-5c37-4009-a1dd-3f0b31ffb769">

Thumb extended left - robot spins counterclockwise

### Spin Right
<img width="520" alt="Spin right gesture" src="https://github.com/BenMcMillen/HandGestureRobot/assets/105152944/a8edfc0e-616b-4a2c-a3a4-d21cc645e4db">

Thumb extended right - robot spins clockwise

## Documentation

For detailed technical documentation, circuit diagrams, and implementation details, see [hand_gesture_robot.pdf](https://github.com/BenMcMillen/HandGestureRobot/files/13884930/hand_gesture_robot.pdf).

## Troubleshooting

**Camera not detected**: Ensure webcam permissions are enabled and no other application is using the camera

**Serial connection failed**: Verify the correct port is specified and Arduino is properly connected

**Gestures not recognized**: Ensure good lighting conditions and position hand clearly in frame

**Robot not responding**: Check NRF24L01 connections and ensure both modules are powered correctly

## Contributors

- **Benjamin McMillen** - Project Lead & Development
- **Sean Kim** - Hardware Integration
- **Nathan Sivalingam** - Testing & Documentation

## Acknowledgments

This project was inspired by and adapted from:
- [Hand Gesture Recognition Tutorial](https://www.youtube.com/watch?v=a7B5EZVHHkw&t=250s) - Adapted for hand control implementation
- [Arduino NRF24L01 Wireless Communication](https://howtomechatronics.com/tutorials/arduino/arduino-wireless-communication-nrf24l01-tutorial/) - Transmitter and receiver Arduino code reference

## License

This project is open source and available for educational purposes.

## Future Enhancements

- Additional gesture controls (backward, variable speed)
- Mobile app interface
- Obstacle detection and avoidance
- Multiple robot control
- Gesture training mode for custom commands
