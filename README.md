# ESP32-CAM Telegram Timelapse & Photo Sender

An Arduino sketch for the AI-Thinker ESP32-CAM (OV2640) that captures a photo upon boot, automatically adjusts exposure under low-light or daylight conditions, sends the image directly to Telegram, and puts the device into deep sleep to conserve power.

---

## Features

* **Direct Telegram Integration:** Sends captured JPEG frames straight to your Telegram chat using the `AsyncTelegram2` library.
* **Smart Day/Night Exposure:** Programmatically reads sensor register light levels and adjusts frame length and exposure registers for optimal performance in varying lighting conditions.
* **Deep Sleep Power Saving:** Enters a low-power deep sleep state between captures to save energy.
* **Brownout Protection:** Disables the onboard brownout detector during high-draw operations like Wi-Fi connection and camera initialization.

---

## Hardware Requirements

* **Microcontroller:** AI-Thinker ESP32-CAM module
* **Camera Sensor:** OV2640 CMOS Camera Module
* **Programmer:** USB-to-Serial (FTDI) adapter (operating at 3V3) for uploading code
* **Power Supply:** Stable 5V power source (external power supply recommended during active Wi-Fi transmission to prevent brownouts)

---

## Library Dependencies

Make sure you have the following libraries installed via the Arduino IDE Library Manager before compiling:

* [AsyncTelegram2](https://github.com/cotestatnt/AsyncTelegram2) by cotestatnt
* ESP32 Board definitions (installed via Arduino IDE Board Manager)

---

## Configuration & Setup

1. Clone or download this repository.
2. Open the `.ino` file in the Arduino IDE.
3. Replace the placeholder credentials in the code with your actual network and bot details:
   ```cpp
   const char* ssid = "YOUR_WIFI_SSID";          // Your Wi-Fi network name
   const char* pass = "YOUR_WIFI_PASSWORD";      // Your Wi-Fi password
   const char* token = "YOUR_TELEGRAM_BOT_TOKEN";// Get this from Telegram's BotFather
   int64_t userid = YOUR_TELEGRAM_USER_ID;       // Your numeric Telegram user ID
4. Select your board (AI Thinker ESP32-CAM) in the Arduino IDE, connect your programmer, and flash the code.
