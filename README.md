# CAN-Driven-Vehicle-Monitoring-and-Driver-Assistance-System1
CAN-Driven Vehicle Monitoring and Driver Assistance System

📖 Overview

The CAN-Driven Vehicle Monitoring and Driver Assistance System is a three-node embedded system developed using the LPC2129 ARM7 microcontroller and the Controller Area Network (CAN) protocol.

The system is designed to monitor important vehicle parameters and provide driver assistance functions through distributed CAN nodes. It monitors fuel level and engine temperature, controls left/right indicators, detects reverse obstacles, and displays the vehicle status on a centralized LCD dashboard.

The system consists of:

Main Node

Indicator & Reverse Alert Node

Fuel Node

The three nodes communicate through a CAN bus using MCP2551 CAN transceivers.

🎯 Project Objective

To design and implement a three-node CAN-based vehicle monitoring and driver assistance system capable of:

Monitoring fuel level

Monitoring engine temperature

Detecting obstacles during reverse operation

Controlling left and right indicators

Providing SAFE, WARNING, and STOP reverse-alert status

Displaying real-time vehicle information on a centralized LCD

✨ Key Features

✅ Three-node CAN communication

✅ LPC2129 ARM7-based embedded system

✅ Engine temperature monitoring using DS18B20

✅ Fuel percentage measurement using on-chip ADC

✅ Fuel information transmitted through CAN

✅ Forward and Reverse mode selection

✅ Left and Right indicator control through CAN

✅ Reverse obstacle detection using HC-SR05 ultrasonic sensor

✅ Buzzer-based reverse warning

✅ SAFE / WARNING / STOP status generation

✅ Centralized LCD dashboard

✅ External interrupt-based switch handling

🏗️ System Architecture

1. Main Node

The Main Node acts as the central controller of the complete vehicle monitoring and driver assistance system.

Its responsibilities are:

Continuously reads engine temperature from the DS18B20 sensor.

Displays engine temperature on the LCD.

Receives fuel percentage from the Fuel Node through CAN.

Displays the received fuel percentage on the LCD.

Monitors the Mode Selection Switch using an external interrupt.

Selects either Forward Mode or Reverse Mode.

Forward Mode

When Forward Mode is selected:

The Main Node monitors the Left Indicator Switch (SW1) and Right Indicator Switch (SW2) using external interrupts.

When the Left Indicator Switch is pressed, a Left Indicator command is sent to the Indicator & Reverse Alert Node through CAN.

When the Right Indicator Switch is pressed, a Right Indicator command is sent through CAN.

Reverse Mode

When Reverse Mode is selected:

The Main Node receives the Reverse Alert Status from the Indicator & Reverse Alert Node through CAN.

Based on the received status, the LCD displays:

SAFE

WARNING

STOP

The LCD continuously displays:

Engine Temperature

Fuel Percentage

Vehicle Mode

Reverse Alert Status

🚦 2. Indicator & Reverse Alert Node

This node performs two functions:

Vehicle indicator control

Reverse obstacle detection

Forward Mode Operation

When Forward Mode is received:

Reverse obstacle detection remains disabled.

A Left Indicator command causes the left indicator LEDs to blink.

A Right Indicator command causes the right indicator LEDs to blink.

An Indicator OFF command switches OFF all indicator LEDs.

Reverse Mode Operation

When Reverse Mode is received:

Normal indicator operation is disabled.

The HC-SR05 ultrasonic sensor is enabled.

The node continuously measures the distance between the vehicle and an obstacle.

The measured distance is compared with predefined:

Safe range

Warning range

Critical range

Reverse Alert Logic

Obstacle Condition

Buzzer

LED

CAN Status

Safe distance

OFF

OFF

SAFE

Warning range

Intermittent

—

WARNING

Critical range

Continuous

Reverse Alert LED ON

STOP

The corresponding status is transmitted to the Main Node through CAN.

When Forward Mode is selected again, the node returns to indicator-control operation.

⛽ 3. Fuel Node

The Fuel Node is responsible for monitoring the fuel level.

Operation:

The fuel gauge provides an analog input.

The LPC2129 on-chip ADC reads the input.

The ADC value is converted into Fuel Percentage.

The Fuel Percentage is periodically transmitted to the Main Node through CAN.

When there is a significant change in fuel percentage, the updated value is transmitted immediately.

🔄 CAN Communication

The system uses CAN communication to exchange information between the three nodes.

Main Node → Indicator & Reverse Alert Node

The Main Node sends:

Vehicle Mode

Left Indicator command

Right Indicator command

Indicator OFF command

Indicator & Reverse Alert Node → Main Node

The node sends:

SAFE status

WARNING status

STOP status

Fuel Node → Main Node

The Fuel Node sends:

Fuel Percentage

This distributed architecture allows each node to perform a dedicated function while the Main Node provides centralized monitoring.

🧩 Hardware Requirements

LPC2129 ARM7 Microcontroller

CAN Transceiver – MCP2551

LEDs

LCD

HC-SR05 Ultrasonic Sensor

Fuel Gauge

Switches

USB-to-UART Converter

DS18B20 Temperature Sensor

Buzzer

💻 Software Requirements

Embedded C Programming

Keil-C Compiler

Flash Magic

🔧 Technologies / Concepts Used

Embedded C

LPC2129 ARM7 Architecture

General Purpose I/O

On-chip ADC

CAN Interface

CAN Protocol

External Interrupts

LCD Interfacing

DS18B20 Temperature Sensor

HC-SR05 Ultrasonic Sensor

Fuel Gauge Interfacing

GPIO / LED Control

UART / USB-to-UART for development and debugging

🔄 Implementation Sequence

The project is implemented and tested module-by-module before complete system integration.

Step 1 – Project Setup

Create the project folder and separate folders for:

Main Node

Indicator & Reverse Alert Node

Fuel Node

Step 2 – LCD Testing

Verify LCD interfacing by displaying:

Character constants

String constants

Integer constants

Step 3 – ADC Testing

Connect variable voltage through a potentiometer.

Read the input using the LPC2129 on-chip ADC.

Display the ADC value on the LCD.

Step 4 – Fuel Percentage

Develop the fuel percentage calculation.

Display the calculated fuel percentage on the LCD.

Step 5 – External Interrupt Testing

Test external interrupt functionality.

Count interrupt occurrences.

Display the interrupt count on the LCD.

Step 6 – HC-SR05 Testing

Generate the ultrasonic trigger pulse.

Measure the echo pulse duration.

Calculate obstacle distance.

Display the measured distance on the LCD.

Verify the measurement for different obstacle positions.

Step 7 – Temperature Sensor Testing

Interface the DS18B20 temperature sensor.

Read engine temperature.

Display engine temperature on the LCD.

Step 8 – CAN Testing

Test the basic CAN code on hardware.

Analyze CAN transmission and reception.

Verify communication between nodes.

Step 9 – Node Development

Develop the final software for:

Main Node

Indicator & Reverse Alert Node

Fuel Node

Step 10 – System Integration

Connect all three nodes through the CAN bus and verify the complete vehicle monitoring and driver assistance system.

📊 System Flow

                         CAN BUS
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
        ▼                   ▼                   ▼
 ┌─────────────┐   ┌──────────────────┐   ┌─────────────┐
 │  MAIN NODE  │   │ INDICATOR &      │   │  FUEL NODE  │
 │             │   │ REVERSE ALERT    │   │             │
 │ LPC2129     │   │ NODE             │   │ LPC2129     │
 │             │   │ LPC2129          │   │ + ADC       │
 └──────┬──────┘   └────────┬─────────┘   └──────┬──────┘
        │                   │                    │
        │                   │                    │
   ┌────┴─────┐       ┌─────┴──────┐        ┌───┴───────┐
   │ LCD      │       │ LEDs       │        │ Fuel Gauge│
   │ DS18B20  │       │ HC-SR05    │        │           │
   │ Switches │       │ Buzzer     │        │ ADC       │
   └──────────┘       └────────────┘        └───────────┘

🖥️ Centralized Dashboard

The Main Node LCD displays the real-time vehicle status:

Engine Temperature : XX °C
Fuel Percentage    : XX %
Vehicle Mode       : FORWARD / REVERSE
Reverse Alert      : SAFE / WARNING / STOP

📂 Suggested Project Folder Structure

CAN-Driven-Vehicle-Monitoring-and-Driver-Assistance-System/
│
├── Main_Node/
│   ├── main.c
│   ├── can.c
│   ├── lcd.c
│   ├── ds18b20.c
│   └── ext_interrupt.c
│
├── Indicator_Reverse_Alert_Node/
│   ├── main.c
│   ├── can.c
│   ├── hc_sr05.c
│   ├── buzzer.c
│   └── indicator.c
│
├── Fuel_Node/
│   ├── main.c
│   ├── can.c
│   └── adc.c
│
├── Docs/
│   └── block_diagram.png
│
└── README.md

🚘 Applications

Automotive Embedded Systems

CAN-Based ECU Communication

Vehicle Monitoring

Reverse Parking Assistance

Vehicle Indicator Control

Distributed Embedded Systems

Driver Assistance Systems

🎓 Learning Outcomes

Through this project, the following concepts are covered:

Embedded-C programming

LPC2129 ARM7 architecture

GPIO interfacing

ADC interfacing

External interrupt handling

CAN protocol and CAN communication

LCD interfacing

Temperature sensor interfacing

Ultrasonic obstacle detection

Multi-node ECU communication

Distributed embedded-system design

👨‍💻 Project By
BHARGAV BASWANI

B.Tech – Electronics and Communication Engineering

Vector India Major Project

Embedded Systems | CAN | LPC2129
