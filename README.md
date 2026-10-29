# Board Game Recommender

> 🚧 **Status: in development** – this README describes the planned scope. Sections marked *(planned)* are not implemented yet.

A data-driven web application that recommends board games based on user input. Users set hard constraints (e.g. player count, playing time) and pick around five games they enjoy; the app returns similar games that satisfy those constraints.

The project focuses on the full path from external data to a served model: consuming a third-party API, building a local data store, implementing and evaluating a recommender, and exposing it through an own REST API.

## Problem

Choosing a new board game is hard: there are tens of thousands of titles, and popularity rankings ignore personal taste. This project asks a measurable question:

**Can a recommender that uses a user's favourite games outperform a simple baseline that returns the highest-rated games matching the same constraints?**

If it cannot, the seed games add no value, and the evaluation will report that honestly.

## How it works

1. **Hard constraints** – the user filters by criteria such as maximum player count and maximum playing time.
2. **Seed games** – the user selects ~5 games they like from a searchable list.
3. **Recommendation** – candidate games are ranked by similarity to the seed games, based on game attributes (mechanics, categories, complexity, …).

## Architecture *(planned)*

```
BGG XML API ──► Ingestion script ──► Local database ──► Recommender ──► REST API ──► Web frontend
               (server-side,          (cached game                     (own
                rate-limited)          metadata)                        endpoints)
```

The web application never calls BoardGameGeek directly. All BGG requests are made server-side by a batch ingestion step and cached locally, as recommended by BGG's API guidelines.


## Roadmap

- [ ] Problem definition and BGG API access
- [ ] Data ingestion and local database
- [ ] Exploratory data analysis
- [ ] Baseline and content-based recommender
- [ ] Offline evaluation against the baseline
- [ ] REST API with tests
- [ ] Web frontend
- [ ] Containerisation and deployment



