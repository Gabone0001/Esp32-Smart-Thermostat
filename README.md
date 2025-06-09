ESP32 Smart Thermostat V1.5

A Wi-Fi-connected smart thermostat built on the ESP32 platform. It provides real-time temperature and humidity monitoring, PID-controlled heating, and a full-featured web interface for configuration and alerts.


Overview

Overview

This project uses a single thermostat setup powered by an ESP32 board (tested on the Heltec WiFi Kit 32 V3). It is equipped with a BME280 sensor to monitor temperature and humidity in real time, and it manages a heating system using a Solid State Relay (SSR) controlled by a PID algorithm.

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

Adafruit BME280 - https://github.com/adafruit/Adafruit_BME280_Library

Adafruit Unified Sensor - https://github.com/adafruit/Adafruit_Sensor

ESPAsyncWebServer - https://github.com/me-no-dev/ESPAsyncWebServer

AsyncTCP - https://github.com/me-no-dev/AsyncTCP

ESP Mail Client - https://github.com/mobizt/ESP-Mail-Client

HT_SSD1306Wire.h - from Heltec ESP32 Library: https://github.com/Heltec-Aaron-Lee/WiFi_Kit_series


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

Input:

Sender Email

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

License

This project is licensed under the MIT License. See the LICENSE file for details.

Author

Developed by Gabone (Gabriel M) – June 2025

Feel free to open an issue or submit a pull request to contribute!

Disclaimer

This project uses open-source tools and AI-assisted development features. While care has been taken to ensure the functionality and reliability of the code, it is provided "as is" without any warranty. Always validate critical systems in a safe environment before deployment.

The AI-generated content should be reviewed by developers and not relied upon for mission-critical or safety-related implementations without further testing and validation.

This project is created by a beginner hobbyist for learning purposes. Feedback and improvements are welcome.
