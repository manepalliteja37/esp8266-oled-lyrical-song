# 🎓 Lesson 1: Your First Upload (Beginner Friendly)

## 🎯 Goal
Get the project running on your ESP8266 in under 10 minutes.

## ✅ Before You Start
- [ ] Arduino IDE installed
- [ ] ESP8266 board support added (see README)
- [ ] Libraries installed: `Adafruit SSD1306`, `Adafruit GFX`
- [ ] Wiring done (VCC, GND, D1→SCL, D2→SDA)

## 🚀 Step-by-Step
1. Open Arduino IDE
2. Go to `File → Open → src/main.ino`
3. Select your board:  
   `Tools → Board → NodeMCU 1.0 (ESP-12E Module)`
4. Select your port:  
   `Tools → Port → /dev/ttyUSB0` (Linux/Mac) or `COM3` (Windows)
5. Click the **→ Upload** button (or press Ctrl+U)
6. Watch the bottom bar: "Done uploading." ✅
7. Look at your OLED — lyrics should start!

## 🔍 What to Expect
- Screen lights up
- Tunnel animation begins
- First word "The" appears after 1 second
- Effects trigger on words like **BLUE**, **BIZARRE**, **DRACULA**

## 🧪 Try This!
Change one word in the code:
```cpp
// Find this line:
{ 0, 300, "morning", EFFECT_POP, 2, 0 },

// Change "morning" to your name:
{ 0, 300, "Alex", EFFECT_POP, 2, 0 },