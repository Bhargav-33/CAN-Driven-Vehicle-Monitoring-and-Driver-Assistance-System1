# 🚗 CAN-Driven Vehicle Monitoring and Driver Assistance System

<p align="center">
  <b>Three-Node CAN-Based Automotive Embedded System</b>
</p>

<p align="center">
  🧠 LPC2129 ARM7 &nbsp; | &nbsp;
  💻 Embedded C &nbsp; | &nbsp;
  📡 CAN &nbsp; | &nbsp;
  🚘 Automotive Embedded Systems
</p>

---

## 📖 Overview

The **CAN-Driven Vehicle Monitoring and Driver Assistance System** is a three-node embedded system developed using the **LPC2129 ARM7 microcontroller** and **Controller Area Network (CAN)** protocol.

The system monitors important vehicle parameters and provides driver-assistance functions through distributed CAN nodes.

### 🔹 System Functions

- 🌡️ Engine temperature monitoring
- ⛽ Fuel-level monitoring
- 🚦 Left and right indicator control
- 📏 Reverse obstacle detection
- 🔊 Reverse warning using buzzer
- 🖥️ Centralized LCD dashboard
- 📡 CAN-based communication between multiple nodes

### 🔹 System Nodes

| Node | Function |
|---|---|
| 🖥️ **Main Node** | Central controller, LCD, temperature monitoring and switch handling |
| 🚦 **Indicator & Reverse Alert Node** | Indicator control and reverse obstacle detection |
| ⛽ **Fuel Node** | Fuel measurement and CAN transmission |

The three nodes communicate through a **CAN bus using MCP2551 CAN transceivers**.

---

# 🎯 Project Objective

To design and implement a **three-node CAN-based vehicle monitoring and driver assistance system** capable of:

- ⛽ Monitoring fuel level
- 🌡️ Monitoring engine temperature
- 📏 Detecting obstacles during reverse operation
- 🚦 Controlling left and right indicators
- 🔊 Providing SAFE, WARNING and STOP reverse-alert status
- 🖥️ Displaying real-time vehicle information on a centralized LCD

---

# ✨ Key Features

- 🔗 Three-node CAN communication
- 🧠 LPC2129 ARM7-based embedded system
- 🌡️ DS18B20 engine temperature monitoring
- ⛽ Fuel percentage measurement using on-chip ADC
- 📡 CAN-based fuel information transmission
- 🔄 Forward / Reverse mode selection
- 🚦 Left / Right indicator control
- 📏 HC-SR05 ultrasonic obstacle detection
- 🔊 Buzzer-based reverse warning
- ⚠️ SAFE / WARNING / STOP status
- 🖥️ Centralized LCD dashboard
- ⚡ External interrupt-based switch handling

---

# 🏗️ System Architecture

## 1️⃣ 🖥️ Main Node

The **Main Node** acts as the central controller of the complete system.

### Responsibilities

- 🌡️ Reads engine temperature from the **DS18B20**
- 🖥️ Displays engine temperature on LCD
- ⛽ Receives fuel percentage from Fuel Node through CAN
- 📊 Displays fuel percentage
- ⚡ Monitors Mode Selection Switch using external interrupt
- 🔄 Selects Forward or Reverse Mode

### 🚘 Forward Mode

When Forward Mode is selected:

- ⬅️ Monitors Left Indicator Switch (SW1)
- ➡️ Monitors Right Indicator Switch (SW2)
- 📡 Sends Left Indicator command through CAN
- 📡 Sends Right Indicator command through CAN

### 🔙 Reverse Mode

When Reverse Mode is selected:

- 📡 Receives Reverse Alert Status through CAN
- 🖥️ Displays:

🟢 **SAFE**

🟡 **WARNING**

🔴 **STOP**

---

# 2️⃣ 🚦 Indicator & Reverse Alert Node

This node performs two major functions:

- 🚦 Vehicle indicator control
- 📏 Reverse obstacle detection

## 🚘 Forward Mode

When Forward Mode is received:

- Reverse obstacle detection is disabled
- ⬅️ Left command → Left LEDs blink
- ➡️ Right command → Right LEDs blink
- ⏹️ OFF command → All LEDs OFF

## 🔙 Reverse Mode

When Reverse Mode is received:

1. Normal indicator operation is disabled.
2. HC-SR05 ultrasonic sensor is enabled.
3. Obstacle distance is continuously measured.
4. Distance is compared with predefined ranges.

### ⚠️ Reverse Alert Logic

| 🚧 Condition | 🔊 Buzzer | 💡 LED | 📡 CAN Status |
|---|---|---|---|
| 🟢 Safe | OFF | OFF | **SAFE** |
| 🟡 Warning | Intermittent | — | **WARNING** |
| 🔴 Critical | Continuous | Reverse Alert LED ON | **STOP** |

The corresponding status is transmitted to the **Main Node through CAN**.

---

# 3️⃣ ⛽ Fuel Node

The **Fuel Node** monitors the fuel level.

### 🔄 Working

```text
Fuel Gauge
     ↓
Analog Input
     ↓
LPC2129 ADC
     ↓
ADC Value
     ↓
Fuel Percentage
     ↓
CAN Transmission
     ↓
Main Node
