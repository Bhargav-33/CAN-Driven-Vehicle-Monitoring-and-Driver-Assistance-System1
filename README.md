<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>CAN-Driven Vehicle Monitoring and Driver Assistance System</title>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            font-family: Arial, Helvetica, sans-serif;
            line-height: 1.7;
            background: #f4f7fb;
            color: #222;
        }

        .container {
            max-width: 1100px;
            margin: 30px auto;
            background: #ffffff;
            padding: 45px;
            border-radius: 18px;
            box-shadow: 0 5px 25px rgba(0, 0, 0, 0.08);
        }

        header {
            text-align: center;
            padding: 30px 20px;
            border-radius: 15px;
            background: linear-gradient(135deg, #172554, #2563eb);
            color: white;
            margin-bottom: 35px;
        }

        header h1 {
            margin: 0;
            font-size: 36px;
        }

        header p {
            font-size: 18px;
            margin-top: 12px;
        }

        h2 {
            margin-top: 45px;
            padding-bottom: 10px;
            border-bottom: 3px solid #2563eb;
            color: #172554;
        }

        h3 {
            color: #1d4ed8;
            margin-top: 30px;
        }

        .badge {
            display: inline-block;
            padding: 7px 14px;
            margin: 5px;
            border-radius: 20px;
            background: #e0e7ff;
            color: #1e3a8a;
            font-weight: bold;
            font-size: 14px;
        }

        .node-container {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            margin: 25px 0;
        }

        .node-card {
            padding: 25px;
            border-radius: 14px;
            background: #f8fafc;
            border: 1px solid #dbeafe;
            text-align: center;
            transition: 0.3s;
        }

        .node-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(37, 99, 235, 0.15);
        }

        .node-card h3 {
            margin-top: 0;
        }

        .feature-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px 25px;
        }

        .feature {
            padding: 10px 15px;
            background: #f8fafc;
            border-radius: 8px;
        }

        ul {
            padding-left: 25px;
        }

        li {
            margin: 8px 0;
        }

        .mode-box {
            background: #eff6ff;
            border-left: 5px solid #2563eb;
            padding: 20px;
            margin: 20px 0;
            border-radius: 8px;
        }

        .safe {
            color: #15803d;
            font-weight: bold;
        }

        .warning {
            color: #ca8a04;
            font-weight: bold;
        }

        .stop {
            color: #dc2626;
            font-weight: bold;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 25px 0;
            overflow: hidden;
            border-radius: 10px;
        }

        th {
            background: #172554;
            color: white;
            padding: 14px;
            text-align: left;
        }

        td {
            padding: 13px;
            border-bottom: 1px solid #ddd;
        }

        tr:nth-child(even) {
            background: #f8fafc;
        }

        tr:hover {
            background: #eff6ff;
        }

        pre {
            background: #0f172a;
            color: #e2e8f0;
            padding: 25px;
            border-radius: 12px;
            overflow-x: auto;
            font-family: Consolas, monospace;
            line-height: 1.5;
        }

        code {
            font-family: Consolas, monospace;
        }

        .dashboard {
            max-width: 700px;
            margin: 25px auto;
            padding: 25px;
            background: #111827;
            color: white;
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.15);
        }

        .dashboard h3 {
            text-align: center;
            color: white;
        }

        .dashboard-line {
            padding: 12px;
            border-bottom: 1px solid #374151;
        }

        .image-box {
            text-align: center;
            margin: 30px 0;
        }

        .image-box img {
            max-width: 100%;
            height: auto;
            border-radius: 12px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.12);
        }

        .image-caption {
            margin-top: 10px;
            color: #64748b;
            font-weight: bold;
        }

        .folder {
            margin-top: 20px;
        }

        .info-box {
            background: #f0fdf4;
            border-left: 5px solid #16a34a;
            padding: 20px;
            border-radius: 8px;
            margin: 20px 0;
        }

        .highlight-box {
            background: linear-gradient(135deg, #eff6ff, #dbeafe);
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            margin-top: 30px;
        }

        .highlight-item {
            display: inline-block;
            padding: 8px 14px;
            margin: 5px;
            background: white;
            border-radius: 20px;
            font-weight: bold;
            color: #1e3a8a;
        }

        footer {
            margin-top: 50px;
            padding: 30px;
            background: #172554;
            color: white;
            text-align: center;
            border-radius: 15px;
        }

        .keywords {
            margin-top: 20px;
        }

        .keyword {
            display: inline-block;
            padding: 6px 10px;
            margin: 4px;
            background: #e0e7ff;
            color: #1e3a8a;
            border-radius: 6px;
            font-family: monospace;
        }

        @media (max-width: 800px) {
            .container {
                margin: 10px;
                padding: 25px;
            }

            .node-container {
                grid-template-columns: 1fr;
            }

            .feature-grid {
                grid-template-columns: 1fr;
            }

            header h1 {
                font-size: 28px;
            }
        }
    </style>
</head>

<body>

<div class="container">

    <!-- HEADER -->
    <header>
        <h1>🚗 CAN-Driven Vehicle Monitoring and Driver Assistance System</h1>

        <p>
            Three-Node CAN-Based Automotive Embedded System
        </p>

        <div>
            <span class="badge">🧠 LPC2129 ARM7</span>
            <span class="badge">💻 Embedded C</span>
            <span class="badge">📡 CAN</span>
            <span class="badge">📡 MCP2551</span>
            <span class="badge">🏢 Vector India Major Project</span>
        </div>
    </header>


    <!-- OVERVIEW -->
    <h2>📖 Overview</h2>

    <p>
        The <strong>CAN-Driven Vehicle Monitoring and Driver Assistance System</strong>
        is a <strong>three-node embedded system</strong> developed using the
        <strong>LPC2129 ARM7 microcontroller</strong> and the
        <strong>Controller Area Network (CAN) protocol</strong>.
    </p>

    <p>
        The system is designed to monitor important vehicle parameters and provide
        driver-assistance functions through distributed CAN nodes. It monitors
        <strong>fuel level and engine temperature</strong>, controls
        <strong>left/right indicators</strong>, detects
        <strong>reverse obstacles</strong>, and displays vehicle status on a
        <strong>centralized LCD dashboard</strong>.
    </p>

    <h3>🔹 System Nodes</h3>

    <div class="node-container">

        <div class="node-card">
            <h3>🖥️ Main Node</h3>
            <p>
                Central controller, LCD display, temperature monitoring
                and switch handling.
            </p>
        </div>

        <div class="node-card">
            <h3>🚦 Indicator & Reverse Alert Node</h3>
            <p>
                Indicator control and reverse obstacle detection.
            </p>
        </div>

        <div class="node-card">
            <h3>⛽ Fuel Node</h3>
            <p>
                Fuel-level measurement and CAN transmission.
            </p>
        </div>

    </div>

    <p>
        The three nodes communicate through a <strong>CAN bus</strong>
        using <strong>MCP2551 CAN transceivers</strong>.
    </p>


    <!-- OBJECTIVE -->
    <h2>🎯 Project Objective</h2>

    <p>
        To design and implement a three-node CAN-based vehicle monitoring and
        driver assistance system capable of:
    </p>

    <ul>
        <li>⛽ Monitoring fuel level</li>
        <li>🌡️ Monitoring engine temperature</li>
        <li>🚧 Detecting obstacles during reverse operation</li>
        <li>🚦 Controlling left and right indicators</li>
        <li>🔊 Providing SAFE, WARNING, and STOP reverse-alert status</li>
        <li>🖥️ Displaying real-time vehicle information on a centralized LCD</li>
    </ul>


    <!-- FEATURES -->
    <h2>✨ Key Features</h2>

    <div class="feature-grid">

        <div class="feature">🔗 Three-node CAN communication</div>
        <div class="feature">🧠 LPC2129 ARM7-based embedded system</div>
        <div class="feature">🌡️ Engine temperature monitoring using DS18B20</div>
        <div class="feature">⛽ Fuel percentage measurement using on-chip ADC</div>
        <div class="feature">📡 Fuel information transmitted through CAN</div>
        <div class="feature">🔄 Forward and Reverse mode selection</div>
        <div class="feature">🚦 Left and Right indicator control through CAN</div>
        <div class="feature">📏 Reverse obstacle detection using HC-SR05</div>
        <div class="feature">🔊 Buzzer-based reverse warning</div>
        <div class="feature">⚠️ SAFE / WARNING / STOP status generation</div>
        <div class="feature">🖥️ Centralized LCD dashboard</div>
        <div class="feature">⚡ External interrupt-based switch handling</div>

    </div>


    <!-- MAIN NODE -->
    <h2>🏗️ System Architecture</h2>

    <h3>1️⃣ 🖥️ Main Node</h3>

    <p>
        The <strong>Main Node</strong> acts as the central controller of the
        complete vehicle monitoring and driver assistance system.
    </p>

    <h3>🔹 Responsibilities</h3>

    <ul>
        <li>🌡️ Continuously reads engine temperature from the DS18B20 sensor.</li>
        <li>🖥️ Displays engine temperature on the LCD.</li>
        <li>⛽ Receives fuel percentage from the Fuel Node through CAN.</li>
        <li>📊 Displays the received fuel percentage on the LCD.</li>
        <li>⚡ Monitors the Mode Selection Switch using an external interrupt.</li>
        <li>🔄 Selects either Forward Mode or Reverse Mode.</li>
    </ul>


    <div class="mode-box">

        <h3>🚘 Forward Mode</h3>

        <ul>
            <li>Monitors Left Indicator Switch (SW1) using an external interrupt.</li>
            <li>Monitors Right Indicator Switch (SW2) using an external interrupt.</li>
            <li>Sends Left Indicator command through CAN.</li>
            <li>Sends Right Indicator command through CAN.</li>
        </ul>

    </div>


    <div class="mode-box">

        <h3>🔙 Reverse Mode</h3>

        <ul>
            <li>Receives Reverse Alert Status through CAN.</li>
            <li>Displays the received status on the LCD.</li>
        </ul>

        <p>
            🟢 <strong>SAFE</strong><br>
            🟡 <strong>WARNING</strong><br>
            🔴 <strong>STOP</strong>
        </p>

    </div>


    <!-- INDICATOR NODE -->
    <h2>2️⃣ 🚦 Indicator & Reverse Alert Node</h2>

    <p>
        This node performs two major functions:
    </p>

    <ul>
        <li>🚦 Vehicle indicator control</li>
        <li>🚧 Reverse obstacle detection</li>
    </ul>


    <h3>🚘 Forward Mode Operation</h3>

    <ul>
        <li>Reverse obstacle detection remains disabled.</li>
        <li>⬅️ Left Indicator command → Left indicator LEDs blink.</li>
        <li>➡️ Right Indicator command → Right indicator LEDs blink.</li>
        <li>⏹️ Indicator OFF command → All indicator LEDs switch OFF.</li>
    </ul>


    <h3>🔙 Reverse Mode Operation</h3>

    <ol>
        <li>Normal indicator operation is disabled.</li>
        <li>The HC-SR05 ultrasonic sensor is enabled.</li>
        <li>The node continuously measures obstacle distance.</li>
        <li>The distance is compared with Safe, Warning and Critical ranges.</li>
    </ol>


    <h3>⚠️ Reverse Alert Logic</h3>

    <table>

        <thead>
            <tr>
                <th>🚧 Obstacle Condition</th>
                <th>🔊 Buzzer</th>
                <th>💡 LED</th>
                <th>📡 CAN Status</th>
            </tr>
        </thead>

        <tbody>

            <tr>
                <td>🟢 Safe distance</td>
                <td>OFF</td>
                <td>OFF</td>
                <td class="safe">SAFE</td>
            </tr>

            <tr>
                <td>🟡 Warning range</td>
                <td>Intermittent</td>
                <td>—</td>
                <td class="warning">WARNING</td>
            </tr>

            <tr>
                <td>🔴 Critical range</td>
                <td>Continuous</td>
                <td>Reverse Alert LED ON</td>
                <td class="stop">STOP</td>
            </tr>

        </tbody>

    </table>


    <!-- FUEL NODE -->
    <h2>3️⃣ ⛽ Fuel Node</h2>

    <p>
        The <strong>Fuel Node</strong> is responsible for monitoring the fuel level.
    </p>

    <h3>🔄 Operation</h3>

    <ol>
        <li>⛽ Fuel gauge provides an analog input.</li>
        <li>📥 LPC2129 on-chip ADC reads the input.</li>
        <li>🧮 ADC value is converted into Fuel Percentage.</li>
        <li>📡 Fuel Percentage is periodically transmitted through CAN.</li>
        <li>⚡ Significant changes are transmitted immediately.</li>
    </ol>


    <!-- CAN COMMUNICATION -->
    <h2>🔄 CAN Communication</h2>

    <p>
        The system uses <strong>CAN communication</strong> to exchange
        information between the three nodes.
    </p>

    <h3>🖥️ Main Node ➡️ 🚦 Indicator & Reverse Alert Node</h3>

    <ul>
        <li>🔄 Vehicle Mode</li>
        <li>⬅️ Left Indicator command</li>
        <li>➡️ Right Indicator command</li>
        <li>⏹️ Indicator OFF command</li>
    </ul>

    <h3>🚦 Indicator & Reverse Alert Node ➡️ 🖥️ Main Node</h3>

    <ul>
        <li>🟢 SAFE status</li>
        <li>🟡 WARNING status</li>
        <li>🔴 STOP status</li>
    </ul>

    <h3>⛽ Fuel Node ➡️ 🖥️ Main Node</h3>

    <ul>
        <li>⛽ Fuel Percentage</li>
    </ul>


    <!-- FLOW -->
    <h3>📡 Communication Flow</h3>

<pre>
                  ┌──────────────────────┐
                  │      🖥️ MAIN NODE     │
                  │       LPC2129        │
                  └──────────┬───────────┘
                             │
                     ↕ CAN Communication
                             │
             ┌───────────────┴───────────────┐
             │                               │
             ▼                               ▼
┌──────────────────────────┐     ┌──────────────────────┐
│ 🚦 INDICATOR &           │     │ ⛽ FUEL NODE          │
│    REVERSE ALERT NODE    │     │ LPC2129 + ADC        │
│ LPC2129 + MCP2551        │     │                      │
└──────────────────────────┘     └──────────────────────┘
</pre>


    <!-- HARDWARE -->
    <h2>🧩 Hardware Requirements</h2>

    <table>

        <thead>
            <tr>
                <th>🔧 Component</th>
                <th>Purpose</th>
            </tr>
        </thead>

        <tbody>

            <tr>
                <td>🧠 LPC2129 ARM7</td>
                <td>Main microcontroller</td>
            </tr>

            <tr>
                <td>📡 MCP2551 CAN Transceiver</td>
                <td>CAN bus interface</td>
            </tr>

            <tr>
                <td>💡 LEDs</td>
                <td>Indicator and reverse-alert indication</td>
            </tr>

            <tr>
                <td>🖥️ LCD</td>
                <td>Vehicle status display</td>
            </tr>

            <tr>
                <td>📏 HC-SR05</td>
                <td>Reverse obstacle detection</td>
            </tr>

            <tr>
                <td>⛽ Fuel Gauge</td>
                <td>Fuel-level input</td>
            </tr>

            <tr>
                <td>🔘 Switches</td>
                <td>Mode and indicator control</td>
            </tr>

            <tr>
                <td>🔌 USB-to-UART Converter</td>
                <td>Serial communication/debugging</td>
            </tr>

            <tr>
                <td>🌡️ DS18B20</td>
                <td>Engine temperature sensing</td>
            </tr>

            <tr>
                <td>🔊 Buzzer</td>
                <td>Reverse warning alert</td>
            </tr>

        </tbody>

    </table>


    <!-- SOFTWARE -->
    <h2>💻 Software Requirements</h2>

    <ul>
        <li>📝 Embedded C Programming</li>
        <li>🛠️ Keil-C Compiler</li>
        <li>⚡ Flash Magic</li>
    </ul>


    <!-- TECHNOLOGIES -->
    <h2>🔧 Technologies & Concepts Used</h2>

    <div class="feature-grid">

        <div class="feature">💻 Embedded C</div>
        <div class="feature">🧠 LPC2129 ARM7 Architecture</div>
        <div class="feature">🔌 General Purpose I/O</div>
        <div class="feature">📈 On-chip ADC</div>
        <div class="feature">📡 CAN Interface</div>
        <div class="feature">🔄 CAN Protocol</div>
        <div class="feature">⚡ External Interrupts</div>
        <div class="feature">🖥️ LCD Interfacing</div>
        <div class="feature">🌡️ DS18B20 Temperature Sensor</div>
        <div class="feature">📏 HC-SR05 Ultrasonic Sensor</div>
        <div class="feature">⛽ Fuel Gauge Interfacing</div>
        <div class="feature">💡 GPIO / LED Control</div>
        <div class="feature">🔌 UART / USB-to-UART</div>

    </div>


    <!-- IMPLEMENTATION -->
    <h2>🔄 Implementation Sequence</h2>

    <p>
        The project is implemented and tested <strong>module-by-module</strong>
        before complete system integration.
    </p>

    <h3>1️⃣ Project Setup</h3>

    <ul>
        <li>🖥️ Main Node</li>
        <li>🚦 Indicator & Reverse Alert Node</li>
        <li>⛽ Fuel Node</li>
    </ul>

    <h3>2️⃣ LCD Testing</h3>

    <ul>
        <li>Character constants</li>
        <li>String constants</li>
        <li>Integer constants</li>
    </ul>

    <h3>3️⃣ ADC Testing</h3>

    <ul>
        <li>Connect variable voltage through a potentiometer.</li>
        <li>Read input using LPC2129 on-chip ADC.</li>
        <li>Display ADC value on LCD.</li>
    </ul>

    <h3>4️⃣ Fuel Percentage</h3>

    <ul>
        <li>Develop fuel percentage calculation.</li>
        <li>Display calculated fuel percentage on LCD.</li>
    </ul>

    <h3>5️⃣ External Interrupt Testing</h3>

    <ul>
        <li>Test external interrupt functionality.</li>
        <li>Count interrupt occurrences.</li>
        <li>Display interrupt count on LCD.</li>
    </ul>

    <h3>6️⃣ HC-SR05 Testing</h3>

    <ul>
        <li>Generate ultrasonic trigger pulse.</li>
        <li>Measure echo pulse duration.</li>
        <li>Calculate obstacle distance.</li>
        <li>Display measured distance on LCD.</li>
        <li>Verify distance for different obstacle positions.</li>
    </ul>

    <h3>7️⃣ Temperature Sensor Testing</h3>

    <ul>
        <li>Interface DS18B20 temperature sensor.</li>
        <li>Read engine temperature.</li>
        <li>Display engine temperature on LCD.</li>
    </ul>

    <h3>8️⃣ CAN Testing</h3>

    <ul>
        <li>Test CAN code on hardware.</li>
        <li>Analyze CAN transmission and reception.</li>
        <li>Verify communication between nodes.</li>
    </ul>

    <h3>9️⃣ Node Development</h3>

    <ul>
        <li>🖥️ Main Node</li>
        <li>🚦 Indicator & Reverse Alert Node</li>
        <li>⛽ Fuel Node</li>
    </ul>

    <h3>🔟 System Integration</h3>

    <p>
        Connect all three nodes through the <strong>CAN bus</strong> and verify
        the complete vehicle monitoring and driver assistance system.
    </p>


    <!-- SYSTEM FLOW -->
    <h2>📊 System Flow</h2>

<pre>
                         📡 CAN BUS
                             │
          ┌──────────────────┼──────────────────┐
          │                  │                  │
          ▼                  ▼                  ▼
   ┌──────────────┐  ┌──────────────────┐  ┌──────────────┐
   │ 🖥️ MAIN NODE │  │ 🚦 INDICATOR &   │  │ ⛽ FUEL NODE │
   │              │  │ REVERSE ALERT    │  │              │
   │ LPC2129      │  │ NODE             │  │ LPC2129      │
   │              │  │ LPC2129          │  │ + ADC        │
   └──────┬───────┘  └────────┬─────────┘  └──────┬───────┘
          │                   │                   │
     ┌────┴─────┐       ┌─────┴──────┐       ┌────┴──────┐
     │ 🖥️ LCD   │       │ 💡 LEDs    │       │ ⛽ Fuel    │
     │ 🌡️ DS18B20│      │ 📏 HC-SR05 │       │ 📈 ADC     │
     │ 🔘 Switch│       │ 🔊 Buzzer  │       │            │
     └──────────┘       └────────────┘       └────────────┘
</pre>


    <!-- DASHBOARD -->
    <h2>🖥️ Centralized Dashboard</h2>

    <p>
        The <strong>Main Node LCD</strong> displays the real-time vehicle status:
    </p>

    <div class="dashboard">

        <h3>🚗 VEHICLE MONITORING SYSTEM</h3>

        <div class="dashboard-line">
            🌡️ <strong>Engine Temperature:</strong> XX °C
        </div>

        <div class="dashboard-line">
            ⛽ <strong>Fuel Level:</strong> XX %
        </div>

        <div class="dashboard-line">
            🚘 <strong>Vehicle Mode:</strong> FORWARD / REVERSE
        </div>

        <div class="dashboard-line">
            ⚠️ <strong>Reverse Alert:</strong> SAFE / WARNING / STOP
        </div>

    </div>


    <!-- BLOCK DIAGRAM -->
    <h2>🖼️ Block Diagram</h2>

    <div class="image-box">

        <img
            src="https://github.com/user-attachments/assets/6fecfdc6-9760-45b8-810a-9d2933fc5870"
            alt="CAN Vehicle Monitoring System Block Diagram"
        >

        <div class="image-caption">
            CAN-Driven Vehicle Monitoring and Driver Assistance System
        </div>

    </div>


    <!-- FOLDER STRUCTURE -->
    <h2>📂 Project Folder Structure</h2>

<pre>
CAN-Driven-Vehicle-Monitoring-and-Driver-Assistance-System/
│
├── 📁 Main_Node/
│   ├── 📄 main.c
│   ├── 📄 can.c
│   ├── 📄 lcd.c
│   ├── 📄 ds18b20.c
│   └── 📄 ext_interrupt.c
│
├── 📁 Indicator_Reverse_Alert_Node/
│   ├── 📄 main.c
│   ├── 📄 can.c
│   ├── 📄 hc_sr05.c
│   ├── 📄 buzzer.c
│   └── 📄 indicator.c
│
├── 📁 Fuel_Node/
│   ├── 📄 main.c
│   ├── 📄 can.c
│   └── 📄 adc.c
│
├── 📁 Docs/
│   └── 🖼️ block_diagram.png
│
└── 📄 README.md
</pre>


    <!-- OUTPUT -->
    <h2>📸 Project Output</h2>

    <h3>🖥️ Dashboard Display</h3>

    <div class="image-box">

        <img
            src="https://github.com/user-attachments/assets/838985a8-b1c9-4cbe-b897-a3b15152e844"
            alt="Vehicle Monitoring Dashboard Output"
        >

        <div class="image-caption">
            Real-Time Vehicle Monitoring Dashboard
        </div>

    </div>


    <h3>🏗️ Complete Setup</h3>

    <div class="image-box">

        <img
            src="https://github.com/user-attachments/assets/cee4db71-c8f6-4ec6-b538-d4f70fa01f9e"
            alt="Complete Project Setup"
        >

        <div class="image-caption">
            Complete CAN Vehicle Monitoring System Setup
        </div>

    </div>


    <!-- APPLICATIONS -->
    <h2>🚘 Applications</h2>

    <div class="feature-grid">

        <div class="feature">🚗 Automotive Embedded Systems</div>
        <div class="feature">📡 CAN-Based ECU Communication</div>
        <div class="feature">📊 Vehicle Monitoring</div>
        <div class="feature">🅿️ Reverse Parking Assistance</div>
        <div class="feature">🚦 Vehicle Indicator Control</div>
        <div class="feature">🔗 Distributed Embedded Systems</div>
        <div class="feature">🛡️ Driver Assistance Systems</div>

    </div>


    <!-- LEARNING -->
    <h2>🎓 Learning Outcomes</h2>

    <ul>
        <li>💻 Embedded-C Programming</li>
        <li>🧠 LPC2129 ARM7 Architecture</li>
        <li>🔌 GPIO Interfacing</li>
        <li>📈 ADC Interfacing</li>
        <li>⚡ External Interrupt Handling</li>
        <li>📡 CAN Protocol and CAN Communication</li>
        <li>🖥️ LCD Interfacing</li>
        <li>🌡️ Temperature Sensor Interfacing</li>
        <li>📏 Ultrasonic Obstacle Detection</li>
        <li>🔗 Multi-Node ECU Communication</li>
        <li>🏗️ Distributed Embedded-System Design</li>
    </ul>


    <!-- PROJECT INFO -->
    <h2>👨‍💻 Project Information</h2>

    <div class="info-box">

        <p>
            <strong>👤 Project By:</strong><br>
            BHARGAV BASWANI
        </p>

        <p>
            <strong>🎓 Education:</strong><br>
            B.Tech – Electronics and Communication Engineering
        </p>

        <p>
            <strong>🏢 Project:</strong><br>
            Vector India Major Project
        </p>

        <p>
            <strong>🛠️ Domain:</strong><br>
            Embedded Systems | CAN | LPC2129
        </p>

    </div>


    <!-- HIGHLIGHTS -->
    <h2>⭐ Project Highlights</h2>

    <div class="highlight-box">

        <span class="highlight-item">🚗 Automotive Embedded System</span>
        <span class="highlight-item">📡 Three-Node CAN Network</span>
        <span class="highlight-item">🧠 LPC2129 ARM7</span>
        <span class="highlight-item">🌡️ Temperature Monitoring</span>
        <span class="highlight-item">⛽ Fuel Monitoring</span>
        <span class="highlight-item">📏 Reverse Obstacle Detection</span>
        <span class="highlight-item">🚦 Indicator Control</span>
        <span class="highlight-item">🔊 Driver Alert System</span>
        <span class="highlight-item">🖥️ Real-Time LCD Dashboard</span>

    </div>


    <!-- KEYWORDS -->
    <h2>📌 Keywords</h2>

    <div class="keywords">

        <span class="keyword">Embedded C</span>
        <span class="keyword">LPC2129</span>
        <span class="keyword">ARM7</span>
        <span class="keyword">CAN</span>
        <span class="keyword">MCP2551</span>
        <span class="keyword">ECU</span>
        <span class="keyword">Automotive</span>
        <span class="keyword">DS18B20</span>
        <span class="keyword">HC-SR05</span>
        <span class="keyword">ADC</span>
        <span class="keyword">GPIO</span>
        <span class="keyword">External Interrupt</span>
        <span class="keyword">LCD</span>
        <span class="keyword">UART</span>
        <span class="keyword">Vehicle Monitoring</span>
        <span class="keyword">Driver Assistance</span>

    </div>


    <!-- FOOTER -->
    <footer>

        <h2 style="color:white; border:none;">
            🚗 CAN-Driven Vehicle Monitoring and Driver Assistance System
        </h2>

        <p>
            💻 Embedded C &nbsp; | &nbsp;
            🧠 LPC2129 ARM7 &nbsp; | &nbsp;
            📡 CAN &nbsp; | &nbsp;
            🚘 Automotive Embedded Systems
        </p>

        <p>
            👨‍💻 <strong>BHARGAV BASWANI</strong>
        </p>

    </footer>

</div>

</body>
</html>
