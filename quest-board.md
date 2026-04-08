# Quest Board

## Overview

**Quest Board** is a single-file HTML gamification app that turns daily tasks into fantasy RPG quests. It is designed to make productivity feel rewarding by wrapping to-do items in a dark fantasy RPG aesthetic with character stats, equipment slots, loot rolls, and XP progression.

The app lives at `quest-board.html` and requires no server, no build step, and no dependencies. Drop it into any static host and it works.

---

## Purpose

The app was built to help with job searching motivation. The core idea is that completing real-world tasks — applying for jobs, studying, cleaning, hobby projects — feels more satisfying when framed as quests with tangible rewards.

---

## Features

- **Character sheet** — STR, CHA, INT stats that increase as quests are completed
- **XP and levelling** — completing quests awards XP; enough XP levels the character up
- **Equipment slots** — Weapon, Off-hand, Helm, Chest, Ring, Amulet; filled by loot rolls
- **Inventory** — overflow loot goes here as pills
- **Portrait upload** — click the portrait box to upload any image (AI-generated art recommended)
- **Main quests** — job search tasks (outreach, applications, studying)
- **Side quests** — personal tasks, hobbies, chores (40k modelling, cleaning, etc.)
- **Tabbed quest view** — main and side quests separated by tabs
- **Add quests** — type any task and hit Enter or Add; AI generates epic RPG title and flavour text
- **Delete quests** — × button removes any quest
- **Loot rolls** — each completed quest awards one loot roll (d20); higher rolls = rarer items
- **Legendary drop** — rolling a natural 20 awards The Adventurer's Signet (+1 all stats)
- **Toast notifications** — level up and quest complete messages pop from the bottom
- **Fully offline** — no external dependencies; works as a local file or on GitHub Pages

---

## Quest Structure

Each quest has the following fields:

| Field | Type | Description |
|-------|------|-------------|
| `id` | number | Unique integer ID assigned on creation |
| `title` | string | RPG-style quest name (AI-generated or default) |
| `desc` | string | One-sentence flavour text describing the quest |
| `xp` | number | XP awarded on completion (main: 30–40, side: 15–25) |
| `stat` | number | Stat index boosted on completion (-1 = none, 0 = STR, 1 = CHA, 2 = INT) |
| `sv` | number | Stat boost amount (1 or 2) |
| `done` | boolean | Whether the quest has been completed |
| `type` | string | `"main"` or `"side"` |

---

## Default Quests

### Main quests

| Title | Description | XP | Stat |
|-------|-------------|-----|------|
| The Messenger's Call | Reach out to your network | 30 | +2 CHA |
| The Guild Applications | Apply to saved positions | 40 | +2 STR |
| The Scholar's Trial | Study for accessibility test | 30 | +2 INT |

### Side quests

| Title | Description | XP | Stat |
|-------|-------------|-----|------|
| Purge the Chaos from the Keep | Clean the office | 20 | +1 STR |
| Summon the Daemon Prince | Build Daemon Prince 40k miniature | 25 | +1 INT |
| Anoint the Warriors | Spray prime all models | 15 | none |
| The First Coat | Paint models brown | 15 | +1 INT |
| Forge the Battlefield | Create bases for models | 20 | +1 STR |
| Seal the Ground | Spray prime the bases | 15 | none |

---

## Loot Table

| Item | Type | Slot | Stat Bonus | Min Roll |
|------|------|------|------------|----------|
| Blade of Confident Words | weapon | Weapon | +1 CHA | any |
| Staff of Arcane Authority | weapon | Weapon | +1 INT | any |
| Mantle of Persistence | armor | Chest | +1 STR | any |
| Helm of Focus | armor | Helm | +1 INT | any |
| Ring of Resilience | accessory | Ring | +2 STR | 16 |
| Amulet of Silver Tongue | accessory | Amulet | +2 CHA | 16 |
| Tome of Hidden Lore | accessory | Off-hand | +2 INT | 16 |
| The Adventurer's Signet | legendary | Ring | +1 ALL | 20 (nat 20) |

---

## Character Stats

| Stat | Abbreviation | Boosted by |
|------|-------------|------------|
| Strength | STR | Physical quests (applications, cleaning, building) |
| Charisma | CHA | Social quests (outreach, networking) |
| Intelligence | INT | Mental quests (studying, planning, crafting) |

---

## XP and Levelling

- Level threshold: `level × 100` XP
- On level up, XP resets to remainder after threshold
- Level is displayed in the header alongside current XP

---

## AI Quest Generation (Optional — Bring Your Own Key)

AI quest generation is **optional** and uses a **Bring Your Own Key (BYOK)** model.

**To enable AI features:**
1. Get an API key from https://console.anthropic.com
2. Enter your key in the "API Settings" section in the sidebar
3. Your key is stored in your browser only — never on any server

**How it works:**
- The app calls the Anthropic API (`claude-haiku-4-5-20251001`) to generate:
  - A short epic RPG quest title (4–6 words)
  - A one-sentence dark fantasy flavour description
- Each user pays for their own API usage (Haiku is very cheap)
- The call requires the header `anthropic-dangerous-direct-browser-access: true`

**Without an API key:**
- The app works fully offline
- Quests use the plain text you enter as the title
- All other features (stats, loot, levelling) work normally

If the API call fails, the plain text is used as a fallback.

---

## File Structure

```
quest-board.html    — the entire app (single file, no dependencies)
quest-board.md      — this documentation file
```

---

## Deployment

### GitHub Pages (recommended)

1. Add `quest-board.html` to your repo (rename to `index.html` for root access)
2. Go to Settings → Pages → deploy from main branch
3. Access at `https://jskriptz.github.io/quest-board`

### Local

Open `quest-board.html` directly in any browser. AI generation may not work locally due to CORS — all other features work offline.

---

## Planned / Possible Additions

- Class selection (Warrior / Mage / Rogue) with class-specific stat bonuses
- Portrait display from uploaded image persisted via localStorage
- Quest persistence across sessions (localStorage or URL hash)
- Daily reset option for recurring quests
- Boss encounter — a special high-XP challenge unlocked after completing all main quests
- More loot items and item rarity tiers (Common / Uncommon / Rare / Legendary)
- Quest categories beyond main/side (e.g. daily, weekly, story)

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| UI | Vanilla HTML + CSS + JS (no framework) |
| Styling | CSS custom properties, dark theme |
| AI | Anthropic API — claude-haiku-4-5-20251001 |
| Hosting | GitHub Pages (static) |
| Build | None — single file |

---

## Character Lore

**The Seeker** is a class-unknown adventurer navigating the treacherous realm of job searching. Armed with determination and an ever-growing inventory of hard-won skills, they face each day as a series of quests — some noble, some mundane, all worthy of reward.

Class is yet to be determined: Warrior (bold, armoured, direct), Mage (strategic, studied, arcane), or Rogue (adaptable, quick, resourceful).
