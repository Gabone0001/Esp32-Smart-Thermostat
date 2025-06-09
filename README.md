ESP32 Smart Thermostat V1.5
A Wi-Fi-connected smart thermostat built on the ESP32 platform. It provides real-time temperature and humidity monitoring, PID-controlled heating, and a full-featured web interface for configuration and alerts.

Overview
Designed for reliability, this thermostat is ideal for greenhouses, reptile enclosures, incubators, and more. It offers OLED display output, live sensor updates, persistent settings, and optional email reporting via Gmail.

Hardware Requirements
ESP32 Heltec WiFi Kit V3 (or compatible)
BME280 Sensor (I2C)
SSD1306 OLED Display (128x64, I2C)
Solid State Relay (SSR) for heating control
Internet connection for NTP sync and email features

Required Libraries
Install these libraries in Arduino IDE:
WiFi (built-in)
ESPmDNS (built-in)
Preferences (built-in)
Wire (built-in)
Adafruit BME280 and Adafruit Unified Sensor
ESPAsyncWebServer → GitHub
AsyncTCP → GitHub
ESP Mail Client → GitHub
HT_SSD1306Wire.h → (from Heltec ESP32 library)

Installation Instructions
Install Arduino IDE (1.8.19+)
Install ESP32 Board Support:
Arduino > Preferences > Additional URLs:
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
Boards Manager → Install "esp32"
Install the required libraries (see above)
Wire the components:
BME280 → SDA (GPIO47), SCL (GPIO48)
OLED → I2C (shared with BME280)
SSR → GPIO1
Upload the code to your ESP32 via Arduino IDE
Access the device via http://esp32.local or the shown IP

Web Interface
Access the thermostat interface:
View live temperature, humidity, and heater status
Set Wi-Fi credentials, PID parameters, alarm thresholds
Enable/disable email alerts and schedule daily reports
Send test email and reset settings to defaults

Email Reporting Setup
Use a Gmail account with App Passwords enabled
Input: Sender Email
Gmail App Password
Recipient Email
Schedule daily report and enable alarm alerts

API Endpoints

/ → Loads the main web interface

/data → Returns a JSON payload with temperature, humidity, and heater status

/scan → Returns a list of available Wi-Fi networks in HTML format

/testemail → Sends a test email to the configured recipient

/reset → Resets all stored settings and reboots the device

/set → Accepts POST data to update and save settings

/debug → Returns current saved settings for diagnostics
| /debug      | GET    | Shows stored config debug info       |

Time Zone Setup

The firmware sets the UK time zone with automatic DST:

setenv("TZ", "GMT0BST,M3.5.0/1,M10.5.0", 1);
tzset();

This provides correct local time (GMT or BST) for logs and email reports.

License

This project is licensed under the MIT License. See the LICENSE file for details.

Author

Developed by Gabone (Gabriel M) – June 2025

Feel free to open an issue or submit a pull request to contribute!

Disclaimer: Please note that with this project i have used different AI as help.
