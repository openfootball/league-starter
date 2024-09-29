# Notes

## Mauritius Premier League 2014/15

- see [mpfl.mu](http:www.mpfl.mu)
- see RSSSF [mauri2015](http://rsssf.com/tablesm/mauri2015.html)
- see Wikipedia
    - [Mauritian League](https://en.wikipedia.org/wiki/Mauritian_League)
    - [Championnat de Maurice de football 2014-2015 [fr]](https://fr.wikipedia.org/wiki/Championnat_de_Maurice_de_football_2014-2015)
- start_at: 2014-11-5 !!!!
- 10 teams
- corrections -- note: for standings table (checksum) add point (pts) corrections
  - Curepipe Starlight:   -1 points
  - Petite Rivière Noire: -1 points
  - Rivière du Rempart:   -2 points
  - AS Quatre Bornes:     -1 points


## Mauritius Football Association (MFA) Cup 2015


## National Super League 2023-2024
- see RSSSF [mauri2024](http://rsssf.com/tablesm/mauri2024.html)
- see wikipedia
  - <https://fr.wikipedia.org/wiki/Championnat_de_Maurice_de_football_2023-2024>
- Édition	79e
- Date	du 1er février 2024 au 1er juin 2024
- Participants	10



## More

Final League Standings 2014/15

```
Rnk    Team                 Pld   W   D   L  GF   GA  +/-  Pts
  1    Cercle de Joachim     36  22   9   5  62   24   38   75
  2    AS Port-Louis 2000    36  21  10   5  67   30   37   73
  3    Pamplemousses         36  18   5  13  56   42   14   59
  4    Curepipe Starlight    36  17   7  12  59   52    7   57
  5    Petite Rivière Noire  36  18   3  15  53   46    7   56
  6    Rivière du Rempart    36  11  12  13  51   53   -2   43
  7    AS Quatre Bornes      36  10   9  17  30   42  -12   38
  8    Chamarel SC           36   9   8  19  40   65  -25   35
  9    La Cure Sylvester     36   8  10  18  38   51  -13   34
 10    Entente Boulet Rouge  36   5   9  22  52  103  -51   24
```

(source: fifa)


```
       Team                          Pld    W    GD   Pts
  1    Cercle de Joachim              36   22    38    75
  2    AS Port-Louis 2000             36   21    37    73
  3    Pamplemousses                  36   18    14    59
  4    Curepipe Starlight*            36   17     7    57
  5    Petite Rivière Noire*          36   18     7    56
  6    Rivière du Rempart**           36   11    -2    43
  7    AS Quatre Bornes*              36   10   -12    38
  8    Chamarel SC                    36    9   -25    35
  9    La Cure Sylvester              36    8   -13    34
 10    Entente B.R/Riche-Mare Rovers  36    5   -51    24
```

```
Corrections:

    Curepipe Starlight:   -1 points
    Petite Rivière Noire: -1 points
    Rivière du Rempart:   -2 points
    AS Quatre Bornes:     -1 points
```

(source: mpfl)

To do: double check standings table with own calculation after import
Note: check for corrections (minus points for some clubs)


```
 1  Cercle de Joachim                      36  22  9  5   62-24  75  Champions
 2  AS Port-Louis 2000                     36  21 10  5   67-30  73
 3  Pamplemousses                          36  18  5 13   56-42  59
 4  Curepipe Starlight                     36  17  7 12   59-52  57  [-1]
 5  Petite Rivière Noire                   36  18  3 15   53-46  56  [-1]
 6  Rivière du Rempart                     36  11 12 13   51-53  43  [-2]
 7  AS Quatre-Bornes                       36  10  9 17   30-42  38  [-1]
 8  Chamarel SC                            36   9  8 19   40-65  35
 ------------------------------------------------------------------
 9  La Cure Sylvester                      36   8 10 18   38-51  34  Relegated
10  Entente Boulet Rouge-Riche Mare Rovers 36   5  9 22  52-103  24  Relegated

Note: Curepipe Starlight, Petite Rivière Noire and AS Quatre-Bornes 1 point deducted;
      Rivière du Rempart 2 points deducted
```

(source: rsssf)


## Todos

### 3-1 pen

```
Rivière du Rempart           3-1 pen (1-1) La Cure Sylvester
```

allow and change to

```
Rivière du Rempart           1-1  La Cure Sylvester   [3-1 pen]
```


### Misc

improve support for  abd, awd, replay e.g.

```
Cercle de Joachim            abd Rivière du Rempart           [abandoned at 0-0 in 5' due to bad weather]
Cercle de Joachim            2-1 Rivière du Rempart           [replay]

Cercle de Joachim            abd ASPL 2000                    [abandoned in 24' due to bad weather]
Cercle de Joachim            2-0 ASPL 2000                    [replay]

ASPL 2000                    awd Chamarel                     [awarded 3-0, originally 2-2]
ASPL 2000                    awd Rivière du Rempart           [awarded 3-0; originally 2-0]
Pamplemousses                awd La Cure Sylvester            [awarded 3-0; originally 1-3, La Cure Sylvester fielded ineligible players]
```


double check matches with status - change syntax/format - why? why not?

```
  Cercle de Joachim      -   AS Port-Louis 2000    [abandoned in 24' due to bad weather]
  Cercle de Joachim     2-0  AS Port-Louis 2000    [replay]
  Pamplemousses         3-0  La Cure Sylvester      [awarded; originally 1-3, La Cure Sylvester fielded ineligible players]
  AS Port-Louis 2000    3-0  Rivière du Rempart     [awarded; originally 2-0]
  Chamarel SC           0-3  AS Port-Louis 2000     [awarded; originally 2-2]
  Cercle de Joachim      -  Rivière du Rempart    [abandoned at 0-0 in 5' due to bad weather]
  Cercle de Joachim     2-1  Rivière du Rempart   [replay]
  ASPL 2000                    3-0  GRSE Wanderers    [awarded]
  Pamplemousses                 -   Savanne              [abandoned in 10' due to unplayable pitch]
  Pamplemousses                5-3  Savanne  [replay]
  Cercle de Joachim         7-6 pen (0-0)  AS Vacoas-Phoenix   [annulled because no extra time was played]
  Cercle de Joachim            3-2 aet  AS Vacoas-Phoenix     [replay]
```

