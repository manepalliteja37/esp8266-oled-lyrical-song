# 🎵 How to Add a New Song

This guide walks you through creating a **new song folder** with ready-to-upload code, timing reference, and clear documentation. No advanced coding required — just copy, edit, and test!

⏱️ **Time to complete:** 10–20 minutes  
🎯 **Difficulty:** ⭐ Beginner

---

## ✅ Before You Start
- [ ] You have a working ESP8266 + OLED setup
- [ ] You've successfully run the `dracula` demo
- [ ] Arduino IDE (or PlatformIO) is installed
- [ ] You have your lyrics ready (with approximate timing in seconds)

---

## 📦 Step 1: Copy the Template Folder

Every song needs its own folder. Start by copying the template:

### Option A: Using Terminal / Git Bash
```bash
cp -r songs/your-song-name/ songs/my-new-song/
```

### Option B: Manual Copy (Windows/Mac)
1. Open the `songs/` folder in your file explorer
2. Right-click `your-song-name` → `Copy`
3. Paste in the same folder → Rename to your song (e.g., `midnight-drive`)
4. Your new path should be: `songs/midnight-drive/`

> 💡 **Naming Rule:** Use lowercase, hyphens for spaces (kebab-case). Example: `neon-dreams`, `telugu-beat-01`

---

## 📝 Step 2: Edit `lyrics.txt` (Timing Reference)

This file is your **human-readable song map**. Edit it first before touching code.

### Format Explained
```txt
delay_ms | duration_ms | word | effect | text_size
```
| Column | What It Means | Example |
|--------|---------------|---------|
| `delay_ms` | Wait time **after** the previous word finishes | `0` (no wait), `200` (pause 0.2s) |
| `duration_ms` | How long the word stays visible | `300` (0.3s), `1000` (1s) |
| `word` | Exact text to display | `"hello"`, `"నమస్కారం"` |
| `effect` | Visual effect | `NONE`, `POP`, `SHAKE`, `INVERT`, `GLITCH`, `ZOOM_IN` |
| `text_size` | Font size | `1` (small), `2` (medium), `3` (large) |

### ✍️ Example Entry
```txt
0     | 400  | Hello   | POP    | 2
100   | 600  | World!  | SHAKE  | 3
```

> 🧮 **Timing Tip:** 1000ms = 1 second. Start by writing lyrics with seconds, then multiply by 1000.  
> Example: 0.3s → `300`, 1.5s → `1500`

---

## 💻 Step 3: Update `src/main.ino`

Open `songs/your-song-name/src/main.ino` in Arduino IDE.

### 1️⃣ Find the Lyrics Array
Look for:
```cpp
Lyric lyrics[] = {
  // ... existing dracula lyrics ...
};
```

### 2️⃣ Replace with Your Lyrics
Convert your `lyrics.txt` entries into C++ format:
```cpp
Lyric lyrics[] = {
  // Phrase 1
  { 0, 400, "Hello",   EFFECT_POP,   2, 0 },
  { 100, 600, "World!", EFFECT_SHAKE, 3, 0 },
  // Add more lines...
};
const int numLyrics = sizeof(lyrics) / sizeof(Lyric);
```

### 3️⃣ Update Song Info (Optional but Recommended)
Change the top comments:
```cpp
// 🎵 Song: My New Song
// ⏱ Duration: ~45 seconds
// 📝 Created by: YourName
```

> ✅ **Auto-Calculation Note:** The code automatically calculates absolute start times in `setup()`. You **don't** need to change `calculatedStartTime` — leave it as `0`.

---

## 📄 Step 4: Update `README.md` & `wiring.md`

These files help others understand your song.

### In `README.md`:
- Change title: `# 🎶 My New Song`
- Update duration, difficulty, effects used
- Replace effect timeline table with your song's timeline
- Add a short description or mood/vibe note

### In `wiring.md`:
- If wiring is the same as default, leave it as-is
- If you use extra hardware (buttons, LEDs, SD card), update the wiring table and add a diagram note

---

## 🧪 Step 5: Test on Hardware

1. Connect ESP8266 + OLED
2. Open `songs/your-song-name/src/main.ino`
3. Select correct board & port
4. Click **Upload** ✅
5. Watch the sequence run

### 🔍 What to Check:
- ✅ Do words appear at the right time?
- ✅ Are effects triggering correctly?
- ✅ Is text readable (not cut off)?
- ✅ Does the background tunnel/EQ look smooth?

> 🛑 **Fix Timing?** Adjust `delay_ms` and `duration_ms` in both `lyrics.txt` and `main.ino`. Re-upload. Small changes (±100ms) make a big difference!

---

## 📤 Step 6: Share Your Song (Optional)

Love what you made? Share it with the community!

1. Commit your changes:
   ```bash
   git add songs/your-song-name/
   git commit -m "feat: add 'my-new-song' lyrical demo"
   git push
   ```
2. Open a Pull Request on GitHub
3. Include:
   - 🎵 Song name & vibe/mood
   - ⏱ Duration
   - 🎬 Short demo video (highly recommended!)
   - 📝 Any special notes (e.g., "Works best at night", "Telugu lyrics included")

📘 See full PR guidelines: [`CONTRIBUTING.md`](../CONTRIBUTING.md)

---

## 💡 Pro Tips for Great-Looking Songs

| Tip | Why It Matters |
|-----|----------------|
| Keep words short | Long words get cut off on 128px width |
| Use `EFFECT_NONE` for verses | Saves processing power, keeps focus on lyrics |
| Reserve `ZOOM_IN`/`INVERT` for drops | Creates impact without overwhelming the eye |
| Leave 200–500ms gaps between phrases | Gives the viewer time to breathe |
| Test with `delay(10)` in `loop()` if too fast | Slows animation for debugging |

---

## 🆨 Troubleshooting

| Problem | Fix |
|---------|-----|
| Text is cut off / too wide | Reduce `text_size` to 1 or 2, or shorten the word |
| Effects trigger at wrong time | Check `delay_ms` adds up correctly. The code calculates start times automatically. |
| Screen flickers / laggy | Reduce `NUM_BARS` to 12 or `NUM_CIRCLES` to 5 in `main.ino` |
| Song loops too quickly | Increase `TOTAL_LOOP_TIME` buffer in `setup()` (currently `+ 3000`) |

---

## 📚 Next Steps
- [📖 Understand the Code Structure](code-basics.md)
- [🎨 Add Custom Effects](effects-guide.md)
- [🤝 Contribute to the Repo](../CONTRIBUTING.md)

🎉 **You just made a song run on a microchip!** Keep experimenting, and share your creation. 💙