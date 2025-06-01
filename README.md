# RFID-and-Computer-Vision-based-Secure-Access-Control-System

# RFID Access Control System with additional outputs

This project is an RFID-based access control system built using an Arduino, MFRC522 RFID reader, and multiple output components like LEDs, a relay, and an input switch. The system grants or denies access based on the detected RFID tag and the state of the input switch, with feedback provided via LEDs and a relay.

💡 Overview
Uses RFID authentication with pre-authorized UID(s).

Includes an input switch to override or supplement RFID access.

Visual indicators (Green, Red, Blue LEDs) show status clearly.

A relay simulates unlocking a door or activating a device.

Controlled through RFID, switch input, or serial commands.

🧰 Hardware Required
Arduino Board (Uno, Mega, Nano)

MFRC522 RFID Reader

RFID Tags/Cards

Green LED (Access granted)

Red LED (Access denied)

Blue LED (Relay indicator)

Relay Module

Input Switch (e.g. pushbutton)

Jumper Wires & Breadboard

🔌 Pin Configuration
RFID Module (MFRC522)
MFRC522 Pin	Arduino Pin
SDA	10
SCK	13
MOSI	11
MISO	12
RST	9
GND	GND
3.3V	3.3V
IRQ	Not Connected

Output Components
Component	Arduino Pin
Green LED	2
Red LED	3
Relay	4
Input Switch	5
Blue LED	6

🧠 Setup Instructions
Open Arduino IDE.

Install the MFRC522 library (Sketch > Include Library > Manage Libraries, then search "MFRC522").

Wire the hardware as per the pin configuration above.

Upload the provided Arduino sketch.

Open Serial Monitor (9600 baud, newline enabled).

Scan an RFID tag and note the UID printed.

Update the code where it checks the UID:

cpp
Copy
Edit
if (content.substring(1) == "XX XX XX XX") // Replace with your tag's UID
Upload the modified code to your Arduino.

Use the serial monitor to send commands:

"1": Trigger access attempt

"2": Force access denied

"3": Turn off all outputs

✅ Testing Scenarios
Condition	Output Behavior
Authorized UID + Switch HIGH + Command 1	Green ON, Red OFF, Relay ON, Blue ON (3.5s)
Authorized UID + Switch LOW + Command 1	Green ON, Red ON, Relay OFF, Blue OFF (0.5s)
Unauthorized UID + Switch HIGH + 1	Green ON, Red ON, Relay OFF, Blue OFF (0.5s)
Unauthorized UID + Switch LOW + 1	Green OFF, Red ON, Relay OFF, Blue OFF (0.5s)
Command 2 (Force Deny)	Green OFF, Red ON, Relay OFF, Blue OFF (0.5s)
Command 3 (Turn Off All Outputs)	Green OFF, Red OFF, Relay OFF, Blue OFF

🌐 Language Support
Bahasa Indonesia version

📌 Notes
You can expand this project by adding more RFID tags or a database.

Consider using EEPROM to store authorized UIDs.

Relay can be connected to any device you want to control (e.g. door lock).
