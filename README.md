# sport.db League Quick Starter Sample - Mauritius Premier League


Create your own plain text datasets for your own league(s) from scratch
and read it all
into your SQL database of choice (e.g. SQLite, PostgreSQL, etc.)
with a single command e.g.:

```
$ sportdb build
```

Let's get started. Follow along these six steps:

- Step 1: Add all leagues
- Step 2: Add all clubs
- Step 3: Add all match fixtures and results
- Step 4: Add the league season "front matter" settings
- Step 5: Add a setups file list (also known as manifest)
- Step 6: Add a datafile build script - That's it. Done.

Using a file structure like:

```
├── 2014-15              # 2014-15 season folder
|   ├── league-i.txt     #   match fixtures / results - matchdays  1-18
|   ├── league-ii.txt    #                            - matchdays 19-36
|   └── league.yml       #   "front matter" settings
├── setups
|   └── all.txt          #   file list (manifest)
├── leagues.txt          # all leagues
├── clubs.txt            # all clubs
└── Datafile             # build script
```



## Step 1: Add all leagues

Example - [`leagues.txt`](leagues.txt):

```
mu, Mauritius Premier League
```


## Step 2: Add all clubs

The Mauritius Premier League includes ten clubs.

Example - [`clubs.txt`](clubs.txt):

```
joachim,       Cercle de Joachim|Cercle de Joachim SC|Joachim,              CDJ
chamarel,      Chamarel|Chamarel SC,                                        CHA
curepipesc,    Curepipe Starlight|Curepipe SC|Starlight,                    CUR
entente,       Entente Boulet Rouge|Entente Boulet Rouge-Riche Mare Rovers, EBR
lacure,        La Cure Sylvester|La Cure,                                   LCS
pamplemousses, Pamplemousses|Pamplemousses SC,                              PPM
petiteriv,     Petite Rivière Noire|Petite Rivière,                         PRN
aspl,          AS Port-Louis 2000|ASPL 2000,                                APL
qbornes,       AS Quatre Bornes|Quatre Bornes,                              AQB
rempart,       AS Rivière du Rempart|Rivière du Rempart,                    ARR
```

Note: Use the pipe (`|`) to list alternative names.


## Step 3: Add all match fixtures and results

Example - [`2014-15/league-i.txt`](2014-15/league-i.txt):

```
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


## Step 4: Add the league season "front matter" settings

Example - [`2014-15/league.yml`](2014-15/league.yml):

```yaml
league:   mu
season:   2014/15
start_at: 2014-11-05

fixtures:
- league-i
- league-ii

10 teams:
- Cercle de Joachim
- AS Port-Louis 2000
- Pamplemousses
- Curepipe Starlight
- Petite Rivière Noire
- Rivière du Rempart
- AS Quatre Bornes
- Chamarel SC
- La Cure Sylvester
- Entente Boulet Rouge
```


## Step 5: Add a setups file list (also known as manifest)

Example - [`setups/all.txt`](setups/all.txt):

```
mu-mauritius!/leagues
mu-mauritius!/clubs
mu-mauritius!/2014-15/league
```


## Step 6: Add a datafile build script - That's it. Done.

Example - [`Datafile`](Datafile):

```ruby
## a) Add country e.g. Mauritius

inline do
  Country.parse 'mu', 'Mauritius', 'MUS', '2_040 km²', '1_261_200'
end 

## b) Read in all football datasets in ./mu-mauritius (defaults to setups/all.txt)

football 'mu-mauritius'
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

1|joachim|Cercle de Joachim||CDJ|Cercle de Joachim SC|Joachim|1||t|||||f|
2|chamarel|Chamarel SC||CHA|Chamarel|Chamarel Sport Club|1||t|||||f|
3|curepipesc|Curepipe Starlight||CUR|Curepipe Starlight SC|1||t|||||f|
4|entente|Entente Boulet Rouge||EBR|Entente Boulet Rouge SC|Entente Boulet Rouge-Riche Mare Rovers|1||t|||||f|
5|lacure|La Cure Sylvester||LCS|La Cure Sylvester SC|La Cure|1||t|||||f|
6|pamplemousses|Pamplemousses||PPM|Pamplemousses SC|1||t|||||f|
7|petiteriv|Petite Rivière Noire||PRN|Petite Rivière Noire SC|Petite Rivière|1||t|||||f|
8|aspl|AS Port-Louis 2000||APL|ASPL 2000|Port-Louis 2000|Association Sportive Port-Louis 2000|1||t|||||f|
9|qbornes|AS Quatre Bornes||AQB|ASQB|Quatre Bornes|1||t|||||f|
10|rempart|Rivière du Rempart||ARR|AS Rivière du Rempart|1||t|||||f|
11|pointauxsables|Pointe-aux-Sables Mates||||1||t|||||f|
12|savanne|Savanne SC|||Savanne Sporting Club|1||t|||||f|
```

And so on.


## Questions? Comments?

Send them along to the
[Open Sports & Friends Forum/Mailing List](http://groups.google.com/group/opensport).
Thanks!

