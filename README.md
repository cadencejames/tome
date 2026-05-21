# Tome

Curated book series and author metadata in JSON format. Built as a fallback data source for [Caliper](https://github.com/cadencejames/Caliper) where free APIs have incomplete or inconsistent coverage. Grows organically with real library collections rather than attempting comprehensive coverage.

---

## Structure

```
book-data/
├── authors/
│   └── {slug}.json
└── series/
    └── {slug}.json
```

Files are named by slug (e.g. `jk-rowling.json`, `stormlight-archive.json`) and fetched individually — only what's needed, when it's needed.

---

## Schemas

### Author

```json
{
  "name": "J.K. Rowling",
  "slug": "jk-rowling",
  "birth_year": 1965,
  "death_year": null,
  "nationality": "British",
  "gender": "female",
  "pen_names": ["Robert Galbraith"],
  "genres": ["fantasy", "mystery"]
}
```

### Series

```json
{
  "name": "The Stormlight Archive",
  "slug": "stormlight-archive",
  "authors": ["brandon-sanderson"],
  "status": "ongoing",
  "universe": "cosmere",
  "genre": "fantasy",
  "related_series": ["mistborn", "warbreaker"],
  "books": [
    { "position": 1,   "title": "The Way of Kings",  "year": 2010, "type": "main" },
    { "position": 2.5, "title": "Edgedancer",        "year": 2016, "type": "novella" }
  ]
}
```

**Field notes:**
- `position` — supports decimals (0.5, 2.5) for novellas and interstitial entries
- `type` — `main` | `novella` | `short_story` | `spin_off`
- `universe` — groups series that share a world (e.g. all Cosmere series)
- `related_series` — slugs of spin-offs or same-universe series
- `authors` — array of author slugs; cross-references `authors/{slug}.json`

---

## Contributing

Entries are added as needed. If you use Caliper and want to add a series or author, open a PR with a new JSON file following the schemas above.
