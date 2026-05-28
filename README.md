# 🎵 ESP8266 OLED Lyrical Songs Collection

> **Display Animated Lyrics on Tiny OLED Screens — Multiple Songs, One Repo**  
> 🎶 Pick a song → Upload → Watch lyrics dance on your OLED!

---

## ✨ What Is This Repo?

A **beginner-friendly collection** of lyrical song projects for **ESP8266 + SSD1306 OLED** displays. Each song lives in its own folder with ready-to-upload code, wiring guide, and customization tips.

🔹 **No audio input needed** — lyrics are pre-timed  
🔹 **Cool visual effects**: Pop, Shake, Glitch, Zoom, Shockwave, Invert  
🔹 **Easy to swap songs** or create your own  
🔹 **Perfect for learning** embedded coding + creative displays  
🔹 **Telugu-friendly** — add lyrics in your language!

---

## 📁 Repository Structure

```
esp8266-oled-lyrics-collection/
│
├── 📁 songs/                    ← All songs live here
│   ├── 📁 dracula/             ← "DRACULA" lyrical demo (your first song!)
│   │   ├── src/main.ino        ← Arduino code for this song
│   │   ├── lyrics.txt          ← Plain text lyrics + timing reference
│   │   ├── preview/gif         ← Song Gif
│   │   └── README.md           ← Song-specific tips & effects guide
│   │
│   ├── 📁 dropdead/            ← Another song (add your own!)
│   │   ├── src/main.ino
│   │   ├── lyrics.txt
|   |   ├── preview/gif         ← Song Gif
│   │   └── README.md
│   │   
│   │
│   ├── 📁 your-song-name/      ← Template folder to copy for new songs
│   │   ├── src/
│   │   ├── lyrics.txt
|   |   ├── Preview/
│   │   └── README.md
│   │
│   └── 📄 SONGS_INDEX.md       ← List of all available songs + difficulty
│
├── 📁 docs/                     ← Shared documentation (all songs)
│   ├── getting-started.md      ← First-time setup guide
│   ├── code-explained.md          ← Understand the core code structure
│   ├── effects-guide.md        ← What each visual effect does
│   ├── troubleshooting.md      ← Fix common problems
│   ├── add-new-song.md         ← Step-by-step: create your own song folder
|   ├── wiring-guide.md
│   └── faq.md                  ← Frequently asked questions
│
├── 📁 assets/                   ← Shared images, diagrams, demos
│   ├── wiring-diagram.png
│   ├── effects-preview.gif
│   └── demo-videos/
│
├── 📄 README.md                 ← You are here! (Main repo guide)
├── 📄 LICENSE                   ← MIT License — use freely!
├── 📄 platform.md               ← For PlatfromIO IDE users
└── 📄 CONTRIBUTING.md           ← How to share your songs with others
```

---

## 🚀 Quick Start: Run Your First Song (DRACULA)

### 1️⃣ What You Need

| Item | Details |
|------|---------|
| **ESP8266** | NodeMCU, WeMos D1 Mini, or any ESP-12E variant |
| **OLED** | SSD1306, 0.96", I2C, 128x64 pixels |
| **Wires** | 4 jumper wires (VCC, GND, SCL, SDA) |
| **USB Cable** | For power + programming |
| **Computer** | With Arduino IDE installed |

### 2️⃣ Wiring (Same for All Songs)

```
   ESP8266          SSD1306 OLED
   ─────────        ────────────
   [VCC]  ───────→  [VCC]   (3.3V power)
   [GND]  ───────→  [GND]   (ground)
   [D1]   ───────→  [SCL]   (clock pin, GPIO5)
   [D2]   ───────→  [SDA]   (data pin, GPIO4)
```

> ⚠️ **Important**: Use **3.3V only** — 5V can damage your OLED!

### 3️⃣ Upload the "DRACULA" Song

```bash
# Option A: Clone this repo (if you have Git)
git clone https://github.com/yourname/esp8266-oled-lyrics-collection.git

# Option B: Download as ZIP from GitHub → Extract folder
```

**In Arduino IDE:**
1. `File → Open → esp8266-oled-lyrics-collection/songs/dracula/src/main.ino`
2. Install libraries if prompted (`Sketch → Include Library → Manage Libraries`):
   - `Adafruit SSD1306` by Adafruit
   - `Adafruit GFX Library` by Adafruit
3. Select your board:  
   `Tools → Board → NodeMCU 1.0 (ESP-12E Module)`
4. Select your port:  
   `Tools → Port → COM3` (Windows) or `/dev/ttyUSB0` (Mac/Linux)
5. Click **Upload** ✅ (arrow button or Ctrl+U)

### 4️⃣ Watch It Run! 🎉

- ✅ Screen lights up with tunnel animation
- ✅ EQ bars bounce at the bottom like a music visualizer
- ✅ Lyrics appear with timed effects:
  - `BLUE` → screen inverts (black↔white)
  - `BIZARRE` → glitch effect with random lines
  - `DRACULA` → zoom in + shockwave ripple!

---

## 🎼 Available Songs

| Song Folder | Difficulty | Duration | Special Effects | Preview |
|-------------|------------|----------|-----------------|---------|
| [`songs/dracula/`](songs/dracula/) | ⭐ Beginner | ~30 sec | Invert, Glitch, Zoom, Shockwave | [Demo GIF](assets/dracula-demo.gif) |
| [`songs/dropdead/`](songs/dropdead/) | ⭐⭐ Intermediate | ~45 sec | Shake, Pop, Tunnel Speed Boost | [Demo GIF](assets/dropdead-demo.gif) |
| [`songs/your-song-name/`](songs/your-song-name/) | 🛠️ Template | — | Copy & customize! | — |

👉 **See full list with details**: [`songs/SONGS_INDEX.md`](songs/SONGS_INDEX.md)

---

## 🔁 How to Switch Songs

You only need to change **ONE folder** — no code rewriting needed!

```bash
# Want to run "dropdead" instead of "dracula"?
# Just open this file in Arduino IDE:
esp8266-oled-lyrics-collection/songs/dropdead/src/main.ino
# → Click Upload → Done! 🎵
```

> 💡 **Pro Tip**: Keep only one `src/main.ino` folder open in Arduino IDE at a time to avoid confusion.

---

## ✍️ How to Add Your Own Song

Creating a new lyrical song is easy! Follow these 4 simple steps:

### Step 1: Copy the Template Folder

```bash
# In terminal (Mac/Linux) or Git Bash (Windows):
cp -r songs/your-song-name/ songs/my-awesome-song/

# Or manually: Copy the entire "your-song-name" folder and rename it
```

### Step 2: Edit `lyrics.txt`

Write your lyrics with timing (all values in **milliseconds**):

```txt
# FORMAT: delay_ms | duration_ms | word | effect | text_size
# ---------------------------------------------------------
# delay_ms    = wait time before this word appears
# duration_ms = how long the word stays on screen
# word        = the text to display (use quotes for spaces)
# effect      = NONE, POP, SHAKE, INVERT, GLITCH, ZOOM_IN
# text_size   = 1 (small), 2 (medium), 3 (large)

# Example: Telugu + English mix 🌍
0     | 300  | Hello  | NONE   | 2
0     | 300  | ప్రపంచం | POP    | 2
200   | 800  | WOW!   | ZOOM   | 3
```

✅ **Supported Effects**:
| Effect | What It Does | Best For |
|--------|--------------|----------|
| `NONE` | Plain text, clean look | Normal words, verses |
| `POP` | Word briefly grows larger | Emphasis: "YES!", "NOW" |
| `SHAKE` | Text jitters like earthquake | Dramatic moments |
| `INVERT` | Screen colors flip (black↔white) | Surprise words: "BLUE" |
| `GLITCH` | Random lines + jitter + flicker | Edgy, chaotic vibes |
| `ZOOM_IN` | Word starts tiny → zooms to full size | Big drops: "DRACULA!" |

### Step 3: Update `src/main.ino`

1. Open `songs/my-awesome-song/src/main.ino`
2. Find the `Lyric lyrics[] = { ... };` array
3. Replace the example lyrics with your new entries from `lyrics.txt`
4. (Optional) Change the song name in the top comments
5. (Optional) Adjust tunnel/EQ speed in `drawTunnel()` and `drawEQ()` for your song's vibe

### Step 4: Test & Share!

```bash
# Upload to your ESP8266
# Record a short video of it running 🎥
# Optional: Share with the community!
```

📚 **Full step-by-step tutorial**: [`docs/add-new-song.md`](docs/add-new-song.md)

---

## 📚 Documentation Hub

| Guide | What You'll Learn | Link |
|-------|-------------------|------|
| **Getting Started** | First-time setup: Arduino IDE, drivers, libraries | [`docs/getting-started.md`](docs/getting-started.md) |
| **Code Explained** | Understand the core code — no experience needed | [`docs/code-basics.md`](docs/code-explained.md) |
| **Effects Guide** | What each visual effect does + when to use it | [`docs/effects-guide.md`](docs/effects-guide.md) |
| **Troubleshooting** | Fix blank screen, upload errors, timing issues | [`docs/troubleshooting.md`](docs/troubleshooting.md) |
| **Add New Song** | Step-by-step: create & share your own song | [`docs/add-new-song.md`](docs/add-new-song.md) |
| **Wiring Guide** | Step-by-step: Wiring for circuit | [`docs/wiring-guide.md`](docs/wiring-guide.md) |
| **FAQ** | Quick answers to common questions | [`docs/faq.md`](docs/faq.md) |

---

## 🎨 Visual Effects Reference (With Examples)

```cpp
// EFFECT_NONE - Clean, simple text
{ 0, 300, "hello", EFFECT_NONE, 2, 0 }
// → Displays: hello

// EFFECT_POP - Word briefly enlarges (like a bounce)
{ 0, 300, "POP!", EFFECT_POP, 2, 0 }
// → Displays: POP! (briefly bigger) 💥

// EFFECT_SHAKE - Text jitters like an earthquake
{ 0, 500, "SHAKE", EFFECT_SHAKE, 2, 0 }
// → Displays: S~H~A~K~E (with random movement) 〰️

// EFFECT_INVERT - Screen colors flip (black↔white)
{ 0, 400, "INVERT", EFFECT_INVERT, 2, 0 }
// → Entire screen inverts for dramatic impact ⚡

// EFFECT_GLITCH - Random lines + jitter + flicker
{ 0, 600, "GLITCH", EFFECT_GLITCH, 2, 0 }
// → Digital distortion effect for edgy moments 📺

// EFFECT_ZOOM_IN - Word starts tiny → zooms to full size
{ 0, 800, "ZOOM", EFFECT_ZOOM_IN, 3, 0 }
// → Starts small, expands dramatically 🔍→🔭
```

🎬 **See all effects in action**: [`assets/effects-preview.gif`](assets/effects-preview.gif)

---

## 🌍 Telugu & Regional Language Support

Yes! You can display lyrics in **Telugu, Hindi, Tamil, or any UTF-8 language**.

### How to Add Telugu Lyrics:

1. **Save your file in UTF-8 encoding**:
   - Arduino IDE: `File → Preferences → Show verbose output → Compilation`
   - Or use VS Code / Notepad++ and save as "UTF-8 without BOM"

2. **Add Telugu text in `lyrics.txt`**:
   ```txt
   0     | 400  | నమస్కారం | POP    | 2
   0     | 300  | తెలుగు   | NONE   | 2
   200   | 600  | అద్భుతం! | ZOOM   | 3
   ```

3. **Update `main.ino`** with your Telugu lyrics array

4. **Upload and enjoy!** 🎉

> 💡 **Note**: The default OLED font supports basic Latin + some extended characters. For full Telugu script support, you may need to add a custom font (see [`docs/code-basics.md`](docs/code-basics.md) for advanced font setup).
---

---
## 📄 License

This project is open-source under the **MIT License**.

✅ **You can**:
- Use it for personal projects
- Share it with friends or students
- Teach with it in workshops
- Remix, modify, and improve it
- Use it in commercial projects

✅ **Just remember to**:
- Include the original license file
- Give credit to the original creators
- Share your improvements back if you can! 🙏
---

---
## 💙 Made With ❤️ For Learners & Creators

> 🎓 **Learn electronics** • 🎵 **Express through code** • 🌐 **Share with the world**

This project was created by **Telugu Mad Thinker** to make embedded coding fun, visual, and accessible — especially for Telugu-speaking learners and electronics enthusiasts.

## 🌟 Join Our Community

- 💼 LinkedIn: [Brahma Teja](https://www.linkedin.com/in/brahma-teja-a5a306174/)
- 📺 YouTube: [Telugu Mad Thinker](https://www.youtube.com/@telugumadthinker)
- 📸 Instagram: [Telugu Mad Thinker](https://www.instagram.com/telugumadthinker/)
- 🐦 Twitter/X: [@TejaMane37](https://x.com/TejaMane37)
- 💻 GitHub: [manepalliteja37](https://github.com/manepalliteja37)
- 📧 Email: manepalliteja37@gmail.com

### 🙏 Thank You To:
- Adafruit for amazing OLED libraries
- ESP8266 community for open-source firmware
- You — for learning, creating, and sharing! 🙌
---
---

> 🔗 **Ready to start?**  
> → [🚀 Quick Start Guide](#-quick-start-run-your-first-song-dracula)  
> → [🎵 Try the DRACULA Demo](songs/dracula/)  
> → [✍️ Create Your First Song](docs/add-new-song.md)  
> → [❓ Need Help? Check FAQ](#-frequently-asked-questions-faq)

*Questions, ideas, or found a bug?*  
👉 [Open an Issue](https://github.com/yourname/esp8266-oled-lyrics-collection/issues) — we're happy to help! 🙋‍♂️✨

---

<p align="center">
  <sub>Built with ESP8266 • SSD1306 • Arduino • ❤️ • Telugu Pride</sub><br>
  <sub>© 2026 Telugu Mad Thinker — Learn • Create • Share</sub>
</p>
```