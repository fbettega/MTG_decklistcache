# MTG_decklistcache

This repository contains a cache in JSON format of tournaments posted on [MTGO](https://www.mtgo.com/decklists), [Manatraders](https://www.manatraders.com/tournaments/2), [Melee](https://melee.gg/Decklists), and [Topdeck](https://topdeck.gg) websites.

## Repository Structure

- **Tournaments**: Main tournament repository, organized by website and date.
- **Tournaments-Archive**: Archive of older tournaments (for sources that are no longer updated or maintained), organized by website and date.

> **Note:** MTGO.com data from 2024-06-20 onwards is significantly more limited due to website changes and is stored in a separate folder.

## JSON Format

Each JSON file corresponds to a `CacheItem` object, containing:
- A **Tournament** object (basic event information),
- An array of **Deck** objects (decklists submitted),
- An array of **Round** objects (match pairings and results, when available),
- An array of **Standing** objects (final standings, when available).



```json
{
  "Tournament": {
    "date": "2025-04-20",
    "name": "Topdeck Season Finals",
    "uri": "https://topdeck.gg/event/12345",
    "formats": ["Modern"],
    "json_file": "Topdeck/2025-04-20_Topdeck_Season_Finals.json",
    "force_redownload": false
  },
  "Decks": [
    {
      "date": "2025-04-20",
      "player": "Alice",
      "result": "5-1",
      "anchor_uri": "https://topdeck.gg/deck/abc123",
      "mainboard": [
        {"count": 4, "card_name": "Lightning Bolt"},
        {"count": 4, "card_name": "Ragavan, Nimble Pilferer"}
      ],
      "sideboard": [
        {"count": 2, "card_name": "Fury"},
        {"count": 1, "card_name": "Engineered Explosives"}
      ]
    }
  ],
  "Rounds": [
    {
      "round_name": "Quarterfinals",
      "matches": [
        {
          "player1": "Alice",
          "player2": "Bob",
          "result": "2-1",
          "id": "match1"
        }
      ]
    }
  ],
  "Standings": [
    {
      "rank": 1,
      "player": "Alice",
      "points": 15,
      "wins": 5,
      "losses": 0,
      "draws": 0,
      "omwp": 0.67,
      "gwp": 0.75,
      "ogwp": 0.71
    }
  ]
}
```

## Usage

To use the data:
1. Clone the repository.
2. Run `git pull` periodically to fetch the latest tournaments.

- **MTGO**, **Melee**, and **Topdeck** data are automatically updated daily around **17:00 UTC**.
- **Manatraders** data is usually updated on the **Monday** following the tournament, around the same time.

## Related Tools

The tools used to scrape and generate this data are available [here](https://github.com/fbettega/mtg_decklist_scrapper).

---

This repository provides an open, standardized dataset for researchers, players, and developers interested in analyzing Magic: The Gathering tournament results.

## Acknowledgment
The design of these entities was initially inspired by a C# project available [here](https://github.com/Badaro/MTGODecklistCache.Tools), and follows a similar structure. 