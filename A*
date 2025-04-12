from queue import PriorityQueue

# 1. Graph structure
graph = {
    "Shapla Garden Appartment": [("Boshiruddin Road", 0.35), ("Lal Fokir mazar Road", 0.14)],
    "Boshiruddin Road": [("Shapla Garden Appartment", 0.35), ("Comfort Hospital Mor", 0.21), ("Kolabagan Bus Stand", 0.5)],
    "Comfort Hospital Mor": [("Boshiruddin Road", 0.21), ("Panthapath Signal", 0.24)],
    "Kolabagan Bus Stand": [("Boshiruddin Road", 0.5), ("Dhanmondi 32 Mirpur Road", 0.35)],
    "Dhanmondi 32 Mirpur Road": [("Kolabagan Bus Stand", 0.35), ("Sonsod Bhobon Manik Mia Avinue", 0.8), ("Panthapath Signal", 1.1)],
    "Sonsod Bhobon Manik Mia Avinue": [("Dhanmondi 32 Mirpur Road", 0.8), ("Khamarbari Mor", 0.95)],
    "Khamarbari Mor": [("Sonsod Bhobon Manik Mia Avinue", 0.95), ("Farmgate Bus Stand", 0.8)],
    "Farmgate Bus Stand": [("Khamarbari Mor", 0.8), ("UAP", 0.55)],
    "Panthapath Signal": [("Comfort Hospital Mor", 0.24), ("Dhanmondi 32 Mirpur Road", 1.1), ("Shomorita Hospital", 0.26), ("UAP", 0.5)],
    "Shomorita Hospital": [("Panthapath Signal", 0.26), ("Nazneen School, Razabazar", 0.5), ("Lal Fokir mazar Road", 0.35)],
    "Nazneen School, Razabazar": [("Shomorita Hospital", 0.5), ("UAP", 0.6)],
    "Lal Fokir mazar Road": [("Shapla Garden Appartment", 0.14), ("Shomorita Hospital", 0.35)],
    "UAP": [("Panthapath Signal", 0.5), ("Farmgate Bus Stand", 0.55), ("Nazneen School, Razabazar", 0.6)]
}

# 2. Heuristic values
heuristics = {
    "Shapla Garden Appartment": 1,
    "Boshiruddin Road": 1,
    "Comfort Hospital Mor": 1,
    "Kolabagan Bus Stand": 1,
    "Dhanmondi 32 Mirpur Road": 1,
    "Sonsod Bhobon Manik Mia Avinue": 1,
    "Khamarbari Mor": 1,
    "Farmgate Bus Stand": 1,
    "Panthapath Signal": 1,
    "Shomorita Hospital": 1,
    "Nazneen School, Razabazar": 1,
    "Lal Fokir mazar Road": 5,
    "UAP": 0
}

# 3. A* Algorithm with optimal cost return
def a_star(graph, heuristics, start, goal):
    open_set = PriorityQueue()
    open_set.put((heuristics[start], 0, start))  # (f = g + h, g, node)
    came_from = {}
    cost_so_far = {start: 0}

    while not open_set.empty():
        _, g, current = open_set.get()

        if current == goal:
            # Reconstruct path
            path = []
            while current in came_from:
                path.append(current)
                current = came_from[current]
            path.append(start)
            path.reverse()
            total_cost = cost_so_far[goal]
            return path, total_cost

        for neighbor, distance in graph.get(current, []):
            new_cost = g + distance
            if neighbor not in cost_so_far or new_cost < cost_so_far[neighbor]:
                cost_so_far[neighbor] = new_cost
                priority = new_cost + heuristics.get(neighbor, float('inf'))
                open_set.put((priority, new_cost, neighbor))
                came_from[neighbor] = current

    return None, float('inf')

# 4. Define start and goal
start = "Shapla Garden Appartment"
goal = "UAP"

# 5. Run A* search
path, total_cost = a_star(graph, heuristics, start, goal)

# 6. Output results
if path:
    print("Shortest path from Shapla Garden Appartment to UAP:")
    print(" -> ".join(path))
    print(f"Optimal total cost (distance): {total_cost} km")
else:
    print("No path found.")
