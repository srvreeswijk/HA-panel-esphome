# Home Assistant Wall/Desk Panel — ESPHome + LVGL Dashboard

Updated to ESPHome 2025.10.5

This project transforms a cheap ESP32-based smart panel into a **custom mini-dashboard for Home Assistant** that also functions as a **fully working smart switch/relay** (supports **1-gang and 3-gang** models).

I use it as a direct replacement for several wall switches, extending my Home Assistant setup with:

- Heating & thermostat controls  
- Multi-room lighting and switch control  
- RGBW ambient light control  
- Front-door camera view  
- Quick-access widgets and top status indicators  

A status bar at the top displays:
- **Boiler heating state**
- **Front door open/closed**
- **Front door locked/unlocked**

This is an **excellent, low-cost device** that works as both a **smart switch** and a **compact Home Assistant dashboard**, powered entirely by **ESPHome** and **LVGL**.

---

## Screenshots

<img src="https://community-assets.home-assistant.io/original/4X/1/3/3/1339b489be02221adcba378b4462c97992f19f59.jpeg" width="50%" />

<img src="https://community-assets.home-assistant.io/original/4X/f/9/7/f975f971d55742fceda674031b30953f017fb104.jpeg" width="50%" />

---

## Technical Specifications

**Hardware**
- Guition ESP32-S3 4.0" IPS Display (480×480)
- Model: *ESP32-4848S040*
- Capacitive touchscreen
- 16 MB Flash, 8 MB PSRAM
- Supports 1-gang or 3-gang relay/switch models

**Software**
- **ESPHome 2025.10.5**
- **LVGL UI Engine**
- ESP-IDF for improved performance
- OTA updates
- Home Assistant API integration

---

## Features

### Page 1 — Home & Clock
- Live time, weekday & date synced from HA
- Weather icon + description + outside temperature
- House temperature
- Quick-access buttons:
  - Corridor light
  - Stairs light
  - Night Light (RGBW control)
- Styled background with LVGL theme

### Page 2 — Heating Controls
- Heating Master toggle (1-cycle or continuous)
- Boiler ON/OFF tile
- Temperature setpoint (+/–)
- Room-by-room heating switches:
  - Bedroom  
  - Living Room  
  - Office  
  - Kids Room  
- Real-time temperature display from HA sensors

### Page 3 — RGBW Night Light
- Independent R, G, B, W sliders  
- Brightness slider  
- Colour preview box  
- Light ON/OFF toggle  
- Full integration with `light.turn_on` and `number.set`

### Page 4 — Additional Buttons Page
- Extra room switches (Office, Kids, Outside, etc.)
- Icons + large touch-friendly tiles
- LVGL grid layout

### General UI/UX
- Top status bar: boiler state, door open, door locked, HA connection
- Boot screen with HA logo + spinner
- Navigation: Prev / Home / Next
- Long-press Home to restart
- Backlight automation:
  - Touch → 100%
  - 30s → 50%
  - 15min → 35%
  - 15min → 0% + anti-burn effect

---

## File Overview

### `ha-panel-1.yaml`
- Base ESPHome configuration (Wi-Fi, OTA, API)
- LVGL setup: fonts, theme, display + touch
- Clock & weather widgets
- Home page light buttons
- Backlight timer and boot sequence

### `ha-panel-2.yaml`
- Heating control page
- Thermostat setpoint (+/–)
- Heating master toggle
- Room heating tiles (Bedroom, Living, Office, Kids)
- Temperature displays
- Home Assistant service bindings

### `ha-panel-3.yaml`
- Complete icon set (Material Design Unicode)
- Full LVGL theme (buttons, sliders, switches)
- Global top status bar widgets
- Navigation bar (prev/home/next)
- Boot screen + spinner
- Full multi-page UI:
  - Clock page
  - Heating page
  - RGBW Light page
  - Buttons page
- All HA service actions and logic

---

## Installation

1. Install **ESPHome**  
2. Copy one of the panel YAML files (or merge your own)  
3. Add your Wi-Fi details to `secrets.yaml`  
4. Create a folder "fonts" and "images" inside your home assistant esphome folder. Copy the files from the repo there. 
5. Flash the panel via SSL/USB  
6. Add the device to Home Assistant (auto-discovered)
7. Enjoy it  