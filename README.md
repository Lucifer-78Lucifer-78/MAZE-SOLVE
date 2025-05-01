# MAZE-SOLVE
A visualization tool and solver for mazes using various pathfinding algorithms.
from collections import defaultdict, deque

def create_graph_420():
    """Creates a graph from user input."""
    graph_420 = defaultdict(list)
    num_edges_420 = int(input("Enter the number of edges: "))

    for _ in range(num_edges_420):
        u_420, v_420 = input("Enter an edge (u v): ").split()
        graph_420[u_420].append(v_420)
        graph_420[v_420].append(u_420)  # If the graph is undirected

    return graph_420

def bfs_420(graph_420, start_420):
    """Performs Breadth-First Search on the graph."""
    visited_420 = set()
    queue_420 = deque([start_420])
    bfs_result_420 = []

    while queue_420:
        node_420 = queue_420.popleft()
        if node_420 not in visited_420:
            visited_420.add(node_420)
            bfs_result_420.append(node_420)
            queue_420.extend(graph_420[node_420])

    return bfs_result_420

def dfs_420(graph_420, start_420, visited_420=None, dfs_result_420=None):
    """Performs Depth-First Search on the graph."""
    if visited_420 is None:
        visited_420 = set()
    if dfs_result_420 is None:
        dfs_result_420 = []

    visited_420.add(start_420)
    dfs_result_420.append(start_420)

    for neighbor_420 in graph_420[start_420]:
        if neighbor_420 not in visited_420:
            dfs_420(graph_420, neighbor_420, visited_420, dfs_result_420)

    return dfs_result_420

if __name__ == "__main__":
    graph_420 = create_graph_420()
    print("Graph:", dict(graph_420))

    start_node_420 = input("Enter the starting node: ")

    bfs_result_420 = bfs_420(graph_420, start_node_420)
    print("BFS Traversal:", bfs_result_420)

    dfs_result_420 = dfs_420(graph_420, start_node_420)
    print("DFS Traversal:", dfs_result_420)
