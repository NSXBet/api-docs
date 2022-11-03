## Events by Season API

- GET `https://{DOMAIN}/api/{SKIN}/odds/1/events-by-seasons?sport_id={SPORT_ID}&tournament_id={TOURNAMENT_ID}&markets={MARKET_ID}&limit={LIMIT}&is_live={IS_LIVE}`
- Parameters:
  - DOMAIN: The domain of the API (e.g. betnacional.bet6.com.br)
  - SKIN: The skin that is requesting (e.g. betnacional)
  - SPORT_ID: The sport id (e.g. 1 for soccer)
  - TOURNAMENT_ID: The tournament id (e.g. 325 for World Cup)
  - MARKET_ID: The market id (e.g. 1 for 1x2)
  - LIMIT: The number of events to return (e.g. 10)
  - IS_LIVE: If the events should be live or not (e.g. 0 for pre-match, 1 for live)
  
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

type LiveScore = {
    away_gamescore: number | null; // Tennis game score
    away_score: number // Score of away team
    current_server: null | string; // Tennis current server
    event_id: number; // id of the event
    home_gamescore: number | null; // Tennis home game score
    home_score: number; // Score of home team
    match_status_code: number; // status of the match, first-half, second-half, penalties, etc
    match_time: string; // Current time of the match
    period: number; // Current period of the match
    remaining_time_in_period: null | string; // remaining time of match in Basketball
    stopped: number; // Is Clock stopped (Basketball)
    tiebreak: string | null; // Tennis Tiebreak
}

type ReturnType = {
    odds: Event[];
    scores?: LiveScore[]; // present only if is_live is 1
}
```
