# Project Documentation

Here are our proposed data types:

```mermaid
classDiagram
    class Team {
      +name : string
      +location : City
      +formedOn : date
      +active : bool
    }

    class Hero {
      +team : Team
      +name : string
      +secretIdentity : string
      +age : int
      +powers : string[]
      +damageCaused : double
    }

    class City {
      +name : string
      +population : int
    }

    Hero "*" --> "0..1" Team : Is part of
    City "1" <-- "*" Team : Based in
```

Relations:

* A **Team** can have any number of **Hero**s (including 0). Each Hero is on at most one team. There is no ownership.
  A hero can leave a team and if a team disbands the Heroes all still exist.
  * Relationship stored on Hero side
  * When a Team is deleted, Heros are updated with the **clear** policy

* A **Team** must be based in a **City**. Multiple teams can be in a City. There is no ownership.
  A Team can leave a city and the city is unaffected.
  * Relationship stored on the Team side
  * A City cannot be deleted if there are Teams in it
