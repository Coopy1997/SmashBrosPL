# PolSmash

PolSmash is a community platform for the Polish competitive **Super Smash Bros. Ultimate** scene. It brings tournament results, Elo rankings, player profiles, city communities, events, statistics, streams, and community posts into one responsive web application.

[Visit PolSmash] (https://polsmash.vercel.app/)/) |

## Product Overview

Tournament information is synchronized from start.gg and transformed into useful, easy-to-read community tools. Players can follow the competitive scene, review their performance, discover local communities, and find upcoming events without searching across multiple platforms.

PolSmash is designed for:

- Players tracking rankings, results, opponents, characters, and activity
- Tournament organizers promoting events and maintaining city information
- Communities discovering players, crews, streams, and local scenes
- Spectators following recent results, season stories, and competitive trends

## Main Features

### Rankings and Results

- Overall and seasonal Elo leaderboards
- Fresh seasonal rankings that restart from the base rating each year
- Offline, online, and combined ranking modes
- Player win/loss records, rating history, peaks, and recent matches
- Tournament standings, podiums, brackets, and set results
- Biggest upsets, rising players, activity records, and season recaps

### Player Profiles

- Claimable player profiles linked to website accounts
- Custom display name, biography, tagline, pronouns, images, and accent color
- Main and secondary character selection
- Social links and profile-following support
- Activity heatmaps, achievements, city rank, crew, and season history
- Shareable profile pages with generated social preview images

### Events and Local Communities

- Upcoming and historical tournament directory
- Interactive tournament and player map
- Calendar view with direct start.gg links
- City pages with rankings, events, community information, and custom crests
- Tournament organizer roles for maintaining local city content
- Twitch and YouTube stream directory

### Community Tools

- Smashiki community feed with categories, images, likes, and comments
- Crew discovery based on player team prefixes
- Player comparison tool
- Character popularity and matchup statistics
- Automatic bracket seeder using current Elo ratings
- Search across players and tournaments
- English and Polish language support
- Dark and light themes
- Installable Progressive Web App experience

## Data and Ranking Model

PolSmash imports public tournament data through the start.gg GraphQL API. The data pipeline stores tournaments, events, entrants, sets, game-level character selections, streams, and canonical player identities.

Rankings are calculated by replaying eligible sets chronologically through a deterministic Elo engine:

| Setting | Value |
| --- | --- |
| Starting rating | 1500 |
| K-factor | 24 |
| Ranked eligibility | Minimum 3 sets |
| Seasonal rankings | Only sets from the selected calendar year |
| Administrative DQs | Excluded from Elo calculations |

Low-sample confidence weighting is used where appropriate for overall rankings. Seasonal boards are ranked by Elo earned within that season.

## Technology

| Area | Technology |
| --- | --- |
| Web application | Next.js 15, React 19, TypeScript |
| Database access | Prisma ORM |
| Production database | PostgreSQL |
| Authentication and uploads | Supabase |
| Tournament data | start.gg GraphQL API |
| Hosting and scheduled jobs | Vercel |
| Maps | Leaflet with OpenStreetMap/CARTO tiles |
| Testing | Node test runner with TypeScript |

The application uses server-rendered pages, incremental caching, generated metadata images, responsive layouts, security headers, sitemap and robots support, and scheduled tournament re-ingestion.
