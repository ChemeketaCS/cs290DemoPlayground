# Project Documentation

Here are our proposed data types:

```mermaid
classDiagram
    class Team {
      +Hero[] heros
      +string name
      +string city
      +date formedOn
      +bool active
    }

    class Hero {
      +Team team
      +string name
      +string secretIdentity
      +int age
      +string[] powers
      +double damageCaused
    }

    Hero "*" --> "0..1" Team : Is part of
```

Relations:

* A **Team** can have any number of **Hero**s (including 0). Each Hero is on at most one team. There is no ownership.
  A hero can leave a team and if a team disbands the Heroes all still exist.
