## Odds API

- GET https://prod-global-external-partners-api.bet6.com.br/api/events-with-odds?sportId={SPORT_ID}&marketIds={MARKET_IDS}&tournamentId={TOURNAMENT_ID}&statusId={STATUS_ID}&limit={LIMIT}&skip={SKIP}
- Parameters: 
  - SPORT_ID: The sport id (e.g. 1 for soccer)
  - MARKET_IDS: The market ids (e.g. 1 for 1x2), can accept multiple markets splitted by comma (eg. marketIds=1,2)
  - TOURNAMENT_ID: The tournament id
  - STATUS_ID: The status id (e.g. 0 for pre-game, 1 for live)
  - LIMIT: The number of events to return
  - SKIP: The number of events to skip
  
- Return Types:
```typescript
type Event = {
    id: number; // id of the event composed with the outcome id
    event_id: number; // id of the event
    category_id: number; // Id of the category
    sport_id: number; // id of the sport (e.g. 1 (Soccer), 2 (Volleyball))
    season_id: number; // id of the season, tournament start and end date
    tournament_id: number; // id of the tournament (e.g. 10, 15)
    market_id: number; // id of the market (e.g. total goals scored, goal scorers, handicap)
    tournament_name: string; // Name of the tournament (e.g. UEFA Champions League)
    category_name: string; // Name of the category (e.g. International Teams)
    home: string; // name of the home team
    away: string; // name of the away team
    date_start: string; // When the event starts
    date_start_original: string; // Same than date_start
    tournament_important: number; // specifies the priority of the tournament to be displayed
    booked: number; // indicate if event will have live odds or not
    created_at: Date; // event creation date in the database
    event_status_id: number; // status of the event, 0 = pre-match, 1 = live, 3 = closed
    image_name: string | null ; // Image of the event
    market_count: number; // number or markets available for this event, coming 0 default
    market_status_id: number; // market status, 1 = active, 0 = inactive, -1 = suspended
    match_date: string; // match date
    odd: string; // The odd for the outcome in this event;
    outcome_id: number; // Represents if the odd is for home ("1"), draw ("2") or away ("3")
    specifier: string; // additional info about the market ID. e.g total=2.5
    specifier_value: string;
};
type ReturnType =  Event[];
```
