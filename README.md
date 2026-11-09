# Smart Trash Bin

A low-cost, touchless trash bin that opens its lid automatically when it detects a hand or person nearby, and closes a few seconds after they leave. Built with an Arduino, an ultrasonic sensor, and a servo motor.

Status: working in the Tinkercad simulator. The real hardware build is coming next.

## How it works

1. The HC-SR04 ultrasonic sensor constantly measures the distance in front of the bin.
2. When something is closer than 25 cm, the Arduino tells the servo motor to rotate and lift the lid.
3. The lid stays open while something is still detected.
4. 5 seconds after the last detection, the servo closes the lid.

## Parts list (about $10-15 total)

| Part | Purpose |
|------|---------|
| Arduino Uno (or Nano) | Brain of the project |
| HC-SR04 ultrasonic sensor | Detects hands and people |
| SG90 micro servo | Opens and closes the lid |
| Jumper wires | Connections |
| Power bank or 4xAA batteries | Power supply |
| Plastic bucket or box with a lid | The bin itself |

## Wiring

| Component pin | Arduino pin |
|---------------|-------------|
| Sensor VCC | 5V |
| Sensor TRIG | 9 |
| Sensor ECHO | 10 |
| Sensor GND | GND |
| Servo signal (orange) | 6 |
| Servo power (red) | 5V |
| Servo ground (brown) | GND |

## Circuit

![Circuit diagram]screenshot(368).png

## Demo

![Demo]smart bin video.mp4

## Code

The full Arduino sketch is in [`smart_trash_bin.ino`](smart_trash_bin.ino).

You can change these settings at the top of the file:

- `OPEN_DISTANCE_CM`: how close something must be to open the lid (default 25)
- `CLOSE_DELAY_MS`: how long to wait before closing, in milliseconds (default 5000)
- `OPEN_ANGLE` and `CLOSED_ANGLE`: how far the servo turns

## Future upgrades

- A second sensor inside the bin to detect when it is full, with an LED or buzzer
- ESP32 with WiFi to send a "bin is full" alert to a phone
- Solar panel so it runs without batteries

## What I learned

- Reading distance with an ultrasonic sensor
- Controlling a servo motor
- Using timing (`millis()`) instead of blocking delays
- Designing and testing a circuit in a simulator before buying parts
