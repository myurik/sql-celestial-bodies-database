# sql-celestial-bodies-database

PostgreSQL database modeling the universe: galaxies, stars, planets, moons and comets.
Built as a project for the **freeCodeCamp Relational Database** certification.

## Schema

| Table    | Description                         | Relationship                  |
|----------|-------------------------------------|-------------------------------|
| `galaxy` | Galaxies (type, age, distance)      | -                             |
| `star`   | Stars (age, distance, shape)        | belongs to a `galaxy`         |
| `planet` | Planets (type, diameter, has life)  | orbits a `star`               |
| `moon`   | Moons (diameter, shape)             | orbits a `planet`             |
| `comet`  | Comets (orbital period, discovery)  | -                             |

## Concepts practiced

- `CREATE DATABASE` / `CREATE TABLE`
- `SERIAL` primary keys and `FOREIGN KEY ... REFERENCES`
- `NOT NULL` and `UNIQUE` constraints
- Data types: `INT`, `NUMERIC`, `VARCHAR`, `TEXT`, `BOOLEAN`
- `INSERT` of sample data (6 galaxies, 6 stars, 12 planets, 23 moons, 4 comets)
- Database dump with `pg_dump`

## How to restore

```bash
psql -U postgres < universe.sql
```

This recreates the `universe` database with all tables and data.

## Example query

```sql
SELECT m.name AS moon, p.name AS planet
FROM moon m
JOIN planet p ON m.planet_id = p.planet_id
ORDER BY p.name, m.name;
```
