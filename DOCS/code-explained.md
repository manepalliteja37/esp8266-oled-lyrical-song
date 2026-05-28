# 🧠 Code Explained: Simple & Clear

This document breaks down `src/main.ino` into easy-to-understand pieces.

---

## 📦 Libraries (The "Tools" We Use)
```cpp
#include <Wire.h>              // For I2C communication (OLED talks via I2C)
#include <Adafruit_GFX.h>      // Core graphics library for displays
#include <Adafruit_SSD1306.h>  // Specific driver for SSD1306 OLED
#include <math.h>              // For math functions (used in tunnel animation)
```
## 🎨 Display Setup
```cpp
#define SCREEN_WIDTH 128
#define SCREEN_HEIGHT 64
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);
```
→ Creates a display object to control the OLED
→ &Wire tells it to use I2C (the D1/D2 pins)

## 🎭 Lyric Effects (The "Cool Stuff")
```cpp
enum Effect {
  EFFECT_NONE,    // Normal text
  EFFECT_POP,     // Word briefly gets bigger
  EFFECT_SHAKE,   // Word jitters like an earthquake
  EFFECT_INVERT,  // Screen colors flip (black↔white)
  EFFECT_GLITCH,  // Random lines + jitter for "broken" look
  EFFECT_ZOOM_IN  // Word starts tiny, zooms to full size
};
```
→ Each lyric in your song can have one of these effects!

## 📝 How Lyrics Are Stored
```cpp
struct Lyric {
  unsigned long delayBeforeMs;   // Wait time before this word appears
  unsigned long durationMs;      // How long the word stays on screen
  const char* word;              // The actual text (e.g., "BLUE")
  Effect effect;                 // Which visual effect to use
  uint8_t size;                  // Text size: 1=small, 2=medium, 3=large
  unsigned long calculatedStartTime; // Auto-calculated (don't edit)
};
```
## Example Lyric Entry:
```cpp
{ 100, 500, "BLUE", EFFECT_INVERT, 3, 0 }
```
→ Wait 100ms, show "BLUE" for 500ms, invert screen colors, use size 3 (large).

## 🎵 The Song Timeline
All lyrics are stored in an array:
```cpp
Lyric lyrics[] = {
  { 0, 300, "The", EFFECT_NONE, 2, 0 },
  { 0, 300, "morning", EFFECT_POP, 2, 0 },
  // ... more lyrics ...
  { 100, 2500, "DRACULA", EFFECT_ZOOM_IN, 3, 0 } // THE DROP! 🎉
};
```
→The code auto-calculates when each word should appear
→Change words, timing, or effects by editing this list


## 🌀 Background Animations (3 Layers)
Tunnel: Concentric circles + radiating lines that move toward you
EQ Bars: 16 bars at the bottom that bounce like an audio visualizer
Shockwave: A ripple that expands when special lyrics appear
These run in the background while lyrics display on top.

## 🔄 Main Loop Logic (Simplified)
```cpp
void loop() {
  1. Check current time in the song
  2. Find which lyric (if any) should be showing now
  3. Draw background (tunnel + EQ + shockwave)
  4. Draw lyric text on top (with effects applied)
  5. Send everything to the OLED screen
  6. Repeat ~60 times per second
}
```

## 🎯 Key Functions
| Function      | What It Does                          |
|---------------|---------------------------------------|
| drawTunnel()  | Draws the moving tunnel background    |
| drawEQ()      | Draws bouncing bars at the bottom     |
| drawShockwave() | Draws ripple effect on special words |
| loop()        | Main function that runs continuously  |
💡 Beginner Tip: Don't worry about understanding every line yet. Start by changing one lyric word, then re-upload. Small steps! 🚶‍♂️→🏃