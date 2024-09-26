# football.db League Quick Starter Sample - Mauritius Premier League


Create your own datasets in plain text for your own league(s) from scratch
and read it all
into your SQL database of choice (e.g. SQLite, PostgreSQL, etc.)
with a single command e.g.:

```
$ sportdb build
```

Let's get started. Follow along these steps:

- Step 1: Add all match fixtures and results
- Let's build. That's it. Done.

Using a file structure like:

```
mauritius
└── 2014-15                # 2014-15 season folder
    ├── 1-league-i.txt     #   match fixtures / results - matchdays  1-18
    └── 1-league-ii.txt    #                            - matchdays 19-36
```


## Step 1: Add all match fixtures and results

Example - [`2014-15/1-league-i.txt`](2014-15/1-league-i.txt):

```
= Mauritius Premier League 2014/15 =

Matchday 1
[Wed Nov/5]
  Curepipe Starlight    1-3  Petite Rivière Noire
  AS Quatre Bornes      1-0  La Cure Sylvester
  Pamplemousses         0-1  Rivière du Rempart
  AS Port-Louis 2000    5-1  Entente Boulet Rouge
  Chamarel SC           2-3  Cercle de Joachim

Matchday 2
[Sun Nov/9]
  Curepipe Starlight    2-1  AS Quatre Bornes
  Entente Boulet Rouge  1-2  Chamarel SC
  Rivière du Rempart    1-1  AS Port-Louis 2000
  La Cure Sylvester     1-2  Pamplemousses
  Petite Rivière Noire  2-0  Cercle de Joachim

Matchday 3
[Wed Nov/12]
  Chamarel SC           1-1  Rivière du Rempart
  AS Port-Louis 2000    1-0  La Cure Sylvester
  Cercle de Joachim     2-2  Entente Boulet Rouge
  Pamplemousses         0-4  Curepipe Starlight
  AS Quatre Bornes      1-2  Petite Rivière Noire


Matchday 4
[Sun Nov/16]
  Petite Rivière Noire  4-1  Entente Boulet Rouge
  Rivière du Rempart    1-1  Cercle de Joachim
  La Cure Sylvester     0-0  Chamarel SC
  Curepipe Starlight    0-0  AS Port-Louis 2000
  AS Quatre Bornes      1-0  Pamplemousses

...
```


## Let's build. That's it. Done.

Now try in your working folder:

```
$ sportdb build
```

This will run the build script and

- setup a new single-file SQLite database e.g. `./sport.db` from scratch (zero)
- read in all datasets in plain text

That's it. Try:

```
$ sqlite3 sport.db

SQLite version 3.7.16
Enter ".help" for instructions
Enter SQL statements terminated with a ";"

sqlite> .tables

alltime_standing_entries  events_grounds            names
alltime_standings         events_teams              parts
assocs                    games                     persons
assocs_assocs             goals                     places
badges                    grounds                   props
cities                    group_standing_entries    rosters
continents                group_standings           rounds
counties                  groups                    seasons
countries                 groups_teams              states
country_codes             langs                     taggings
districts                 leagues                   tags
event_standing_entries    logs                      teams
event_standings           metros                    usages
events                    munis                     zones

sqlite> select * from countries;

1|mu|Mauritius|MRI|...

sqlite> select * from leagues;

1|mu_premierleague|Premier League|...
2|mu_cup|Cup|...

sqlite> select * from teams;

 1|Curepipe Starlight|...
 2|Petite Rivière Noire|...
 3|AS Quatre Bornes|..
 4|La Cure Sylvester|...
 5|Pamplemousses|...
 6|Rivière du Rempart|...
 7|AS Port-Louis 2000|...
 8|Entente Boulet Rouge|...
 9|Chamarel SC|...
10|Cercle de Joachim|...
11|Pointe-aux-Sables Mates|...
12|Savanne SC|...

sqlite> select * from events;

1|mu_premierleague.2014/15|...
2|mu_cup.2015|...

sqlite> select * from matches;
...
```

And so on.




Note - The latest sportdb update / machinery comes pre-configured with many built-in football leagues (& cups)
from around the world, see [`/leagues`](https://github.com/openfootball/leagues).

If you want to add more football league(s), you are more than welcome
to open a ticket/issue.



## Questions? Comments?

Yes, you can. More than welcome.
See [Help & Support »](https://github.com/openfootball/help)

