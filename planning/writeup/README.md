# Project 4: Planning [![tests](../../../badges/submit-proj4/pipeline.svg)](../../../pipelines/submit-proj4/latest)

## Q1

![Shortest A*](q1.png)

`Path length: 362.88692665140957`

## Q2

### Radius 61

```bash
Path length: 363.068415217045   
Planning time: 0.5983076095581055
Edges evaluated: 9231
```

![placeholder](q21.png)

### Radius 122

```bash
Path length: 362.88692665140957
Planning time: 2.3131773471832275
Edges evaluated: 32820
```

![placeholder](q22.png)

### Radious 200

```bash
Path length: 362.88669499958723
Planning time: 6.023391962051392
Edges evaluated: 73204
```

![placeholder](q23.png)

### Summary

Increasing the connection radius techinically produced slightly shorter paths. However this came at the cost of exponentially higher planning time and many more edge evaluations.

## Q3

### Verteces 545

```bash
Path length: 362.88692665140957
Planning time: 1.2819221019744873
Edges evaluated: 18837
```

![placeholder](q31.png)

### Verteces 1000

```bash
Path length: 356.3329847638013
Planning time: 4.282504081726074
Edges evaluated: 63705
```

![placeholder](q32.png)

### Verteces 1200

```bash
Path length: 356.3329847638013
Planning time: 6.295160531997681
Edges evaluated: 92124
```

![placeholder](q33.png)

### Summary

With the fixed radius 100, increasing the number of vertices did realistically improves path quality, up to a certain point(around 1000). This also increased planning time due to a larger roadmap and more edge evaluations.

## Q4

### Lazy A*

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

![placeholder](q41.png)

### A*

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

![placeholder](q42.png)

### Summary

As is seen in the results, the Lazy A* algorithm produces the same path but significantly faster. It only evaluated 3% of A* original verteces causing a speedup of 8.

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

### Planning

![placeholder](q51.png)

`Planning time: 0.003015279769897461`

### Shortcutting

![placeholder](q52.png)

`Shortcut time: 0.012484073638916016`

### Differences

The shortcut calculation does add significantly more time complexity. However the actual time difference is rather minimal. The quality of the path does decrease the total length but not by much 12.96 vs 12.59. While the edges created via shortuctting are techincally non colliding, the path from sampled edges does provide more leeway from hitting the obstacle, and has significanly more shallow curves. These are preffered metrics for a robot. 

## Q6

### c = 3

![placeholder](q61.png)

`Path length: 16.086911525242698`

### c = 4.5

![placeholder](q62.png)

`Path length: 14.77307984701639`

### c = 9

![placeholder](q63.png)

`Path length: 13.606245510056146`

### c = 15

![placeholder](q63.png)

`Path length: 13.20596227969313`

### Differences

As we can see the increasing curvature drastically reduces the turning radius. Increasing c makes it closer to the closed form, straight edge solution.  

## Q7

Κ = tan(δ)/L
δ = 0.34, L = 0.33
tan(0.34) ≈ 0.35
0.35/0.34≈1.06m

## Q8

```bash
roslaunch planning planner_sim.launch map:='$(find cse478)/maps/maze_0.yaml' num_vertices:=1000 connection_radius:=10 curvature:=1
```

![placeholder](q71.png)

## Q9

```bash
roslaunch planning planner_sim.launch map:='$(find cse478)/maps/cse2_2.yaml' num_vertices:=1500 connection_radius:=10 curvature:=1 initial_x:=16 initial_y:=28
```

![placeholder](q81.png)

## Q10

I did not change my motion models paramaters.
