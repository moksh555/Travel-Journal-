# Travel Journal - Family Travel Tracker

An interactive travel tracking web application built with Node.js, Express, EJS, and PostgreSQL. The app renders a full SVG world map and lets multiple family members each track which countries they have visited, with each person's visited countries highlighted in their chosen color.

## Key Features

- **Interactive SVG World Map** - Full world map rendered with individual SVG paths for every country; visited countries are highlighted in each user's chosen color
- **Multi-user Support** - Create multiple family member profiles, each with a unique display name and a custom color (red, green, yellow, olive, orange, teal, blue, violet, purple, or pink)
- **Country Visit Tracking** - Type a country name to add it to the active user's visited list; invalid entries display an inline error message via EJS locals
- **Tab-based User Switching** - Switch between family members using a tab-style form; each tab is styled with the member's chosen color
- **PostgreSQL Persistence** - User profiles and visited countries stored in relational tables with a foreign-key relationship
- **Add Family Member Flow** - Dedicated new.ejs page for adding a new family member with name and color picker

## Tech Stack

| Layer | Technologies |
|---|---|
| Runtime | Node.js |
| Framework | Express.js |
| Templating | EJS |
| Database | PostgreSQL (via pg client) |
| Middleware | body-parser |

## Database Schema

```sql
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name VARCHAR(15) UNIQUE NOT NULL,
  color VARCHAR(15)
);

CREATE TABLE visited_countries (
  id SERIAL PRIMARY KEY,
  country_code CHAR(2) NOT NULL,
  user_id INTEGER REFERENCES users(id)
);
```

## Setup and Installation

Prerequisites: Node.js 18+ and PostgreSQL installed and running locally.

1. Clone the repository:
   ```bash
   git clone https://github.com/moksh555/Travel-Journal-.git
   cd Travel-Journal-
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Create the database and tables using the schema above (or run the provided queries.sql file).
4. Update the PostgreSQL credentials in index.js to match your local setup.
5. Start the server:
   ```bash
   node index.js
   ```
6. Open http://localhost:3000 in your browser.

## Usage

- The home page displays the world map with currently visited countries highlighted
- Click a family member's tab to switch the active user and see their visited countries
- Type a country name in the input field and click Add to mark it as visited
- Click "Add Family Member" to create a new profile with a name and color
