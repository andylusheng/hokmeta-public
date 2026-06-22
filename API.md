# HOKMeta Public API

HOKMeta provides static JSON endpoints for Honor of Kings Global hero and item data.

Base URL:

```txt
https://hokmeta.com
```

## Endpoints

### All Heroes

```txt
GET /api/heroes.json
```

URL:

```txt
https://hokmeta.com/api/heroes.json
```

Returns an array of all tracked Honor of Kings Global heroes.

### Single Hero

```txt
GET /api/heroes/{slug}.json
```

Example:

```txt
https://hokmeta.com/api/heroes/hou-yi.json
```

Returns data for a single hero by slug.

### Items

```txt
GET /api/items.json
```

URL:

```txt
https://hokmeta.com/api/items.json
```

Returns item data used in HOKMeta hero builds.

## Hero Fields

Common hero fields include:

| Field | Type | Description |
|---|---|---|
| `slug` | string | URL-safe hero identifier |
| `name` | string | English hero name |
| `role` | string | Primary role |
| `roles` | string | Role tags |
| `lane` | string | Recommended lane |
| `tier` | string | Current meta tier |
| `difficulty` | string | Hero difficulty |
| `winRate` | number/null | Win rate percentage |
| `pickRate` | number/null | Pick rate percentage |
| `banRate` | number/null | Ban rate percentage |
| `build` | array | Recommended item build |
| `arcana` | array | Recommended arcana |
| `spells` | array | Recommended battle spells |
| `counters` | array | Heroes this hero is strong into |
| `counteredBy` | array | Heroes that counter this hero |
| `skills` | array | Hero skill data |
| `patchHistory` | array | Recent balance changes |
| `dataUpdated` | string/null | Last data sync date when available |

## Item Fields

Common item fields include:

| Field | Type | Description |
|---|---|---|
| `id` | string | Item ID |
| `slug` | string | URL-safe item identifier |
| `name` | string | English item name |
| `description` | string | Item stat line and short description |
| `descLabel` | string/null | Short item label |
| `passiveSkills` | array | Passive effect descriptions |
| `icon` | string | Item icon URL |
| `gold` | number/null | Item cost |
| `type` | string/null | Item category |
| `level` | number/null | Item level when available |

## Example Hero Object

```json
{
  "slug": "hou-yi",
  "name": "Hou Yi",
  "role": "Marksman",
  "roles": "Marksman",
  "lane": "Farm Lane",
  "tier": "S+",
  "difficulty": "Medium",
  "winRate": 49.18,
  "pickRate": 2.45,
  "banRate": 0.15,
  "arcana": ["Lvl 5: Red Moon", "Lvl 5: Unparalleled", "Lvl 5: Beast Scar"],
  "spells": ["Flash"],
  "counters": ["Cirrus", "Mulan", "Xuance"],
  "counteredBy": ["Agudo", "Master Luban"],
  "dataUpdated": "2026-06-22"
}
```

## JavaScript Example

```js
async function getHero(slug) {
  const res = await fetch(`https://hokmeta.com/api/heroes/${slug}.json`);

  if (!res.ok) {
    throw new Error('Hero not found');
  }

  return res.json();
}

getHero('hou-yi').then(console.log);
```

## Fetch All Heroes

```js
async function getHeroes() {
  const res = await fetch('https://hokmeta.com/api/heroes.json');
  return res.json();
}
```

## Fetch Items

```js
async function getItems() {
  const res = await fetch('https://hokmeta.com/api/items.json');
  return res.json();
}
```

## Common Use Cases

This API can be used to build:

- Discord hero lookup bots
- Counter pick tools
- Ranked climb dashboards
- Content creator overlays
- Community spreadsheets
- Meta reports
- Fan-made Honor of Kings tools

## Data Notes

HOKMeta focuses on Honor of Kings Global.

Data may include hero stats, builds, counters, arcana, spells, skills, and patch notes. The data is updated periodically and may not always reflect live in-game changes immediately.

## Attribution

If you use this data publicly, please credit HOKMeta:

```md
[Data by HOKMeta](https://hokmeta.com)
```

Suggested plain text attribution:

```txt
Data by HOKMeta: https://hokmeta.com
```

## Disclaimer

HOKMeta is an independent fan-made project.

It is not affiliated with Tencent, Level Infinite, TiMi Studio Group, or Honor of Kings.

All trademarks belong to their respective owners.
