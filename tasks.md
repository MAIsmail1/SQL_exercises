# Football Matches - Tasks

Each of the questions/tasks below can be answered using a `SELECT` query. When you find a solution copy it into the code block under the question before pushing your solution to GitHub.

1) Find all the matches from 2017.

```sql
<!-- Copy solution here -->
SELECT * FROM public.matches WHERE season = 2017;

```

2) Find all the matches featuring Barcelona.

```sql
<!-- Copy solution here -->
SELECT * FROM public.matches WHERE hometeam = 'Barcelona' OR awayteam = 'Barcelona';
```

3) What are the names of the Scottish divisions included?

```sql
<!-- Copy solution here -->
SELECT name FROM divisions where country = 'Scotland';

```

4) Find the division code for the Bundesliga. Use that code to find out how many matches Freiburg have played in the Bundesliga since the data started being collected.

```sql
<!-- Copy solution here -->
SELECT code FROM divisions WHERE name = 'Bundesliga';
SELECT COUNT(id) FROM matches WHERE division_code = 'D1' AND (hometeam ='Freiburg' OR awayteam = 'Freiburg');

```

5) Find the unique names of the teams which include the word "City" in their name (as entered in the database)

```sql
<!-- Copy solution here -->
 SELECT DISTINCT hometeam, awayteam FROM matches WHERE hometeam LIKE '%City';

```

6) How many different teams have played in matches recorded in a French division?

```sql
<!-- Copy solution here -->
SELECT COUNT(DISTINCT hometeam) FROM matches WHERE division_code = 'F1' OR division_code = 'F2';

```

7) Have Huddersfield played Swansea in the period covered?

```sql
<!-- Copy solution here -->
SELECT * FROM matches WHERE (hometeam = 'Huddersfield' AND awayteam = 'Swansea');
SELECT * FROM matches WHERE (hometeam = 'Swansea' AND awayteam = 'Huddersfield');

```

8) How many draws were there in the Eredivisie between 2010 and 2015?

```sql
<!-- Copy solution here -->
SELECT COUNT(ftr) FROM matches WHERE (ftr = 'D') AND (season >= 2010 AND season <= 2015) AND division_code = 'N1';

```

9) Select the matches played in the Premier League in order of total goals scored from highest to lowest. Where there is a tie the match with more home goals should come first.

```sql
<!-- Copy solution here -->
SELECT * FROM public.matches WHERE division_code = 'E0' ORDER BY (ftag + fthg) DESC, fthg DESC;

```

10) In which division and which season were the most goals scored?

```sql
<!-- Copy solution here -->
SELECT SUM(ftag + fthg), season, division_code FROM public.matches GROUP BY division_code, season ORDER BY SUM DESC LIMIT 1;

```

### Useful Resources

- [Filtering results](https://www.w3schools.com/sql/sql_where.asp)
- [Ordering results](https://www.w3schools.com/sql/sql_orderby.asp)
- [Grouping results](https://www.w3schools.com/sql/sql_groupby.asp)