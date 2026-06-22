# HOKMeta

Honor of Kings Global meta database, hero builds, counters, tier lists, and public JSON API.

Website: https://hokmeta.com

## What Is HOKMeta?

HOKMeta is an independent Honor of Kings Global resource for players, guide writers, community tool builders, and content creators.

It helps players make better ranked decisions with structured hero data, build recommendations, counter picks, item references, patch tracking, and practical climb guides.

## What You Can Find

- Hero builds
- Tier lists by lane and role
- Counter picks and matchup notes
- Item and arcana references
- Patch and balance tracking
- Ranked climb recommendations
- Beginner and advanced strategy guides
- Static JSON data for community tools

## Key Pages

- Tier List: https://hokmeta.com/tier-list/
- Heroes Database: https://hokmeta.com/heroes/
- Best Heroes: https://hokmeta.com/best-heroes/
- Counter Picker: https://hokmeta.com/tools/counter-picker/
- Build Generator: https://hokmeta.com/tools/build-generator/
- Learning Hub: https://hokmeta.com/learn/

## Public Data API

HOKMeta provides static JSON endpoints for developers and community projects.

- All heroes: https://hokmeta.com/api/heroes.json
- Example hero: https://hokmeta.com/api/heroes/hou-yi.json
- Items: https://hokmeta.com/api/items.json

See [API.md](API.md) for endpoint details and usage examples.

## Use Cases

This project can be useful for:

- Honor of Kings guide writers
- Discord bot developers
- Content creators making build or counter videos
- MOBA data analysis
- Ranked climb dashboards
- Fan-made tools and websites
- Community spreadsheets

## Data Coverage

HOKMeta tracks Honor of Kings Global data such as:

- Hero names, roles, lanes, and difficulty
- Win rate, pick rate, and ban rate
- Recommended builds
- Arcana and spell setups
- Counter relationships
- Skills and playstyle notes
- Patch history and balance updates

## Example

```js
async function getHero(slug) {
  const res = await fetch(`https://hokmeta.com/api/heroes/${slug}.json`);
  if (!res.ok) throw new Error('Hero not found');
  return res.json();
}

getHero('hou-yi').then(console.log);
```

## Repository Purpose

This public repository is for:

- HOKMeta project introduction
- Public API documentation
- Data schema reference
- Sample data
- Example API usage

The production website source, data sync scripts, and internal operations tooling are not included here.

## Attribution

If you use HOKMeta data publicly, please credit:

```md
[Data by HOKMeta](https://hokmeta.com)
```

## Disclaimer

HOKMeta is an independent fan-made project.

It is not affiliated with Tencent, Level Infinite, TiMi Studio Group, or Honor of Kings.

All trademarks belong to their respective owners.
