# Tradish (Working Title)

**Tagline:** Discover authentic, lesser-known global recipes enriched with cultural context and adaptive ingredient guidance.

## Overview
Tradish is a mobile app for culturally curious individuals, home cooks, and learners seeking authentic yet lesser-known recipes from around the world. It blends culinary instruction with storytelling, highlighting cultural origins, regional techniques, and adaptive substitutions.

## Core User Flow
1. Personalization: choose language + optional focus country.
2. Discovery Feed: personalized recipe recommendations.
3. Recipe Detail: steps, cultural background, story, local tips, ingredient list.
4. Ingredient Management: mark unavailable items, request AI substitutions, scan environment to build an editable available-ingredients list.
5. Adaptive Suggestions: feed adjusts based on ingredient availability.

## Key Interactions
- Browse / search recipes
- View steps + cultural narrative
- Mark ingredients unavailable
- “Find Substitute” (AI suggestions)
- Scan to auto-generate ingredient list
- (Future) favorite/save

## Data Entities
**User:** id, profile, language, focusCountry, dietaryPrefs  
**Recipe:** id, title, ingredients, instructions[], story, culturalNotes, tags  
**Ingredient:** id, name, availabilityStatus, substitutes[]  
**IngredientList:** id, userId, source (manual|scan|AI), items[]  
**SubstitutionSuggestion:** missingIngredientId, candidates[], confidence, rationale

## Adaptive Logic (High-Level)
1. Initial recommendations seeded by language + focus country.  
2. Ingredient availability re-ranks recipes.  
3. Substitution requests generate localized & accessible alternatives.  
4. Scans update availability -> refresh feed.

## Example API (Illustrative)
`GET /api/feed` -> `{ recipes: [ { id, title, matchScore, unavailableCount } ] }`  
`POST /api/substitutions` -> suggestions with confidence + rationale.

## Scanning Concept
Scan -> extract text -> normalize -> map to ingredients -> return confirmed list -> update availability.

## Possible Tech Stack (MVP)
- Mobile: React Native or Flutter
- Backend: Node.js + PostgreSQL
- Search/Semantic: Vector store
- AI Layer: Substitutions + narrative enrichment
- Object Storage: Media assets

## Future Enhancements
- Offline cache
- Audio / multimedia cultural snippets
- Dietary filters (vegan, halal, kosher, etc.)
- Seasonal availability
- Community submissions
- Gamified exploration

## Security & Privacy
Minimal PII (email + optional avatar), anonymized analytics, AI prompts exclude personal data.

## Contributing
1. Fork
2. `git checkout -b feature/<name>`
3. Code & test
4. `git commit -m "Add ..."`
5. `git push origin feature/<name>`
6. Open Pull Request

## Branch Workflow
- No direct commits to `main`
- Use `feature/`, `fix/`, `content/` prefixes
- Rebase or merge main before final review

## License
(To be decided: MIT / Apache-2.0 / other)

## Status
Concept / Demo – Not production ready.
