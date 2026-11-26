# Smart City Route Optimization System

Finds the shortest route between locations in a city. Locations are **vertices**, roads are **weighted edges** (weight = travel time/distance). Implements and compares **Dijkstra** and **Bellman-Ford**.

## Structure
```
src/graph.py        CityGraph (adjacency list) + random city generator
src/algorithms.py   dijkstra(), bellman_ford()
src/benchmark.py    performance comparison across graph sizes
src/main.py         demo city route
tests/              pytest suite
```

## Run
```bash
python src/main.py        # demo route Airport -> Hospital
python src/benchmark.py   # timing table (+ chart if matplotlib installed)
pip install pytest && pytest
```

## Algorithms
| | Dijkstra | Bellman-Ford |
|---|---|---|
| Complexity | O((V+E) log V) | O(V·E) |
| Negative weights | No | Yes |
| Negative cycle detection | No | Yes |
| Best for | Road networks (non-negative) | Graphs with penalties/credits |

## Findings
Both return identical distances. Dijkstra scales far better as the graph grows, while Bellman-Ford slows sharply. For real road networks use Dijkstra; use Bellman-Ford only when negative weights are possible.
