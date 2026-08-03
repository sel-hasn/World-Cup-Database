# 🏆 World Cup Database

A PostgreSQL database project built as part of the **freeCodeCamp Relational Database Certification**.

This project creates a relational database containing World Cup tournament match data from the final three rounds of the 2014 and 2018 tournaments. The data is imported from a CSV file using Bash scripting, stored in PostgreSQL, and queried to generate useful tournament statistics.

---

## 📌 Project Overview

This project consists of three main parts:

### 1. Database Creation
- Create a PostgreSQL database named `worldcup`
- Create relational tables for teams and games
- Define primary keys and foreign key relationships

### 2. Data Import
- Read match data from `games.csv`
- Insert unique teams into the `teams` table
- Insert match results into the `games` table
- Retrieve team IDs dynamically instead of hard-coding values

### 3. Database Queries
- Execute SQL queries to retrieve tournament statistics
- Analyze goals, teams, champions, and match results

---

## 📂 Project Structure

```text
World-Cup-Database/
│
├── games.csv          # World Cup match data
├── insert_data.sh     # Bash script to import CSV data
├── queries.sh         # Bash script containing SQL queries
├── worldcup.sql       # Database dump file
└── README.md          # Project documentation
```

---

## 🛠 Technologies Used

- PostgreSQL
- SQL
- Bash scripting
- Linux command line

---

## 🗄 Database Schema

### Teams Table

Stores all unique teams participating in the tournament.

| Column | Data Type | Constraints |
|--------|-----------|-------------|
| `team_id` | SERIAL | Primary Key |
| `name` | VARCHAR(50) | UNIQUE, NOT NULL |

---

### Games Table

Stores each match and connects teams using foreign keys.

| Column | Data Type | Constraints |
|--------|-----------|-------------|
| `game_id` | SERIAL | Primary Key |
| `year` | INT | NOT NULL |
| `round` | VARCHAR(50) | NOT NULL |
| `winner_id` | INT | Foreign Key → `teams(team_id)` |
| `opponent_id` | INT | Foreign Key → `teams(team_id)` |
| `winner_goals` | INT | NOT NULL |
| `opponent_goals` | INT | NOT NULL |

---

## 🚀 Installation and Usage

### Clone the repository

```bash
git clone https://github.com/sel-hasn/World-Cup-Database.git

cd World-Cup-Database
```

---

### Create the database

Restore the database using the SQL dump file:

```bash
psql -U postgres < worldcup.sql
```

---

### Import the data

Make the script executable:

```bash
chmod +x insert_data.sh
```

Run the import script:

```bash
./insert_data.sh
```

The script will:

- Insert 24 unique teams
- Insert 32 World Cup matches
- Create correct relationships between games and teams

---

### Run database queries

Make the query script executable:

```bash
chmod +x queries.sh
```

Run:

```bash
./queries.sh
```

---

## 📊 Example Queries

The project includes SQL queries to find:

- Total goals scored by winning teams
- Total goals scored by both teams
- Average goals per game
- Highest number of goals scored in a single game
- Games where winners scored more than two goals
- The 2018 World Cup champion
- Teams that played in the 2014 Eighth-Final round
- Champions by tournament year
- Teams starting with a specific name pattern

---

## 📚 Skills Demonstrated

Through this project, I practiced:

- Relational database design
- PostgreSQL database management
- Creating tables and relationships
- Primary keys and foreign keys
- Database normalization
- SQL JOIN operations
- Aggregate functions:
  - `SUM()`
  - `AVG()`
  - `COUNT()`
  - `MAX()`
- Bash scripting
- Reading CSV files
- Automating database operations

---

## 🎓 Certification

This project was completed as part of the:

**freeCodeCamp Relational Database Certification**

---

## 👤 Author

**sel-hasn**

GitHub:  
https://github.com/sel-hasn

---

## 📄 License

This project is licensed under the MIT License.
