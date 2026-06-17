# SQL QUEST

A timed, arcade-style SQL practice game built for retention. Write real queries, race the clock, and keep your heart system intact across 8 progressive challenges.

## What is SQL Quest?

SQL Quest is a **browser-based SQL drill** that turns query practice into a competitive game. Instead of passive flashcards or boring problem sets, you type actual SQL against a live schema, get instant feedback on syntax and structure, and build streaks by nailing consecutive correct answers.

Perfect for students who just finished a database course and want to *retain* what they learned—or anyone grinding SQL fundamentals before an interview.

## Features

- **Free-form SQL input** — type real queries, no multiple choice.
- **Progressive difficulty** — Easy tier (SELECT, WHERE, ORDER BY) → Medium tier (GROUP BY, HAVING, JOINs, subqueries).
- **Timed challenges** — 90 seconds per question. Time runs out? You lose a heart and see the answer.
- **Hearts system** — 3 hearts per run. Missing a clause = 1 heart. Typo / syntax slip = ½ heart. 0 hearts = back to Level 1.
- **Scoring** — base points + time bonus (faster = more) + difficulty multiplier (Medium = 1.5×). Misses cost 25 pts and break your streak.
- **Continue button** — no auto-skip. Study the answer, then click Continue when you're ready to move on.
- **Persistent stats** — high score, best streak, total clears tracked in browser storage.
- **Unique run codes** — `SQLQ-XXXX` generated for each playthrough—shareable proof of your score.
- **Case-sensitive validation** — keywords must be UPPERCASE, identifiers lowercase, queries end with `;`. Details matter.
- **Table-based schema view** — employees, departments, customers, orders with exact column names and types (INT, VARCHAR, DECIMAL, DATE).

## Quick Start

1. Download **sql-quest.html** and open it in any modern browser.
2. Click **▶ Start Run** on the home screen.
3. Type your SQL into the query console.
4. Hit **Run query** (or Ctrl+Enter) to submit.
5. Get instant feedback—correct = points and move on; wrong = lose a heart (or ½) and retry.
6. Clear both tiers to finish the run and lock in your score.

**That's it.** No build, no dependencies, no login. Just SQL.

---

## Game Mechanics

### Questions (8 Total)

**Easy Tier (4 questions, 1× multiplier, 90s each)**
1. SELECT * — all columns, all rows
2. SELECT specific columns from a table
3. WHERE filtering with exact match
4. ORDER BY with DESC direction

**Medium Tier (4 questions, 1.5× multiplier, 90s each)**
1. GROUP BY + COUNT aggregates
2. GROUP BY + HAVING filter on aggregates
3. JOIN across two tables
4. Subquery with IN

### Hearts

- **3 hearts per run.**
- **Full heart lost (−1)** = missing a whole clause (no WHERE when needed, no JOIN, no GROUP BY, etc.) or timeout.
- **Half heart lost (−0.5)** = detail slip: typo in a keyword, wrong column name, forgot the semicolon, or keyword/identifier case wrong.
- **0 hearts** = run over, back to Level 1.

### Scoring

- **Base**: 100 pts per Easy question, 150 pts per Medium (1.5× multiplier).
- **Time bonus**: remaining seconds × 2 (Easy) or × 3 (Medium).
- **Penalties**: −25 pts per miss (but streak breaks, too).
- **High score tracked** — best run saved in browser storage.

### Streak

Increments for each correct answer. Resets to 0 on any miss. Your current streak and best streak are displayed.

---

## Validation & Syntax Rules

The game uses **pattern matching** to validate answers. Your query must include:

1. **All required clauses** (structural correctness).
2. **Exact column / table names** from the schema (case-sensitive: `employees`, not `EMPLOYEES`).
3. **Keywords in UPPERCASE** (SELECT, FROM, WHERE, etc., not select, from).
4. **Trailing semicolon** (queries end with `;`).

Examples:
- ✓ `SELECT name FROM employees;` — correct case, semicolon, exact identifiers.
- ✗ `select name from employees` — lowercase SELECT, missing semicolon = ½ heart.
- ✗ `SELECT name FROM Employees;` — wrong case on table name = ½ heart.
- ✗ `SELECT name FROM employees WHERE department = 'HR'` — missing semicolon = ½ heart.

**Tip:** Open **▸ show schema** on any question to see the exact column names and types. Never guess.

---

## Schema

The game comes with 4 sample tables:

| Table | Columns |
|-------|---------|
| **employees** | emp_id (INT), name (VARCHAR), department (VARCHAR), salary (DECIMAL), hire_date (DATE) |
| **departments** | dept_name (VARCHAR), location (VARCHAR), budget (DECIMAL) |
| **customers** | cust_id (INT), name (VARCHAR), city (VARCHAR), signup_date (DATE) |
| **orders** | order_id (INT), cust_id (INT), amount (DECIMAL), order_date (DATE) |

---

## Technical Details

- **Single HTML file** — no build, no npm, no backend.
- **Vanilla JavaScript** — no frameworks.
- **Client-side storage** — browser localStorage persists your stats.
- **Dark mode UI** — phosphor-inspired arcade console with CRT scanline ambiance.
- **Pattern-matching validation** — checks for required keywords and clause structure; not full SQL execution (so some equivalent phrasings may not match).

---

## Roadmap

- [ ] **Random topic generator** — procedurally generate new questions beyond the base 8.
- [ ] **Custom question upload** — load your own questions from course notes or study materials.
- [ ] **Leaderboard** — share scores and compete with friends.
- [ ] **SQL execution engine** — validate queries against real in-memory databases (sql.js) for stricter correctness.
- [ ] **Hint system** — optional guided feedback per question.

---

## Who Built This?

SQL Quest was built as a **one-hour alpha** for hands-on SQL retention following an Advanced Database Programming course. Designed by and for people who want practice that *sticks*—not passive review.

---

## License

MIT — do whatever you want with it.

---

## Feedback?

Found a question that's too strict or too loose? Think a validation rule is unfair? Open an issue or fork and improve it.

**Happy querying.** ✓
