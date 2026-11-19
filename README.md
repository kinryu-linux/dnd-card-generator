# D&D 2024 Card Manager

A single-file browser app for browsing, filtering, and printing D&D 2024 (5.5e) spell and item reference cards.

Cards are formatted as printable A4 sheets (4 per page) — handy for handing out to players or stashing in a DM binder.

## Files

| File | Description |
|------|-------------|
| `dnd-card-manager.html` | The app — open this in any browser |
| `cards-data.zip` | Card data: spells, items, and magic items |

## Getting started

1. Open `dnd-card-manager.html` in your browser (Chrome or Firefox recommended).
2. Click **Load Data (ZIP)** and select `cards-data.zip`.  
   Data is saved to your browser's local storage — you only need to do this once.
3. Browse, filter, and select cards, then click **Print Selected**.

## Features

- **Table view** — sortable columns: Name, Type, Level/Category, School/Rarity, Source, Classes
- **Hover preview** — mouse over any row to see the card
- **Filters** — item type chips (Simple, Martial, Potions, Magic, Gear…), spell level chips, class chips, and a search box
- **Checkbox selection** — tick rows individually or use **Select All Filtered**
- **Print Selected** — generates 4-up A4 print pages for only the cards you've checked
- **Custom card builder** — click **＋ New Card** to create a spell or item card with a live preview; saved cards persist in local storage
- **Edit / Delete** — double-click any row to edit or delete that card
- **Export ZIP** — download your current data (including any custom cards) as a zip

## Card data

The included data covers D&D 2024 (5.5e) rules:

- **479 spells** — PHB cantrips through 9th level, plus spells from SCAG, XGtE, and TCE, all tagged with class lists including Artificer
- **107 mundane items** — weapons, armour, adventuring gear, tools, kits, gaming sets, and musical instruments
- **127 magic items** — common through rare items appropriate for levels 1–5 (potions, scrolls, wands, rings, wondrous items) sourced from DMG, XGtE, and TCE

## Updating the data

The zip contains three JSON files:

| File | Contents |
|------|----------|
| `spells.json` | All spells |
| `items.json` | Mundane items |
| `magic_items.json` | Magic items |

**Option A — in the app:** Use **Export ZIP** to download your current data, edit the JSON files in a text editor, re-zip them (keeping the same filenames), and re-import with **Load Data (ZIP)**.

**Option B — from source:** Edit `phb_data.json` and regenerate:

```
python split_data.py
python package_data.py
```

Then re-import the new `cards-data.zip`.

## Card schema

**Spell fields:** `type`, `name`, `level`, `school`, `castTime`, `range`, `components`, `duration`, `classes`, `description`, `subEntries`, `higherLevel`

**Item fields:** `type`, `name`, `category`, `cost`, `weight`, `damage`, `damageType`, `ac`, `properties`, `description`, `masteryProperty`, `masteryText`

**Magic item additional fields:** `rarity`, `source`, `consumable`
