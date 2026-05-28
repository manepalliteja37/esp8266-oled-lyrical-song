# 🔌 Wiring Guide: ESP8266 + SSD1306 OLED

## 📋 Parts Checklist
✅ ESP8266 board (NodeMCU, WeMos D1 Mini, etc.)  
✅ SSD1306 OLED display (0.96", I2C, 128x64)  
✅ 4 jumper wires  
✅ USB cable for power  

## 🔗 Connection Diagram
ESP8266 SSD1306 OLED
───────── ────────────
[VCC] ───────→ [VCC] (3.3V power)
[GND] ───────→ [GND] (ground)
[D1] ───────→ [SCL] (clock pin, GPIO5)
[D2] ───────→ [SDA] (data pin, GPIO4)


## 🖼️ Visual Reference
*(Later: add a Fritzing diagram or photo here)*

## ⚠️ Important Notes
- **Use 3.3V, not 5V** — Most OLEDs can be damaged by 5V.
- **I2C Address**: This code assumes `0x3C`. If your screen doesn't work, try `0x3D` in `display.begin(SSD1306_SWITCHCAPVCC, 0x3D)`.
- **Pull-up resistors**: Most OLED modules have them built-in. If your display is unstable, add 4.7kΩ resistors between SCL/SDA and VCC.

## 🔍 Testing Your Connection
1. Upload a simple "Hello World" OLED sketch first
2. If you see text → wiring is good!
3. If screen is blank → double-check VCC/GND and I2C address

> 💡 **Pro Tip**: Use the `I2C Scanner` sketch (search online) to find your OLED's address if unsure.