## 📄 songs/dracula/README.md`

# 🧛 DRACULA — Lyrical OLED Demo

A cinematic, pre-timed lyrical sequence designed for **ESP8266 + SSD1306 OLED**. Features a tunnel background, bouncing EQ bars, and 6 visual effects synced to word timing.

⏱ **Duration**: ~30 seconds  
🎯 **Difficulty**: ⭐ Beginner (copy, upload, watch)  
🎨 **Effects Used**: Pop, Invert, Glitch, Shake, Zoom, Shockwave

---

## 🚀 Quick Run

1. Open `src/main.ino` in Arduino IDE
2. Select board: `Tools → Board → NodeMCU 1.0 (ESP-12E Module)`
3. Select port & click **Upload**
4. Watch the lyrics animate!

> 🔌 Wiring is the same for all songs: `VCC→3.3V`, `GND→GND`, `D1→SCL`, `D2→SDA`

---

## 🎬 Effect Timeline

| Time | Word | Effect | What Happens |
|------|------|--------|--------------|
| 0.0s | The | None | Clean start |
| 0.3s | morning | Pop | Brief size bump |
| 1.5s | BLUE | Invert | Screen flips black↔white |
| 2.4s | BIZARRE | Glitch | Random lines + jitter |
| 3.8s | night | Pop | Emphasis bump |
| 6.5s | ARE | Shake | Earthquake jitter + shockwave |
| 7.1s | shadows, | Shake | Continued tension |
| 9.8s | STAR | Invert | Dramatic color flip |
| 12.3s | Daylight | Pop | Warm build-up |
| 14.0s | DRACULA | Zoom + Shockwave | Starts tiny → expands + ripple effect (2.5s hold) |

---

## 🛠️ Customize This Song

### Change Timing
Open `src/main.ino` → find `Lyric lyrics[] = { ... };`  
Edit the first two numbers:
```cpp
// { delayBeforeMs, durationMs, "word", effect, size }
{ 0, 300, "The", EFFECT_NONE, 2, 0 }  // ← Change 300 → 500 to hold longer
```

### Change Effects
Replace the effect enum:
```cpp
EFFECT_POP → EFFECT_SHAKE  // Makes "morning" jitter instead
```

### Change Speed of Background
In `drawTunnel()`, adjust:
```cpp
float speed = 1.0;  // ↑ faster, ↓ slower
```

---

## 📜 Lyrics Reference
See exact timing & text in: [`lyrics.txt`](lyrics.txt)

---

## 🎓 Learning Tips
- Try changing `DRACULA` duration from `2500` to `4000` → see how long it stays on screen
- Replace `EFFECT_ZOOM_IN` with `EFFECT_NONE` → notice how calm it feels
- Add `delay(20)` in `loop()` to slow everything down for debugging

---

## 🔗 More Help
- [Main Repo README](../../README.md)
- [Effects Guide](../../docs/effects-guide.md)
- [Troubleshooting](../../docs/troubleshooting.md)

🎵 *Made for learners, creators, and midnight coders.*
```