# XY Music Visualizer (Installable Web App)

A zero-backend, client-side music player and visualizer built on a 100% free architecture. Plays local audio files with synchronized lyrics floating amidst champagne gold stardust.

---

## 🏛️ Free Architecture

- **Audio Engine**: HTML5 Audio API (`<audio>` / `Audio` object with Media Session API for lock screen and notification controls).
- **Audio Visualizer**: Web Audio API (`AudioContext`, `createMediaElementSource`, `AnalyserNode` frequency binning) + Canvas 2D audio-reactive renderer.
- **Lyrics Database**: [LRCLIB](https://lrclib.net) (free, open, community-contributed synchronized lyrics API).
- **Synchronization**: Real-time LRC timestamp parser supporting standard `[mm:ss.xx]`, multiline stamps, and offset correction.
- **Installation**: Progressive Web App (PWA) with Service Worker offline caching and `manifest.webmanifest`.
- **Design & Theme**: Deep obsidian black (`#040404`), champagne gold accents (`#d8b96e`, `#f4e6be`), and subtle audio-reactive golden particles.

---

## 🎵 LRCLIB API Integration

The app natively integrates LRCLIB's endpoints:

1. **Full-text Query Search**:
   ```http
   GET https://lrclib.net/api/search?q=still+alive+portal
   ```
2. **Fetch Directly by LRCLIB ID**:
   ```http
   GET https://lrclib.net/api/get/3396226
   ```
3. **Exact Metadata Lookup**:
   ```http
   GET https://lrclib.net/api/get?artist_name=Borislav+Slavov&track_name=I+Want+to+Live&album_name=Baldur%27s+Gate+3+(Original+Game+Soundtrack)&duration=233
   ```

### Using Lyrics in the App:
- **Automatic Resolution**: Automatically queries LRCLIB using ID3 tags / file metadata (`get?` then fallback `search?`).
- **Interactive Search Modal**: Tap the **`LRCLIB`** button in the player or lyrics editor to search any song (`search?q=...`) or enter a numeric ID directly (`get/:id`).
- **Local Pairing**: Drop a `.mp3` and `.lrc` file together; they pair automatically.
- **Lyrics Editor**: Paste plain lyrics, stamp live playback times, shift ±0.5s, or auto-time.
- **Offline Caching**: Synced lyrics are saved into `localStorage`, working offline forever after first load.

---

## 📱 PWA & Offline Installation

- **Android**: Open in Chrome > Tap menu > **Install app** (or tap **Install app** in the home screen).
- **iOS / iPadOS**: Open in Safari > Tap **Share** > **Add to Home Screen**.
- **Desktop (Chrome/Edge)**: Click the install icon in the address bar or menu.
- **Offline Shell**: Service Worker (`service-worker.js`) caches the application shell and icons for instant offline launch.

---

## 🚀 Free Deployment

- **GitHub Pages / Cloudflare Pages**: Push this directory to your repository and enable static hosting.
- **Vercel**: `vercel.json` configures strict Content Security Policy headers permitting `https://lrclib.net`.
