# football.db League Quick Starter Sample - Mauritius Premier League


Create your own plain text datasets for your own league(s) from scratch
and read it all
into your SQL database of choice (e.g. SQLite, PostgreSQL, etc.)
with a single command e.g.:

```
$ sportdb build
```

Let's get started. Follow along these five steps:

- Step 1: Add all leagues
- Step 2: Add all clubs
- Step 3: Add all match fixtures and results
- Step 4: Add the league season "configuration" settings
- Step 5: Add a datafile build script - That's it. Done.

Using a file structure like:

```
mauritius
├── 2014-15                # 2014-15 season folder
|   ├── .conf.txt          #   league "configuration" settings
|   ├── 1-league-i.txt     #   match fixtures / results - matchdays  1-18 
|   └── 1-league-ii.txt    #                            - matchdays 19-36      
├── leagues.txt            # all leagues
├── clubs.txt              # all clubs
└── Datafile               # build script
```



## Step 1: Add all leagues

Example - [`leagues.txt`](leagues.txt):

```
= Mauritius =

1  Mauritius Premier League
```

Note: The datafile starts with the country heading, that is, `= ... =`
and than lists all leagues and cups on its own lines.


## Step 2: Add all clubs

Example - [`clubs.txt`](clubs.txt):

```
= Mauritius =

Cercle de Joachim | Cercle de Joachim SC | Joachim
Chamarel | Chamarel SC
Curepipe Starlight | Curepipe SC | Starlight
Entente Boulet Rouge | Entente Boulet Rouge-Riche Mare Rovers
La Cure Sylvester | La Cure
Pamplemousses | Pamplemousses SC
Petite Rivière Noire | Petite Rivière
AS Port-Louis 2000 | ASPL 2000
AS Quatre Bornes | Quatre Bornes
AS Rivière du Rempart | Rivière du Rempart
```

Note: The datafile again starts with the country heading, that is, `= ... =` and than lists
all clubs on its own lines. Use the pipe (`|`) to list alternate club names.
The Mauritius Premier League includes ten clubs.


## Step 3: Add all match fixtures and results

Example - [`2014-15/1-league-i.txt`](2014-15/1-league-i.txt):

```
= Mauritius Premier League 2014/15 =

Matchday 1
[Wed Nov/5]
  Curepipe Starlight    1-3  Petite Rivière Noire
  AS Quatre Bornes      1-0  La Cure Sylvester
  Pamplemousses         0-1  Rivière du Rempart
  AS Port-Louis 2000    5-1  Entente Boulet Rouge
  Chamarel FC           2-3  Cercle de Joachim

Matchday 2
[Sun Nov/9]
  Curepipe Starlight    2-1  AS Quatre Bornes
  Entente Boulet Rouge  1-2  Chamarel FC
  Rivière du Rempart    1-1  AS Port-Louis 2000
  La Cure Sylvester     1-2  Pamplemousses
  Petite Rivière Noire  2-0  Cercle de Joachim

Matchday 3
[Wed Nov/12]
  Chamarel FC           1-1  Rivière du Rempart
  AS Port-Louis 2000    1-0  La Cure Sylvester
  Cercle de Joachim     2-2  Entente Boulet Rouge
  Pamplemousses         0-4  Curepipe Starlight
  AS Quatre Bornes      1-2  Petite Rivière Noire


Matchday 4
[Sun Nov/16]
  Petite Rivière Noire  4-1  Entente Boulet Rouge
  Rivière du Rempart    1-1  Cercle de Joachim
  La Cure Sylvester     0-0  Chamarel FC
  Curepipe Starlight    0-0  AS Port-Louis 2000
  AS Quatre Bornes      1-0  Pamplemousses

...
```


## Step 4: Add the league season "configuration" settings

Example - [`2014-15/.conf.txt`](2014-15/.conf.txt):

```
= Mauritius Premier League 2014/15 =

Cercle de Joachim
AS Port-Louis 2000
Pamplemousses
Curepipe Starlight
Petite Rivière Noire
Rivière du Rempart
AS Quatre Bornes
Chamarel SC
La Cure Sylvester
Entente Boulet Rouge
```


## Step 5: Add a datafile build script - That's it. Done.

Example - [`Datafile`](Datafile):

```ruby
# Read in all football datasets in ./mauritius (defaults to all seasons)

football 'mauritius'
```


Now try in your working folder:

```
$ sportdb build
```

This will read in the `./Datafile` and

- setup a new single-file SQLite database e.g. `./sport.db`
- read in all plain text datasets

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

1|Mauritius|mauritius|mu|1|MUS|||1261200|2040|||f|t|f|f|

sqlite> select * from teams;

1|joachim|Cercle de Joachim||CDJ|Cercle de Joachim SC|Joachim||t|||||f|
2|chamarel|Chamarel SC||CHA|Chamarel|Chamarel Sport Club||t|||||f|
3|curepipesc|Curepipe Starlight||CUR|Curepipe Starlight SC||t|||||f|
4|entente|Entente Boulet Rouge||EBR|Entente Boulet Rouge SC|Entente Boulet Rouge-Riche Mare Rovers||t|||||f|
5|lacure|La Cure Sylvester||LCS|La Cure Sylvester SC|La Cure||t|||||f|
6|pamplemousses|Pamplemousses||PPM|Pamplemousses SC||t|||||f|
7|petiteriv|Petite Rivière Noire||PRN|Petite Rivière Noire SC|Petite Rivière||t|||||f|
8|aspl|AS Port-Louis 2000||APL|ASPL 2000|Port-Louis 2000|Association Sportive Port-Louis 2000||t|||||f|
9|qbornes|AS Quatre Bornes||AQB|ASQB|Quatre Bornes||t|||||f|
10|rempart|Rivière du Rempart||ARR|AS Rivière du Rempart||t|||||f|
11|pointauxsables|Pointe-aux-Sables Mates|||||t|||||f|
12|savanne|Savanne SC|||Savanne Sporting Club||t|||||f|
```

And so on.


## Questions? Comments?

Send them along to the
[Open Sports & Friends Forum/Mailing List](http://groups.google.com/group/opensport).
Thanks!

