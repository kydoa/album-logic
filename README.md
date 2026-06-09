# album-logic

[![Language](https://img.shields.io/badge/Language-Prolog-orange)](https://www.swi-prolog.org/)
[![Status](https://img.shields.io/badge/Status-Functional-success)](https://github.com/)

A logic-based knowledge base implemented in Prolog, containing a curated catalogue of albums, artists, genres, and musical metadata.

The database stores relational facts including release years, instruments used, producers, and countries of origin, allowing for complex querying through logic programming.

## Table of Contents
- [What This Project Does](#what-this-project-does)
- [Why This Project Is Useful](#why-this-project-is-useful)
- [Database Schema](#database-schema)
- [Data Samples](#data-samples)
- [Getting Started](#getting-started)
- [Usage Examples](#usage-examples)
- [Project Structure](#project-structure)
- [Maintainers and Contributions](#maintainers-and-contributions)

## What This Project Does
`album-logic` implements a structured musical repository and an engine for relational queries:
- `album`: Defines the existence of an album in the catalogue.
- `genero`: Maps albums to their primary musical genres (e.g., 'Pop', 'MPB').
- `metadata predicates`: Stores complex attributes like release years, artists, and instruments.
- **Relational Queries**: Enables filtering by overlapping criteria (e.g., "Find all Rock albums released in the USA using electric guitar").

## Why This Project Is Useful
This repository is useful if you want to:
- Study how to represent real-world relational data using Prolog predicates.
- Learn how to construct complex queries involving list membership (`member`) and numerical comparisons.
- Use a template for building larger, more complex knowledge-based systems (KBS).
- Experiment with logic programming concepts like unification and backtracking in a musical context.

## Database Schema
The database is organized into the following predicates:
- **Core Facts**:
    - `album(Name)`: The primary identifier.
    - `genero(Album, Genre)`: Primary genre classification.
    - `gravado_por(Album, Band)`: Recording entity.
- **Extended Attributes**:
    - `artista(Album, Artist)`: Link to the performer.
    - `ano_de_lancamento(Album, Year)`: Chronological data.
    - `instrumentos(Album, ListOfInstruments)`: A list of musical tools used.
    - `pais_de_origem(Album, Country)`: Geographic origin.
    - `produtor(Album, Producer)`: Production credits.

## Data Samples
Below are examples of the facts stored in the database:

| Predicate | Example Fact |
| --- | --- |
| `album` | `album('Alucinação').` |
| `genero` | `genero('Thriller', 'Pop').` |
| `genero` | `genero('Getz/Gilberto', 'Bossa Nova').` |

## Getting Started
### Prerequisites
- SWI-Prolog installed on your system.

- **Or** use the SWISH website: https://swish.swi-prolog.org/

### Run the queries
1. Open your terminal or the SWI-Prolog console.
2. Load the database file:
   ```prolog
   consult('music_catalogue.pl').
   ```
3. Start querying the database directly.

## Usage Examples
### 1) Filter by Genre
Find all albums belonging to the 'Pop' genre:
```prolog
genero(Album, 'Pop').
```

### 2) Temporal Queries
Find all music released before the year 1980:
```prolog
ano_de_lancamento(Album, Year), Year < 1980.
```

### 3) Instrument Search
Identify albums that feature a 'piano' in their instrument list:
```prolog
instrumentos(Album, List), member(piano, List).
```

### 4) Multi-Criteria Filtering
Find 'Rock' albums from the 'USA' that use an 'electric_guitar':
```prolog
genero(Album, 'Rock'), pais_de_origem(Album, 'USA'), instrumentos(Album, L), member(electric_guitar, L).
```

## Project Structure
```text
.
├── music_catalogue.pl   # The main Prolog database containing all facts
├── queries.txt          # Example Queries          
└── README.md            # Documentation and query guide
```

## Maintainers

Maintainer:

- [@kydoa](https://github.com/kydoa)