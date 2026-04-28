# ESPHome IR → BLE Keyboard Bridge

ESPHome-based bridge that converts IR signals into BLE keyboard inputs to control an Android TV device (e.g. Xiaomi Mi Box S) using a Logitech Harmony Touch.

---

## Hardware

- ESP32-C3 Super Mini  
- Inteset IR Receiver Extender Cable (38–56 kHz)  
  https://intesettech.com/products/inteset-38-56-khz-wideband-infrared-ir-receiver-extender-cable-for-cable-boxes-dvrs-stbs  

> Other IR receivers should work as well.

---

## References

- https://github.com/guyman70718/esphome-blekeyboard  

The upstream repository has an issue where multimedia keys are not properly released.  
This project uses a fork that fixes key release by addressing individual buttons directly (enabling proper key hold behavior).  
Note: “release all” functionality still does not work reliably.

---

## Wiring

```
IR Receiver (3.5mm plug)           ESP32-C3 Super Mini
--------------------------------   -----------------------
 Tip   (Red / VCC)   ----------->   3.3V
 Ring  (Blue / Data) ----------->   GPIO0
 Sleeve(Black / GND) ----------->   GND
```

---

## Setup

1. Add a **Sony KDL-40BX400** device (arbitrary but compatible choice) to your Logitech Harmony Touch.  
2. Flash the ESP32-C3 with this ESPHome configuration.  
3. Pair the ESP32 with your Android TV device (e.g. Xiaomi Mi Box S) via Bluetooth.  

---

## Usage

This setup emulates a BLE keyboard, so it should work with most Android TV devices.

### Button Mapping

| Remote Button | Key Code |
|--------------|---------|
| Left         | `KEY_LEFT_ARROW` |
| Right        | `KEY_RIGHT_ARROW` |
| Up           | `KEY_UP_ARROW` |
| Down         | `KEY_DOWN_ARROW` |
| Enter        | `KEY_RETURN` *(long press opens main menu on Mi Box)* |
| Back         | `KEY_MEDIA_WWW_BACK` |
| Home         | `KEY_MEDIA_WWW_HOME` |
| Volume Up    | `KEY_MEDIA_VOLUME_UP` |
| Volume Down  | `KEY_MEDIA_VOLUME_DOWN` |
