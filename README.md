# football.db League Quick Starter Sample - Mauritius Premier League

Yes, you can - create your own plain text datasets in the Football.TXT format
for your own league(s) from scratch
and read it all
into your SQL database with a single command e.g.:


```
$ fbtxt2sqlite  mauritius.db  .
```

or convert to .JSON  (with fbtxt2json) or .CSV (with fbtxt2csv).




Let's get started. Follow along these steps:

- Step 1: Add all match fixtures and results in the Football.TXT format
- Let's build. That's it. Done.

Using a file structure like:

```
mauritius/
└── 2014-15/                # 2014-15 season folder
    ├── 1-league-i.txt      #   match fixtures / results - matchdays  1-18
    └── 1-league-ii.txt     #                            - matchdays 19-36
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



---

### Tip - Step 0 - fbtxt2sqlite Installation via Gems (Package Manager)

To install the fbtxt2sqlite command-line tool use the gems command-line tool, that is, ruby's package manager. Type:

     $ gem install fbtxt2sqlite


To check-up on the installation try:

     $ fbtxt2sqlite -h        # or
     $ fbtxt2sqlite --help

resulting in:

```
Usage: fbtxt2sqlite [options] DBPATH PATH
        --verbose, --debug           turn on verbose / debug output (default: false)
        --seasons SEASONS            turn on processing only seasons (default: false)
```

---




Now try in your working folder:

```
$ fbtxt2sqlite mauritius.db .
```

This will run the build machinery and

- setup a new single-file SQLite database e.g. `./mauritius.db` from scratch (zero)
- read in all plain text datasets in the Football.TXT format in the working directory e.g. `./`


That's it. Try:

```
$ sqlite3 mauritius.db

SQLite version 3.7.16
Enter ".help" for instructions
Enter SQL statements terminated with a ";"


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




## Tips & Tricks

### More Formats

You can use the [`fbtxt2json` command-line tool](https://github.com/sportdb/footty/tree/master/fbtxt2json) to convert any file in the Football.TXT format to JSON.

Let's try to convert the Mauritus Premier League 2014/15
in the Football.TXT format (see [`2014-15/1-league-i.txt`](2014-15/1-league-i.txt) and
[`2014-15/1-league-ii.txt`](2014-15/1-league-ii.txt)
) to JSON:

```
$ fbtxt2json 2014-15/1-league-i.txt 2014-15/1-league-ii.txt -o mu.1.json
```

Resulting in:

```json
{
  "name": "Mauritius Premier League 2014/15",
  "matches": [
    {
      "round": "Matchday 1",
      "date": "2014-11-05",
      "team1": "Curepipe Starlight",
      "team2": "Petite Rivière Noire",
      "score": { "ft": [1,3] }
    },
    {
      "round": "Matchday 1",
      "date": "2014-11-05",
      "team1": "AS Quatre Bornes",
      "team2": "La Cure Sylvester",
      "score": { "ft": [1,0] }
    },
    // ...
  ]
}
```

or convert all datasets all-at-once by passing in the directory:

```
$ fbtxt2json .
```

resulting in:

```
mauritius/
└── 2014-15/            
    ├── 1-league-i.json
    └── 1-league-ii.json

```

For an all-in-one .CSV datafile 
use the `fbtxt2csv` command-line tool. 
Try:

```
$ fbtxt2csv ./ -o mauritius.csv
```

resulting in:

``` csv
League,Date,Team 1,Team 2,FT,ET,P,Round,Status
Mauritius Premier League 2014/15,2014-11-05,Curepipe Starlight,Petite Rivière Noire,1-3,,,Matchday 1,
Mauritius Premier League 2014/15,2014-11-05,AS Quatre Bornes,La Cure Sylvester,1-0,,,Matchday 1,
Mauritius Premier League 2014/15,2014-11-05,Pamplemousses,Rivière du Rempart,0-1,,,Matchday 1,
Mauritius Premier League 2014/15,2014-11-05,AS Port-Louis 2000,Entente Boulet Rouge,5-1,,,Matchday 1,
Mauritius Premier League 2014/15,2014-11-05,Chamarel SC,Cercle de Joachim,2-3,,,Matchday 1,
Mauritius Premier League 2014/15,2014-11-09,Curepipe Starlight,AS Quatre Bornes,2-1,,,Matchday 2,
Mauritius Premier League 2014/15,2014-11-09,Entente Boulet Rouge,Chamarel SC,1-2,,,Matchday 2,
Mauritius Premier League 2014/15,2014-11-09,Rivière du Rempart,AS Port-Louis 2000,1-1,,,Matchday 2,
Mauritius Premier League 2014/15,2014-11-09,La Cure Sylvester,Pamplemousses,1-2,,,Matchday 2,
# ...
```





### Debugging & Troubleshooting

You can use the `fbtok` command-line tool shipping with the sportdb machinery to check-up on the Football.TXT tokenizer / tokens.

Let's try the Mauritus Republic Cup 2024
(see [2024/republic-cup.txt](2024/republic-cup.txt)):

```
$ fbtok 2024/republic-cup.txt
```

Resulting in:

```
line >Round 1<
[[:round, "Round 1"]]

line >[Apr 28]<
[[:date, "Apr 28", {:m=>4, :d=>28}]]

line >Cercle de Joachim            3-2  EBRRMR<
[[:team, "Cercle de Joachim"], [:score, "3-2", {:ft=>[3, 2]}], [:team, "EBRRMR"]]

line >Chebel Citizens              2-0  ASPL 2000<
[[:team, "Chebel Citizens"], [:score, "2-0", {:ft=>[2, 0]}], [:team, "ASPL 2000"]]

line >Quarterfinals<
[[:round, "Quarterfinals"]]

line >[May 8]<
[[:date, "May 8", {:m=>5, :d=>8}]]

line >Savanne                      2-1  Chebel Citizens<
[[:team, "Savanne"], [:score, "2-1", {:ft=>[2, 1]}], [:team, "Chebel Citizens"]]

...

line >Final<
[[:round, "Final"]]

line >[Jul 27]<
[[:date, "Jul 27", {:m=>7, :d=>27}]]

line >Cercle de Joachim            1-0   AS Rivière du Rempart<
[[:team, "Cercle de Joachim"], [:score, "1-0", {:ft=>[1, 0]}], [:team, "AS Rivière du Rempart"]]

OK   no parse errors found
```



## Questions? Comments?

Yes, you can. More than welcome.
See [Help & Support »](https://github.com/openfootball/help)


