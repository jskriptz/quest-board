# Quest Board

A single-file HTML gamification app that turns daily tasks into fantasy RPG quests.

## Features

- **Character Sheet** — STR, CHA, INT stats that grow as you complete quests
- **XP & Levelling** — Earn XP and level up your adventurer
- **Equipment Slots** — Weapon, Off-hand, Helm, Chest, Ring, Amulet
- **Loot Rolls** — Complete quests to earn d20 loot rolls
- **Main & Side Quests** — Separate tabs for job search and personal tasks
- **AI Quest Generation** — Optional: transforms plain tasks into epic RPG quests (BYOK)
- **Fully Offline** — Works without internet, no dependencies

## Quick Start

1. Open `index.html` in any browser
2. Add quests and complete them to earn XP and loot
3. (Optional) Add your Anthropic API key for AI-generated quest flavour

## AI Features (Optional)

Quest Board uses **Bring Your Own Key (BYOK)** for AI features:

- Get a key from [console.anthropic.com](https://console.anthropic.com)
- Enter it in "API Settings" in the sidebar
- Your key stays in your browser — never on any server
- Without a key, the app works fully offline (quests use plain text)

## Deployment

### GitHub Pages
1. Fork this repo
2. Go to Settings → Pages → Deploy from main
3. Access at `https://yourusername.github.io/quest-board`

### Local
Just open `index.html` — everything works offline except AI generation.

## File Structure

```
index.html          # The entire app (single file)
quest-board.md      # Detailed documentation
README.md           # This file
LICENSE             # MIT License
docs/
  ├── PRIVACY.md        # Privacy policy
  ├── TERMS.md          # Terms of service
  ├── CONTRIBUTING.md   # Contribution guidelines
  ├── CODE_OF_CONDUCT.md # Community standards
  └── SECURITY.md       # Security policy
```

## Tech Stack

| Layer | Technology |
|-------|-----------|
| UI | Vanilla HTML + CSS + JS |
| Styling | CSS custom properties, dark theme |
| AI | Anthropic API (Haiku) — optional, BYOK |
| Storage | Browser localStorage |
| Build | None — single file |

## License

[MIT](LICENSE)

## Links

- [Detailed Documentation](quest-board.md)
- [Privacy Policy](docs/PRIVACY.md)
- [Security Policy](docs/SECURITY.md)
