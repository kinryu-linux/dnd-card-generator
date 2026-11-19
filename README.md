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
2. Click **Load Data from Server** on the welcome screen (or **Load Data (ZIP)** to import manually).  
   Data is saved to your browser's local storage — you only need to do this once.
3. Browse, filter, and select cards, then click **Print Selected**.

## Features

- **Table view** — sortable columns: Name, Type, Level/Category, School/Rarity, Source, Classes
- **Hover preview** — mouse over any row to see the card
- **Full-text search** — searches name, description, school, classes, cast time, components, and all other fields
- **Filters** — item type chips (Simple, Martial, Potions, Magic, Gear…), spell level chips, class chips, and a search box
- **Checkbox selection** — tick rows individually or use **Select All Filtered**
- **Print Selected** — generates 4-up A4 print pages for only the cards you've checked
- **Custom card builder** — click **＋ New Card** to create a spell or item card with a live preview; saved cards persist in local storage
- **Edit / Delete** — double-click any row to edit or delete that card
- **Export ZIP** — download your current data (including any custom cards) as a nicely formatted ZIP, ready to edit manually

## Importing data

When importing a ZIP while data is already loaded, you'll be asked how to handle it:

| Option | Behaviour |
|--------|-----------|
| Merge — Accept duplicates | Appends everything; duplicate cards coexist |
| Merge — Replace duplicates | Incoming version wins on name+type matches; everything else kept |
| Merge — Skip duplicates | Existing version wins; only genuinely new cards added |
| Delete & Replace | Wipes all existing data and loads only the new ZIP |

## Card data

The included data covers D&D 2024 (5.5e) rules:

- **479 spells** — PHB cantrips through 9th level, plus spells from SCAG, XGtE, and TCE, all tagged with class lists including Artificer
- **107 mundane items** — weapons, armour, adventuring gear, tools, kits, gaming sets, and musical instruments
- **127 magic items** — common through rare items appropriate for levels 1–5 (potions, scrolls, wands, rings, wondrous items) sourced from DMG, XGtE, and TCE

## Editing card data

**In the app:** Double-click any row to edit or delete that card. Click **＋ New Card** to create a new one. Changes are saved automatically to local storage.

**Bulk editing:** Use **Export ZIP** to download your current data as nicely formatted JSON, edit the files in a text editor, then re-import with **Load Data (ZIP)** using whichever merge option fits.

The exported JSON is formatted for readability — objects are indented, and simple arrays (like class lists) stay on one line:

```json
{
  "type": "spell",
  "name": "Fireball",
  "level": 3,
  "classes": ["Sorcerer", "Wizard"],
  "description": "..."
}
```

## Card schema

**Spell fields:** `type`, `name`, `level`, `school`, `castTime`, `range`, `components`, `duration`, `classes`, `source` *(optional)*, `description`, `subEntries` *(optional)*, `higherLevel` *(optional)*

**Item fields:** `type`, `name`, `category`, `cost`, `weight`, `damage`, `damageType`, `ac`, `properties`, `description`, `masteryProperty`, `masteryText`

**Magic item additional fields:** `rarity`, `source`, `consumable`

## Legal

Card text is sourced from D&D 2024 (5.5e) materials © Wizards of the Coast LLC.

Spell and item descriptions that appear in the [Systems Reference Document 5.2](https://www.dndbeyond.com/srd) are used under the [Creative Commons Attribution 4.0 International License (CC-BY-4.0)](https://creativecommons.org/licenses/by/4.0/). Non-SRD content is © Wizards of the Coast and is included here for personal and fan reference use only.

This project is an unofficial fan tool and is not affiliated with, endorsed by, or sponsored by Wizards of the Coast or Hasbro. It is non-commercial and intended for use at your own table. *Dungeons & Dragons* is a trademark of Wizards of the Coast LLC.

This project operates under the [Wizards of the Coast Fan Content Policy](https://www.dndbeyond.com/fancontent).

**No warranty.** This tool is provided "as is" without warranty of any kind. The author is not responsible for any issues arising from its use.
