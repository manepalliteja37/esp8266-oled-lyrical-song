Here are the 4 files, formatted and ready to copy-paste directly into your repository. Each uses simple English, clear structure, and follows your project's code logic.

---

## 📄 `CONTRIBUTING.md`

```markdown
# 🤝 How to Contribute

Thank you for wanting to improve this project! Whether you're fixing a bug, adding a new song, or creating a cool visual effect — your help is welcome.

---

## 🧭 Quick Contribution Paths

| You Want To... | Where to Start |
|----------------|----------------|
| Add a new song | `songs/your-song-name/` (use the template) |
| Create a visual effect | `docs/effects-guide.md` |
| Improve docs or fix typos | `docs/` folder |
| Report a bug or crash | Open an Issue with photos/logs |

---

## 🛠️ Step-by-Step: Submit a Change

### 1️⃣ Fork & Clone
```bash
git clone https://github.com/YOUR-USERNAME/esp8266-oled-lyrics-collection.git
cd esp8266-oled-lyrics-collection
```

### 2️⃣ Create a Branch
```bash
git checkout -b feat/add-telugu-song
# or: git checkout -b fix/eq-bar-overflow
```

### 3️⃣ Make Your Changes
- ✅ Keep code under 80-100 lines per function
- ✅ Add comments for non-obvious logic
- ✅ Test on real hardware (ESP8266 + OLED)
- ✅ Update docs if you change behavior

### 4️⃣ Commit & Push
```bash
git add .
git commit -m "feat: add 'Nuvve Nuvve' song with Telugu lyrics"
git push origin feat/add-telugu-song
```

### 5️⃣ Open a Pull Request
- Title: Clear & descriptive (`feat: add dropdead song`, `fix: shockwave radius overflow`)
- Description: What you changed, why, and how to test it
- Attach: Short video or photo if adding visual changes

---

## 📐 Code & Folder Standards

### 📁 Song Folder Structure
Every song **must** follow this layout:
```
songs/[song-name]/
├── src/main.ino          ← Arduino sketch
├── lyrics.txt            ← Timing reference (human-readable)
├── wiring.md             ← Hardware notes (copy from template if same)
└── README.md             ← Song-specific guide
```

### 🧠 Code Style
- Use `snake_case` for variables: `lyricDelayMs`, not `lD`
- Keep `loop()` under 50 lines where possible
- Add `//` comments before math/GFX tricks
- Use `const` or `#define` for magic numbers (e.g., `#define MAX_BARS 16`)

### 📱 Hardware Testing
- Test on **NodeMCU v1/v3** or **WeMos D1 Mini**
- Use **I2C SSD1306 128x64** (0.96")
- Verify 3.3V power (not 5V)
- Check for screen flicker or slow refresh (>60ms per frame)

---

## 🐛 Reporting Bugs
Please include:
1. 📸 Photo of wiring (if hardware-related)
2. 💻 Board model & OLED type
3. 📋 Exact error message or behavior
4. 🔁 Steps to reproduce
5. 📜 Code snippet (if modified)

---

## 🌍 Community Values
- 🙏 Be kind & patient — everyone starts somewhere
- 📖 Explain things simply — avoid heavy jargon
- 🧪 Test before pushing — broken builds block others
- 🎉 Celebrate small wins — first song? First effect? Awesome!

Questions? Open an issue or comment on a PR. We reply within 48 hours! 🚀

---