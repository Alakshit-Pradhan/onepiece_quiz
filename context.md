# ☠ One Piece Quiz — Context File

**Project:** One Piece Quiz Website  
**Developer:** Alakshit Pradhan  
**Type:** Single-file HTML Web App  
**File:** `onepiece_quiz.html`

---

## 🎯 What This Project Is

A fast, interactive **One Piece character quiz** where a pirate's portrait appears and you have to pick the correct name from 4 options — within 8 seconds. Built as a single self-contained HTML file, no framework or build step needed.

Inspired by the classic *"Who's That Pokémon?"* format, adapted for the One Piece universe.

---

## 🕹️ How It Works

1. Open `onepiece_quiz.html` in any browser
2. Home screen loads **instantly** — no waiting
3. Click **Pirate / Captain / Yonko** to choose difficulty
4. The app fetches **50 characters** for that mode from AniList API (~1–2 sec)
5. Quiz starts — 50 questions, 8 seconds each, 4 answer choices
6. Score and pirate rank shown at the end

---

## ⚙️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Pure HTML + CSS + JavaScript |
| Framework | None — single `.html` file |
| Images | AniList GraphQL API (`graphql.anilist.co`) |
| Fonts | Google Fonts — Cinzel + Nunito |
| Build | No build step — open directly in browser |

---

## 🌐 Image Source — AniList API

Characters and their portrait images are fetched from the **AniList GraphQL API** at quiz start (per mode). AniList is free, public, and CORS-enabled — no API key required.

**Endpoint:** `https://graphql.anilist.co`

**Query used:**
```graphql
{
  Media(id: <anime_id>, type: ANIME) {
    characters(page: <page>, perPage: 25, sort: FAVOURITES_DESC) {
      nodes {
        id
        name { full }
        image { medium }
      }
    }
  }
}
```

**One Piece Anime ID on AniList:**
| Anime | AniList ID |
|---|---|
| One Piece (1999 — ongoing) | 21 |

One Piece is a single long-running anime (1000+ episodes) so all characters come from the same source, paginated by popularity.

**Pages fetched per mode:**
| Mode | Pages | Characters fetched |
|---|---|---|
| Pirate (Easy) | Pages 1–2 | Most popular — Straw Hats, Yonko, Warlords |
| Captain (Medium) | Pages 3–4 | Marines, Worst Generation, allies |
| Yonko (Hard) | Pages 5–7 | New World deep cuts, Wano, Final Saga |

Characters with missing/default images are automatically excluded.

---

## 🎮 Game Features

- **3 Difficulty Modes:**
  - 🏴‍☠️ **Pirate** 海賊 — Straw Hats, Yonko, Warlords & iconic One Piece cast (Easy)
  - ⚓ **Captain** 船長 — Marines, Worst Generation & supporting cast (Medium)
  - 👑 **Yonko** 四皇 — New World deep cuts, Wano & Final Saga (Hard)

- **8-second timer** per question — bar goes navy → amber → red as time runs out
- **50 questions** per round
- **4 answer choices** — shuffled each time
- **Keyboard shortcuts** — Press `1`, `2`, `3`, `4` to answer
- **Grading system** — S / A / B / C / D / F based on score
- **Smart caching** — replaying same mode uses cached data (instant restart)
- **Preloading** — next question's image loads in background for smooth transitions

---

## 🎨 Design — Wanted Poster & Ocean Theme

- **Background:** Warm parchment `#FFF8EE` — old wanted poster paper aesthetic
- **Primary colour:** Navy blue `#1A2E5E` — ocean / Marine uniform
- **Accent colour:** Dark red `#CC1500` — pirate flag / Luffy's colour
- **Gold:** `#C8920A` / `#FFD040` — treasure / bounty reward
- **Header & Footer:** Deep navy blue gradient
- **☠ skull & ⚓ anchor marks** floating throughout the UI
- **Sticky header:** `☠ ONE PIECE QUIZ ☠` + `Made by Alakshit Pradhan`
- **Sticky footer:** `⚓ Made by Alakshit Pradhan ⚓`
- **Portrait frame:** Square gold-bordered frame — Wanted poster style (not circular)
- **"WANTED" watermark** at top of character card
- **"DEAD OR ALIVE" watermark** at bottom of character card
- **Bounty chips** on the home screen — Straw Hats / Yonko / Marines / Warlords
- **Subtle skull pattern** as background tile
- **Fonts:** Cinzel (headings/titles) + Nunito (body text)
- **Japanese rank labels:** 海賊 / 船長 / 四皇 watermarked on mode cards
- **Card top border:** Navy → Red → Gold → Red → Navy gradient stripe
- **Result card:** Parchment gold with skull decoration

---

## 📁 File Structure

```
onepiece-quiz/
├── onepiece_quiz.html    ← Entire app (HTML + CSS + JS in one file)
├── context.md            ← This file
└── README.md             ← Project description
```

---

## 🚀 Running Locally

No setup required:

```bash
git clone https://github.com/Alakshit-Pradhan/onepiece-quiz.git
cd onepiece-quiz

# Option 1 — just open the file
open onepiece_quiz.html

# Option 2 — serve locally
python3 -m http.server 8000
# then visit http://localhost:8000
```

**Requirements:** A modern browser + internet connection (for AniList API and Google Fonts on first load).

---

## 🔄 How Loading Works

```
Open file
    ↓
Home screen visible INSTANTLY (no fetch on startup)
    ↓
User clicks Pirate / Captain / Yonko
    ↓
Card shows "⏳ Loading..." (~1-2 seconds)
    ↓
50 characters fetched from AniList for that mode
    ↓
Quiz starts immediately
    ↓
Play Again → loads from cache (instant)
```

---

## 📊 Scoring / Grades (One Piece-themed)

| Score | Grade | Title |
|---|---|---|
| 95–100% | S | ☠ Pirate King Level! |
| 85–94% | A | ⚓ Yonko Level! |
| 70–84% | B | 🏴‍☠️ Warlord Level! |
| 55–69% | C | ⚔ Pirate Captain! |
| 40–54% | D | 😅 Keep Sailing... |
| 0–39% | F | 💀 Walk the Plank! |

---

## 🔗 Related Projects

- **Naruto Quiz** — Same format, Naruto theme, uses AniList API
- **Bleach Quiz** — Same format, Bleach theme, uses AniList API
- **Dragon Ball Quiz** — Same format, Dragon Ball theme, uses AniList API
- **Pokemon Quiz** — [github.com/Alakshit-Pradhan/pokemon_quiz](https://github.com/Alakshit-Pradhan/pokemon_quiz) — Original, uses PokeAPI sprites

---

## 📚 Character Research Sources

- [animecharactersdatabase.com — All One Piece Characters](https://www.animecharactersdatabase.com/allchars.php?id=1447) — Full character list sorted by popularity
- [onepiece.fandom.com/wiki/Category:Characters](https://onepiece.fandom.com/wiki/Category:Characters) — Fandom wiki character database
- [en.wikipedia.org/wiki/List_of_One_Piece_characters](https://en.wikipedia.org/wiki/List_of_One_Piece_characters) — Comprehensive character descriptions
- [poggers.com — One Piece Characters](https://poggers.com/blogs/anime/one-piece-list-of-characters-straw-hat-pirates-allies) — Straw Hats & allies guide
- [tvtropes.org — One Piece Characters](https://tvtropes.org/pmwiki/pmwiki.php/Characters/OnePiece) — Full character index by group

---

*Made with ☠ by **Alakshit Pradhan***
