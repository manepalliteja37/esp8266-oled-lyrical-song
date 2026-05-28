## 📄 `docs/effects-guide.md`

```markdown
# 🎨 Visual Effects Guide

This guide explains the built-in effects, how they work, and how to add **new effects** using `math.h`, Arduino built-ins, and `Adafruit_GFX` shapes.

---

## 📦 Existing Effects (From Code)

| Effect | What It Does | Trigger Words Example |
|--------|--------------|------------------------|
| `EFFECT_NONE` | Plain text, clean background | Normal lyrics |
| `EFFECT_POP` | Word briefly grows +1 size | "morning", "feeling" |
| `EFFECT_SHAKE` | Random X/Y jitter | "ARE", "shadows," |
| `EFFECT_INVERT` | Screen flips black↔white | "BLUE", "STAR" |
| `EFFECT_GLITCH` | Random lines + offset + invert | "BIZARRE" |
| `EFFECT_ZOOM_IN` | Starts small → zooms + shakes | "DRACULA" |

---

## ➕ How to Add a New Effect (Step-by-Step)

### Step 1: Add to Enum
In `src/main.ino`, find:
```cpp
enum Effect {
  EFFECT_NONE = 0,
  EFFECT_POP,
  EFFECT_SHAKE,
  EFFECT_INVERT,
  EFFECT_GLITCH,
  EFFECT_ZOOM_IN,
  EFFECT_WAVE  // ← Add your new effect here
};
```

### Step 2: Add Logic in `loop()`
Find the effect application block and add:
```cpp
} else if (l.effect == EFFECT_WAVE) {
  // Example: wave text position using sin()
  offsetX = sin(progress * 2 * PI) * 6;
  offsetY = cos(progress * 3 * PI) * 3;
}
```

### Step 3: (Optional) Add Background Function
If your effect needs background drawing, create:
```cpp
void drawWaveBackground() {
  for (int x = 0; x < SCREEN_WIDTH; x += 4) {
    int y = SCREEN_HEIGHT/2 + sin(x * 0.1 + millis() * 0.01) * 10;
    display.drawPixel(x, y, WHITE);
  }
}
```
Call it in `loop()` before drawing lyrics.

---

## 🧮 New Effect Ideas (Copy-Paste Ready)

### 1️⃣ `EFFECT_WAVE` (Math: `sin()`/`cos()`)
Text bobs up/down smoothly.
```cpp
// Inside loop() effect switch:
offsetX = sin(progress * 4 * PI) * 5;
offsetY = cos(progress * 3 * PI) * 3;
```
💡 **Why it works**: `sin()` creates smooth oscillation. `progress` (0.0→1.0) maps to wave cycles.

---

### 2️⃣ `EFFECT_RAIN` (Arduino: `random()` + GFX `drawPixel`)
Falling white dots behind text.
```cpp
void drawRain() {
  for (int i = 0; i < 20; i++) {
    int rx = random(SCREEN_WIDTH);
    int ry = random(SCREEN_HEIGHT);
    display.drawPixel(rx, ry, WHITE);
  }
}
```
Call `drawRain()` before lyrics. Add `display.fillRect(0,0,SCREEN_WIDTH,SCREEN_HEIGHT,BLACK);` first to avoid trails.

---

### 3️⃣ `EFFECT_PULSE` (Math: `map()` + `cos()`)
Text size breathes in/out.
```cpp
int pulseSize = map(cos(progress * 4 * PI) * 100, -100, 100, 1, 4);
display.setTextSize(pulseSize);
```
💡 `map()` converts `-100→100` range to `1→4` text sizes.

---

### 4️⃣ `EFFECT_TRIANGLE_SCAN` (GFX Shapes)
Scanning triangle overlay.
```cpp
void drawScanTriangle() {
  int y = (millis() / 20) % SCREEN_HEIGHT;
  display.drawTriangle(0, y, SCREEN_WIDTH, y, SCREEN_WIDTH/2, y-15, WHITE);
}
```
Great for "drop" moments. Call before text.

---

### 5️⃣ `EFFECT_FADE_OUT` (GFX: `drawCircle` + `fillRect`)
Word slowly disappears by shrinking + transparency trick.
```cpp
// OLEDs don't support alpha, so we simulate fade:
int fadeSize = max(1, 3 - (int)(progress * 2));
display.setTextSize(fadeSize);
display.setTextColor((progress > 0.5) ? BLACK : WHITE);
```

---

## ⚠️ ESP8266 Performance Tips
- ✅ Use `int` instead of `float` when possible (ESP8266 handles floats slower)
- ✅ Limit `random()` calls per frame (max 30-50)
- ✅ Avoid nested loops inside `loop()`
- ✅ Use `display.display()` only **once** per loop
- ✅ Test frame rate: if text jitters, reduce `NUM_BARS` or `NUM_CIRCLES`

---

## 📐 Math & GFX Cheat Sheet

| Function | Use Case | Example |
|----------|----------|---------|
| `sin(x)`, `cos(x)` | Smooth movement, waves | `y = sin(millis() * 0.01) * 10` |
| `random(min, max)` | Glitch, particles, noise | `x = random(0, SCREEN_WIDTH)` |
| `map(val, inMin, inMax, outMin, outMax)` | Scale values | `size = map(progress, 0, 1, 1, 4)` |
| `display.drawPixel()` | Stars, rain, dots | `display.drawPixel(x, y, WHITE)` |
| `display.drawTriangle()` | Scanners, lasers | `display.drawTriangle(x1,y1, x2,y2, x3,y3, WHITE)` |
| `display.fillCircle()` | Pulses, shockwaves | `display.fillCircle(cx, cy, r, WHITE)` |

---

## 🛠️ Need Help Adding an Effect?
Open an issue with:
- Effect name & goal
- Reference video/GIF (if any)
- Code snippet you tried
We'll help you optimize it for ESP8266! 🙌
```