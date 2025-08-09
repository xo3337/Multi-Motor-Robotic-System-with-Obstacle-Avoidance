# 🤖 Multi-Motor Robotic System with Obstacle Avoidance

## 🧠 Project Overview

This Arduino-based project controls **4 DC motors** using the **L293D motor driver**

It is designed to demonstrate:
- Coordinated multi-motor control
- Sequential movement logic
- Obstacle detection and response
---

## 🔧 Hardware Used

| Component           | Quantity |
|--------------------|----------|
| Arduino UNO R3     | 1        |
| L293D Motor Driver | 1–2      |
| DC Motors          | 4        |
| Battery Pack (4xAA, 6V) | 1    |
| Breadboard + Wires | As needed |

---

## 🧰 Features

### Part 1: Motor Motion Sequence
- 🚗 Move forward for 30 seconds
- 🔄 Move backward for 60 seconds
- ↪️ Alternate between right and left turns for 1 minute (5 seconds each)
- ⛔ Stop


---

## 🔌 Circuit Description
<img width="687" height="814" alt="image" src="https://github.com/user-attachments/assets/720a326c-f97b-4b9f-bfd9-0413e7343263" />


### Power Connections
- **VCC1 (Logic)** → Arduino 5V
- **VCC2 (Motor Power)** → Battery +6V
- **GND** → Shared between battery, Arduino, L293D

### L293D to DC Motors
- 4 motors connected via `INx` and `OUTx` pins
- `EN1` and `EN2` must be tied HIGH (5V or digital HIGH) to enable motor channels

## 🧪 How to Use

1. **Wire all components** as described
2. **Upload the code** from `main.ino` to the Arduino
3. Power the Arduino and motor driver
4. Observe the sequence:
   - Forward → Backward → Turning
   - If an obstacle is detected (≤ 10 cm), system will stop and respond

---


## 📈 code
```
// Motor A pins
int in1 = 2;
int in2 = 3;

// Motor B pins
int in3 = 4;
int in4 = 5;

void setup() {
  pinMode(9, OUTPUT);
  pinMode(in1, OUTPUT);
  pinMode(in2, OUTPUT);
  pinMode(in3, OUTPUT);
  pinMode(in4, OUTPUT);
}

void loop() {
  // Move both motors forward
  digitalWrite(9, HIGH);
  digitalWrite(in1, HIGH);
  digitalWrite(in2, LOW);

  digitalWrite(in3, HIGH);
  digitalWrite(in4, LOW);

  delay(3000); // Run for 3 seconds

  // Move both motors backward
  digitalWrite(in1, LOW);
  digitalWrite(in2, HIGH);

  digitalWrite(in3, LOW);
  digitalWrite(in4, HIGH);

  delay(3000);

  // Stop motors
  digitalWrite(in1, LOW);
  digitalWrite(in2, LOW);
  digitalWrite(in3, LOW);
  digitalWrite(in4, LOW);

  delay(3000);
}

```

