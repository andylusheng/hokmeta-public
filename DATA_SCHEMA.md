# HOKMeta Data Schema

This document describes the common public data shapes used by the HOKMeta static JSON API.

The API is JSON-based and may add new fields over time. Consumers should ignore unknown fields and treat optional fields as nullable.

## Hero

```ts
type Hero = {
  slug: string;
  name: string;
  role: string;
  roles?: string;
  lane?: string | null;
  tier: 'S+' | 'S' | 'A' | 'B' | 'C' | string;
  difficulty?: string | null;
  winRate?: number | null;
  pickRate?: number | null;
  banRate?: number | null;
  build?: BuildItem[];
  arcana?: string[];
  spells?: string[];
  counters?: string[];
  counteredBy?: string[];
  skills?: Skill[];
  patchHistory?: PatchEntry[];
  dataUpdated?: string | null;
};
```

## Build Item

```ts
type BuildItem = {
  slot?: number;
  itemId?: string;
  name: string;
  description?: string;
  icon?: string;
};
```

## Skill

```ts
type Skill = {
  name: string;
  type?: string;
  description?: string;
  icon?: string;
};
```

## Patch Entry

```ts
type PatchEntry = {
  version?: string;
  date?: string;
  tag?: string;
  change?: string;
  detail?: string;
};
```

## Item

```ts
type GameItem = {
  id: string;
  slug?: string;
  name: string;
  description?: string;
  descLabel?: string;
  passiveSkills?: string[];
  icon?: string;
  gold?: number | null;
  type?: string | null;
  level?: number | null;
};
```

## Rate Fields

Rate fields are represented as percentage numbers.

Example:

```json
{
  "winRate": 49.18,
  "pickRate": 2.45,
  "banRate": 0.15
}
```

This means:

- Win rate: 49.18%
- Pick rate: 2.45%
- Ban rate: 0.15%

## Slugs

Slugs are URL-safe identifiers.

Examples:

- `hou-yi`
- `marco-polo`
- `luban-no-7`

Single hero endpoint format:

```txt
https://hokmeta.com/api/heroes/{slug}.json
```

## Stability Notes

The static endpoints are designed for simple read-only use.

Recommended client behavior:

- Cache responses when possible.
- Do not assume every optional field exists.
- Do not hard-code the full schema.
- Use `slug` as the stable hero identifier.
- Credit HOKMeta when publishing derived tools or reports.
