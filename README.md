# Esp32-Smart-Thermostat v1.5
A Wi-Fi-connected smart thermostat built on the ESP32 platform. It features real-time temperature and humidity monitoring (via BME280), PID-based heating control, OLED display output, and a responsive web interface for live data, configuration, and email alerts.

Features

Real-time monitoring via BME280 (temperature & humidity)

PID control (Kp, Ki, Kd adjustable via web GUI)

OLED display with IP address, status, and alarms

Wi-Fi setup with auto-reconnect

Web interface for full configuration

Daily and alarm-based email reports via Gmail SMTP

JSON API endpoint for integration

Persistent configuration storage with Preferences library

Hardware Requirements

ESP32 board (tested with Heltec WiFi Kit V3)

BME280 temperature and humidity sensor (I2C)

SSD1306 128x64 OLED display (I2C)

Solid State Relay (SSR) for heater control

3.3V power supply and USB cable

Internet access for NTP and email features

Required Libraries

Install the following libraries via the Arduino Library Manager or download from GitHub:

WiFi (built-in)

ESPmDNS (built-in)

Preferences (built-in)

Wire (built-in)

Adafruit BME280 Library by Adafruit

Adafruit Unified Sensor by Adafruit (dependency for BME280)

ESPAsyncWebServer [https://github.com/me-no-dev/ESPAsyncWebServer]

AsyncTCP [https://github.com/me-no-dev/AsyncTCP]

ESP Mail Client [https://github.com/mobizt/ESP-Mail-Client]

HT_SSD1306Wire.h from Heltec ESP32 library

Note: To use ESPAsyncWebServer, install ESPAsyncTCP first. Ensure your board supports ESP32 and you have installed the latest ESP32 board definitions.

Installation Steps

Install Arduino IDE (version 1.8.19 or later recommended)

Install ESP32 board support:

Open Arduino IDE > Preferences

Add this URL to "Additional Board Manager URLs":

https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json

Go to Tools > Board > Board Manager > Search "ESP32" and install the latest version.

Install Required Libraries (see above)

Connect the hardware:

Wire BME280 to pins GPIO47 (SDA) and GPIO48 (SCL)

Wire SSD1306 OLED to same I2C pins (if shared bus)

Connect SSR to GPIO1

Upload Code:

Select Heltec WiFi Kit 32 (V3) from Tools > Board

Select correct COM port

Upload the sketch from Arduino IDE

Initial Setup:

Connect to the same Wi-Fi network as the ESP32

Open http://esp32.local or find the IP from the Serial Monitor

Configure Wi-Fi, thermostat settings, and email credentials in the web interface

Click Save All Settings (the ESP32 will reboot)

Email Setup Notes

Use Gmail with App Passwords (enable 2FA first)

Fill in:

Sender Email (your Gmail address)

App Password (not the regular password)

Recipient Email (any valid address)

Test the email from the web interface

Web Interface

Access UI: http://esp32.local or the device IP (shown on OLED)

Features:

View live temperature and humidity

Configure Wi-Fi and PID parameters

Set alarm thresholds and logging interval

Configure and test email reporting

Reset to default settings

API Endpoints

/data – JSON output with current temperature, humidity, and heater state

/scan – Returns Wi-Fi SSID list for dropdown

/reset – Clears settings and reboots device

/testemail – Sends a test email

/debug – Dumps stored settings

/set – Receives settings from web interface (POST)

Licensing

MIT License

Developed By

Gabone (Gabriel M) – June 2025

For support, feedback, or contributions, please submit an issue or pull request on GitHub.

