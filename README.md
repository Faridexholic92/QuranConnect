# 🕌 QuranConnect

> Read. Listen. Memorize. — A focused Quran companion built for daily practice.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-in%20development-orange)
![Stack](https://img.shields.io/badge/stack-Flutter%20%7C%20Next.js%20%7C%20TypeScript-informational)

---

## ✨ Features

| Feature | Description |
|---|---|
| 📖 Clean Reading Mode | Distraction-free Uthmani script with translation overlay |
| 🎧 Audio Recitations | 50+ reciters via Quran.com API, verse-synced |
| 🧠 Hifz Mode | Spaced repetition memorization with self-test |
| 🔖 Bookmarks & Progress | Reading streaks, completed juz tracking |
| 📴 Offline First | Full text + downloaded audio available offline |
| 🔒 Privacy Focused | No account required. No tracking. |

---

## 🛠 Tech Stack

### Mobile (Flutter)
```
Flutter SDK
Dart
just_audio — audio playback
hive / isar — local storage
riverpod — state management
```

### Web / PWA (Next.js)
```
Next.js 14 (App Router)
TypeScript
Tailwind CSS
TanStack Query — data fetching
Zustand — global state
PWA (next-pwa) — offline support
```

### Data
```
Quran.com API v4 — Quran text, translations, audio
https://api-docs.quran.com
```

---

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- Flutter SDK 3.x
- Free API key from [Quran.com](https://quran.com/)

### Web / PWA
```bash
git clone https://github.com/Faridexholic92/QuranConnect.git
cd QuranConnect/web
npm install
cp .env.example .env.local
# Add your Quran.com API key to .env.local
npm run dev
```

### Mobile (Flutter)
```bash
cd QuranConnect/mobile
flutter pub get
flutter run
```

---

## 🌐 Quran.com API — Quick Reference

### Base URL
```
https://api.quran.com/api/v4
```

### Key Endpoints

| Endpoint | What you get |
|---|---|
| `GET /chapters` | All 114 Surahs (name, ayah count, revelation type) |
| `GET /verses/by_chapter/{id}` | Ayahs for a specific Surah |
| `GET /recitations` | List of all available reciters |
| `GET /audio_files/{recitation_id}/{chapter_number}` | Audio file for a Surah |
| `GET /translations` | Available translations (Malay, English, etc.) |

### Example — Fetch Al-Fatiha
```ts
const res = await fetch(
  'https://api.quran.com/api/v4/verses/by_chapter/1?language=en&words=true&translations=131'
);
const data = await res.json();
// data.verses[0].text_uthmani → Arabic text
// data.verses[0].translations[0].text → English translation
```

### Example — Get Audio for a Surah
```ts
// Recitation ID 7 = Mishary Rashid Alafasy
const res = await fetch(
  'https://api.quran.com/api/v4/chapter_recitations/7/1'
);
const data = await res.json();
// data.audio_file.audio_url → direct MP3 URL
```

> No API key required for basic endpoints. Rate limited to 120 req/min.

---

## 📁 Project Structure

```
QuranConnect/
├── web/                  # Next.js PWA
│   ├── app/
│   ├── components/
│   ├── lib/api/          # Quran.com API client
│   └── public/
├── mobile/               # Flutter app
│   ├── lib/
│   │   ├── features/
│   │   ├── data/
│   │   └── main.dart
│   └── pubspec.yaml
├── docs/
│   └── index.html        # Landing page
└── README.md
```

---

## 🗺 Roadmap

- [x] Set up project structure & repo
- [ ] Define data model (Surah, Ayah, Translation, Reciter, UserState)
- [ ] Integrate Quran.com API
- [ ] Build Surah list & Ayah reader UI
- [ ] Implement audio playback
- [ ] Add bookmarks & reading progress
- [ ] Build Hifz mode
- [ ] PWA manifest & offline support
- [ ] Daily practice reminders
- [ ] Deploy to Vercel + app stores

---

## 🤝 Contributing

This is a solo project in active development. Issues and PRs are welcome once the MVP is stable.

---

## 📄 License

MIT © 2026 [Faridexholic](https://github.com/Faridexholic92)
