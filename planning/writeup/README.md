# Project 4: Planning [![tests](../../../badges/submit-proj4/pipeline.svg)](../../../pipelines/submit-proj4/latest)

## Q1

Path length: 362.88692665140957
q1

## Q2

Radius 61
q21

Radius 122
q22

Radious 200
Path length: 362.88669499958723

## Q3

Verteces 545
Path length: 362.88692665140957

Verteces 1000
Path length: 356.3329847638013

Verteces 1200
Path length: 356.3329847638013

## Q4

```bash
lcl dwn:~/mushr_ws/src/alg_fnd_mushr/planning$ python3 scripts/run_search -m test/share/map2.txt -n 1200 -r 200 --lazy r2 -s 252 115 -g 350 350
Lazy: True
Vertices: 1200
Edges: 291082
Running A*
Path length: 356.33275311197895
Planning time: 3.12811279296875
Edges evaluated: 9386
```

q41

```bash
lcl dwn:~/mushr_ws/src/alg_fnd_mushr/planning$ python3 scripts/run_search -m test/share/map2.txt -n 1200 -r 200  r2 -s 252 115 -g 350 350
Lazy: False
Vertices: 1200
Edges: 205233
Running A*
Path length: 356.33275311197895
Planning time: 23.43128275871277
Edges evaluated: 292086
```

q42

## Q5

```bash
lcl dwn:~/mushr_ws/src/alg_fnd_mushr/planning$ python3 scripts/run_search -m test/share/map1.txt -n 25 -r 3.0 --lazy --shortcut --show-edges r2 -s 1 1 -g 7 8
Lazy: True
Vertices: 25
Edges: 51
Running A*
Path length: 12.960450156532826
Planning time: 0.003015279769897461
Edges evaluated: 14
Shortcutting A* path
Shortcut length: 12.591492106547538
Shortcut time: 0.012484073638916016
```

q51
q52
