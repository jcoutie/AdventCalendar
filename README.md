# 🎄 Advent Calendar LED Tree

A Wi-Fi controlled **Advent Calendar LED display**, powered by an **ESP8266** and **WS2811 RGB LEDs**.  
Each drawer in a physical Christmas tree advent calendar lights up with a corresponding LED — beautifully animated, web-controlled, and entirely **vibe-coded with ChatGPT**.

---

## ✨ Features

- **Two primary modes:**
  - 💤 **Sleep Mode:** Each LED slowly fades in and out (breathing effect), randomly cycling between red and green.  
  - 🎁 **Advent Mode:**  
    1. A rapid “twinkle” animation that builds excitement.  
    2. A reveal phase:  
       - Past days glow **green**  
       - Future days glow **red**  
       - The current day pulses **yellow**  

- **Smart date logic:**  
  Automatically highlights the current calendar date, clamped to 1–24.

- **Web control panel:**  
  Access via any device on the same network. Includes:
  - Enter/exit Advent Mode  
  - Jump to “Today”  
  - Manually select or step through days  

- **Pseudo-random LED mapping:**  
  LEDs are shuffled in a consistent order based on a seed value (`DATE_SHUFFLE_SEED`).  
  Changing the seed re-arranges the mapping — perfect for creative or physical rearrangements.

- **Debug Mode:**  
  (When enabled in code) shows odd/even LED positions in alternating colours for easy wiring verification.

- **Auto sleep timeout:**  
  If inactive for 3 minutes, it gently returns to Sleep Mode.

---

## 🧠 The ChatGPT Bit

This entire project — from the idea, code, animations, and UI design to the debugging process — was **fully written collaboratively with ChatGPT (GPT-5)**, one message at a time.  
Every improvement, colour tweak, and animation was vibe-coded to perfection.  

---

## ⚙️ Hardware Used

| Component | Description / Notes |
|------------|--------------------|
| **ESP8266MOD (AI-Thinker)** | Wi-Fi microcontroller used to host the web UI and drive the LEDs | https://amzn.to/47Jnhzy
| **WS2811 RGB Pixel LEDs** | 50-LED string (IP68, 12 mm diffused nodes) | https://amzn.to/4p5qf6Z
| **5 V Power Supply** | Shared between LEDs and ESP8266 (VIN and GND connected to common supply) |
| **Data Pin** | Connected to GPIO 4 (`D4`) on the ESP8266 |
| **FastLED Library** | Handles pixel colour and animation control |
| **ESP8266WebServer Library** | Hosts the web interface for control |
* Amazon affiliate links for products if you feel generous, but you can probably find them cheaper on other sites

---

## 🧩 File Overview

| File | Description |
|------|-------------|
| `Advent_v0.11.ino` | Main Arduino sketch containing all LED logic and web server |
| `README.md` | This file — project overview and setup guide |

---

## 🕹️ Setup & Usage

1. **Flash the code** to your ESP8266 (NodeMCU / Wemos D1 Mini recommended).  
2. **Update your Wi-Fi credentials** at the top of the `.ino` file:  
   ```cpp
   const char* WIFI_SSID = "YourWiFiName";
   const char* WIFI_PASS = "YourWiFiPassword";
   ```
3. **Power up** the ESP8266 and WS2811 string with a 5 V supply.
4. Open the **Serial Monitor** to find the ESP’s IP address.
5. Open that IP in a web browser — the control page will appear.
6. Enjoy the sparkle ✨

---

## 🧪 Configuration

At the top of the script you can modify:
```cpp
#define PAST_IS_RED false   // false = past green, true = past red
uint32_t DATE_SHUFFLE_SEED = 1333592070; // change to re-map LED order
```

---

## 💡 Future Ideas

- Integration with Google Home / voice control
- Daily auto-unlock logic synced to the calendar
- Physical button inputs for manual interaction
- MQTT or Home Assistant integration

---

## 📜 License

This project is released under the **MIT License** — share, remix, and enjoy!

---

**Made with love, LEDs, and vibes.**  
*— James Coutie + ChatGPT*
