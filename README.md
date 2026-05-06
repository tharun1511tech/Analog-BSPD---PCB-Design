# 🚗 Analog BSPD for Formula Student EV

## 📌 Overview
This project implements a **Formula Student EV compliant Analog Brake System Plausibility Device (BSPD)**.

The BSPD is a **critical safety system** that monitors braking and power delivery simultaneously and **disconnects the Shutdown Circuit (SDC)** when an unsafe condition is detected.

Unlike software-based systems, this design is **fully analog**, ensuring:
- Deterministic behavior  
- High reliability  
- Compliance with Formula Student safety rules  

---

## 🎯 Objective
The goal of this project is to:
- Design a **rule-compliant analog safety system**
- Detect **simultaneous braking and acceleration**
- Enforce **power and brake thresholds**
- Implement **time-based validation (>500 ms)**
- Create a **hardware fail-safe shutdown mechanism**
- Develop a **2-layer PCB for real-world deployment**

---

## ⚙️ Key Features
- ⚡ Fully analog implementation (no microcontroller)  
- 🔍 Comparator-based threshold detection  
- ⏱ RC-based 500 ms delay validation  
- 🔗 Hardware logic condition (AND operation)  
- 🔒 Fault latching mechanism  
- 🔌 Relay-based Shutdown Circuit control  
- 🛡️ Designed for high EMI automotive environment  

---

## 🧠 Working Principle

The BSPD operates based on **simultaneous condition detection**:

- Brake pressure sensor provides braking input  
- Current sensor provides power delivery input  
- Comparators check if thresholds are exceeded  
- RC circuit ensures fault persists (>500 ms)  
- Logic gate validates combined condition  
- Latch holds fault state  
- Relay opens the Shutdown Circuit (SDC)  

👉 This ensures:
> The vehicle cannot accelerate while braking  

---

## 🔢 Design Calculations

### ⚡ Power to Current Conversion
\[
I = \frac{P}{V} = \frac{5000}{400} = 12.5A
\]

### 🔌 Sensor Voltage Thresholds
- Current threshold → **1.25 V**  
- Brake threshold → **3.0 V**

---

## ⏱ RC Delay Mechanism

The delay is implemented using an RC charging circuit:

\[
V(t) = V_{cc}(1 - e^{-t/RC})
\]

- R = 100kΩ  
- C = 4.7µF  
- Delay ≈ **470 ms**

👉 Prevents false triggering due to transient noise  

---

## 🔗 Logic Implementation

Let:
- B = Brake High  
- C = Current High  
- T = Delay satisfied  

\[
BSPD = B \cdot C \cdot T
\]

👉 Fault triggers only when **all conditions are true**

---

## 🔒 Latching Mechanism
- Once triggered, system **remains in fault state**
- Reset requires:
  - Power cycle  
  - OR optional 10s auto-reset  

👉 Ensures safety compliance  

---

## 🔌 Hardware Components

- Comparators (LM393)  
- Resistors  
- Capacitors  
- NPN Transistor  
- Relay  
- Flyback Diode  
- PCB (2-layer design)  

---

## ⚙️ Role of Each Component

### 🔍 Comparators
- Detect threshold crossing  
- Convert analog signals → digital logic  

---

### 🔌 Resistors
- Set voltage references  
- Limit current  
- Define RC timing  

---

### ⚡ Capacitor
- Creates **time delay (RC behavior)**  
- Acts as:
> fault validation element  

---

### 🔀 Transistor
- Drives relay  
- Acts as:
> switching stage  

---

### 🔁 Relay
- Physically disconnects Shutdown Circuit  
- Ensures:
> complete power isolation  

---

## 🧪 System Behavior

- Normal condition → System inactive  
- Brake + Power → Fault condition starts  
- If <500 ms → Ignored  
- If >500 ms → Trigger activated  
- Relay opens → SDC cut off  
- System latches until reset  

---

## 🧪 Observations

- Eliminates false triggers due to noise  
- Ensures reliable safety shutdown  
- Fully deterministic behavior  
- Independent of software failures  
- Suitable for harsh automotive environments  

---

## 🚀 Applications

- 🏎️ Formula Student EV safety systems  
- 🚗 Automotive fail-safe circuits  
- ⚡ Industrial protection systems  
- 🔌 Power monitoring systems  
- 🛡️ Safety-critical embedded hardware  

---

## ✅ Result

- Successfully designed **fully analog BSPD**  
- Achieved **rule-compliant safety logic**  
- Implemented **500 ms fault validation**  
- Designed **functional PCB layout**  
- Ensured **reliable shutdown operation**  

---

## 🔮 Future Scope

- Improve EMI shielding techniques  
- Optimize PCB size and routing  
- Add redundancy for higher safety  
- Integrate diagnostic indicators  
- Validate under real vehicle conditions  

---

## 🧠 Key Concepts Used

- Analog Circuit Design  
- Comparator Circuits  
- RC Timing Circuits  
- Boolean Logic Implementation  
- Power Electronics  
- Automotive Safety Systems  

---

## 👨‍💻 Author

**Tharun S**

---

## ⭐ If you like this project

Give it a ⭐ on GitHub!
