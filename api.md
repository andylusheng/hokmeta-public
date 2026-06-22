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

## Example Hero Object

```json
{
  "slug": "hou-yi",
  "name": "Hou Yi",
  "role": "Marksman",
  "lane": "Farm Lane",
  "tier": "S+",
  "difficulty": "Easy",
  "winRate": 52.1,
  "pickRate": 2.4,
  "banRate": 0.3,
  "arcana": ["Cataclysm", "Hunt", "Eagle Eye"],
  "spells": ["Flash"]
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
