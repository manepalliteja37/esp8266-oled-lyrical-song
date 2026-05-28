---

## ❓ Frequently Asked Questions (FAQ)

<details>
<summary><strong>Q: Do I need a speaker or microphone for this project?</strong></summary>

**A:** No! 🎧 This project uses **pre-timed lyrics** — the ESP8266 runs everything alone. No audio input, no real-time processing. Just upload and watch!

</details>

<details>
<summary><strong>Q: Can I use a different OLED display (128x32 or SPI version)?</strong></summary>

**A:** This code is built for **I2C SSD1306 128x64** displays. Other displays need code changes:
- 128x32: Change `SCREEN_HEIGHT` to 32 and adjust text positioning
- SPI version: Replace `&Wire` with SPI pins in `Adafruit_SSD1306` constructor  
See [`docs/troubleshooting.md`](docs/troubleshooting.md) for detailed steps.

</details>


<details>
<summary><strong>Q: How do I change the song speed or timing?</strong></summary>

A: Adjust these values in lyrics.txt or main.ino:
delayBeforeMs: Wait time before the word appears (in milliseconds)
durationMs: How long the word stays on screen
Example: Change { 0, 300, "fast", ... } to { 0, 600, "slow", ... } to make it display twice as long.
</details>

<details>
<summary><strong>Q: Can I add real-time audio visualization (microphone input)?</strong></summary>

A: Yes! That's an advanced feature for future versions. Start with pre-timed lyrics first to learn the basics. Later, you can explore:
MAX9814 microphone module
FFT (Fast Fourier Transform) libraries
Real-time EQ bar updates
We'd love your help building this! Open an issue to discuss. 🎤
</details>

<details>
<summary><strong>Q: Is Telugu or other language support possible?</strong></summary>

A: Absolutely! 🌍 The OLED library supports UTF-8 encoding. To add Telugu lyrics:
Save your .ino and .txt files in UTF-8 encoding
Use Telugu text in the word field: { 0, 400, "నమస్కారం", ... }
For full script support, add a custom Telugu font (see docs/code-basics.md)
We're actively working on making regional language support even easier!
</details>

<details>
<summary><strong>Q: The screen is blank / code won't upload — help!</strong></summary>

A: Don't worry — this is common! Check:
🔌 Wiring: VCC→3.3V, GND→GND, D1→SCL, D2→SDA
🔋 Power: Use a good USB cable (some only charge, no data)
📦 Libraries: Install Adafruit SSD1306 + Adafruit GFX
🎯 Board: Select NodeMCU 1.0 (ESP-12E Module)
🔗 Port: Choose the correct COM/USB port
Still stuck? See docs/troubleshooting.md or open an issue! 🙋
</details>

---