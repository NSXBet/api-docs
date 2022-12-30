- GET https://prod-global-external-partners-api.bet6.com.br/api/tourneys?search={SEARCH}&limit={LIMIT}&skip={SKIP}
- Parameters:
    - SEARCH: A search string to filter the tourneys by tournament name
    - LIMIT: The number of events to return
    - SKIP: The number of events to skip

```typescript
type Tourney = {
    category_id: number; // Id of the category
    image_name: string | null; // Image of the tourney
    season_id: number;  // Id of the season
    sport_id: number;  // Id of the sport
    tournament_id: number; // Id of the tournament
    tournament_name: string; // Name of the tournament (e.g. UEFA Champions League)
}
type ReturnType =  Tourney[];
```
