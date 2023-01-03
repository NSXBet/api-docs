## Markets API

- GET https://prod-global-external-partners-api.bet6.com.br/api/markets?search={SEARCH}&limit={LIMIT}&skip={SKIP}
- Parameters:
    - SEARCH: A search string to filter the tourneys by tournament name
    - LIMIT: The number of events to return
    - SKIP: The number of events to skip

```typescript
type Market = {
    id: number; // Id of the market
    name: string; // Translated name of the market
    english_name: number;  // Reference name of the market
}
type ReturnType =  Market[];
```
