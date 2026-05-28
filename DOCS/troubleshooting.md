## 🆘 `docs/troubleshooting.md` (Fix Common Problems)
```markdown
# 🆘 Troubleshooting Guide

## ❌ Screen is Blank / Black
| Possible Cause | Fix |
|----------------|-----|
| Wrong voltage | Use **3.3V**, not 5V |
| Wrong I2C address | Try changing `0x3C` to `0x3D` in `display.begin()` |
| Loose wires | Re-check all 4 connections |
| Library not installed | Install `Adafruit SSD1306` + `Adafruit GFX` |

## ❌ Upload Fails / ESP8266 Not Detected
| Possible Cause | Fix |
|----------------|-----|
| Wrong board selected | `Tools → Board → NodeMCU 1.0 (ESP-12E)` |
| Wrong port | `Tools → Port → Select the COM/USB port` |
| Driver missing | Install [CH340 drivers](https://www.wemos.cc/en/latest/ch340_driver.html) (for clones) |
| Boot mode issue | Hold FLASH button while pressing RESET, then upload |

## ❌ Lyrics Are Out of Sync / Wrong Timing
- Timing is in **milliseconds** (1000ms = 1 second)
- Adjust `delayBeforeMs` (wait before word) or `durationMs` (how long word shows)
- Test with short phrases first

## ❌ Effects Look "Broken" or Too Fast
- OLEDs are small! Effects are simplified for performance
- Try reducing `NUM_BARS` or `NUM_CIRCLES` if animation is choppy
- Add `delay(10)` in `loop()` to slow things down for testing

## ❓ Still Stuck?
1. Check the [FAQ](faq.md)
2. Search [GitHub Issues](../../issues)
3. Open a new issue with:
   - Photo of your wiring
   - Error message (if any)
   - ESP8266 board model
   - OLED model (if known)

> 💬 **Community Tip**: Join the [ESP8266 Community Forum](https://www.esp8266.com/) for fast help!