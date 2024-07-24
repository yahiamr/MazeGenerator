# p5.js Backtracking Maze Generator

An interactive maze generator using the backtracking algorithm, visualized with the p5.js library.

## Overview

This project provides an interactive way to visualize the backtracking maze generation algorithm. With p5.js, we bring the algorithmic process to life, allowing users to observe and appreciate the intricacies of maze generation.

## Features



1. **Cell Object (`cell.js`)**: Each cell in the grid is represented by this object. It has attributes like position (i, j), walls (top, right, bottom, left), and whether it's visited or not. It also contains methods to display the cell and to check for neighbors that haven't been visited.

2. **Maze Grid (`sketch.js`)**: This file sets up the maze grid, defines the maze generation algorithm, and displays the maze. The grid is an array of cell objects, and the maze generation uses a stack to backtrack when it reaches a cell with no unvisited neighbors.

Let's dive a little deeper:

- **Initialization**: In the `setup()` function, you set the size of the canvas, determine the number of columns and rows based on the canvas size, and initialize the grid with cells. The starting cell is the first cell in the grid.

- **Maze Generation (`draw()` function)**: This function repeatedly:
  1. Marks the current cell as visited.
  2. Checks for an unvisited neighbor.
  3. If there's an unvisited neighbor:
     - Push the current cell to the stack.
     - Remove the walls between the current cell and chosen cell.
     - Make the chosen cell the new current cell.
  4. If there are no unvisited neighbors:
     - Pop a cell from the stack and make it the current cell.

The maze generation continues until the stack is empty, which means all cells are visited and the maze is complete.

Your code seems to be pretty neat and modular. The use of the `checkNeighbors()` method in the `Cell` object and the `removeWalls()` function in the main `sketch.js` makes the implementation clean.

**Potential Enhancements**:
1. **End Point**: You've highlighted the last cell. In a typical maze, you'd usually want a clear start and end. You've got the start (top-left) and an end (bottom-right), but you might want to ensure that there's always a clear path to the end point.
 
2. **Animation Speed**: If you want to observe the maze generation more clearly, consider introducing a speed control or pausing mechanism.

3. **Solution Visualization**: Once the maze is generated, it'd be interesting to implement an algorithm that finds the solution path from the start to the end.

4. **User Interaction**: Allow users to change the grid size, maze generation speed, or even the starting and ending points.

5. **Different Algorithms**: There are many maze generation algorithms, like Prim's or Kruskal's. You can implement multiple algorithms and let the user choose which one to use.


## Getting Started

1. **Clone the Repository**
   ```sh
   git clone https://github.com/your-username/p5js-maze-generator.git
   cd p5js-maze-generator
   ```

2. **Open `index.html` in Your Browser**
   Simply double-click the `index.html` file to start visualizing the maze generation process.

3. **Interact with the Maze Generator**
   Adjust settings, restart the generation, and dive deep into the world of mazes.

## Development

Contributions are welcome!

1. Fork the repo on GitHub.
2. Clone your fork.
3. Make your changes.
4. Commit and push to your fork.
5. Open a pull request.

## Technologies Used

- [p5.js](https://p5js.org/) - A JS client-side library for creating graphic and interactive experiences.

## TODO solve using GAs
1. Representation
Each genome in the GA will represent a path through the maze. The genome could be a string of directions, e.g., UDLR for up, down, left, and right respectively.

2. Fitness Function
The fitness of each path will be based on how close it gets to the exit (or how far it travels without hitting a wall). The more distance it covers, the higher its fitness.

3. Selection
Select two parent paths based on their fitness. Paths that cover more distance in the maze without hitting a wall are more likely to be selected.

4. Crossover
Given two parent paths, produce a child path. One way to crossover is to pick a random point in the path and swap the segments after that point between the two parents.

5. Mutation
Occasionally, make a random change to a path. This could involve changing a direction or adding/removing a step.

6. Repeat
Generate new populations of paths using selection, crossover, and mutation. Over time, paths that get closer to solving the maze should emerge.

Implementation:
1- Initialize a population of random paths.
2- Calculate the fitness of each path in the population.
   - Move through the maze according to the directions in the path.
   - If you hit a wall, stop.
   - Calculate fitness based on distance traveled. If a path reaches the end of the maze, give it a large fitness bonus.
3- Select two parent paths. Paths that traveled further in the maze are more likely to be selected.
4- Crossover the parents to produce a child path.
5- Occasionally mutate the child path.
6- Repeat with the new population.
7- Stop when a path has found the exit or after a certain number of generations.



## TODO: Implement Solver Using BFS Algorithm

### Overview

The next phase in our project is to implement a maze solver using the Breadth-First Search (BFS) algorithm. BFS is an ideal choice for this task as it finds the shortest path in an unweighted graph, which, in our case, is the maze represented by a grid of cells.

### Objective

The solver should find the shortest path from the starting cell (top-left corner of the maze) to the target cell (bottom-right corner). It will navigate through the maze grid, respecting the walls and boundaries defined during the maze generation phase.

### Implementation Details

1. **BFS Algorithm**: Unlike Depth-First Search (DFS), BFS explores the maze level by level, starting from the start node and moving towards the end node, ensuring the shortest path is found.

2. **Data Structures**:
   - A `queue` to keep track of cells to be explored next.
   - A `visited` array or property to mark cells that have already been explored to avoid revisiting them.

3. **Solver Function**: The core function to implement the BFS algorithm. It will:
   - Initialize the queue with the starting cell.
   - Explore each cell's neighbors, adding them to the queue if they haven't been visited and are accessible (no wall in between).
   - Continue the process until the queue is empty or the target cell is reached.

4. **Path Reconstruction**: After reaching the target cell, reconstruct the path taken from the start to the end. This might require additional properties in the cell object to keep track of the path.

5. **Visual Representation**: Visually represent the path found by the solver in the maze, possibly with a distinct color or pattern.

6. **Integration**: Ensure that the solver is triggered after the maze generation phase is complete, and that it interacts correctly with the existing maze structure.

### Function Signature

The BFS solver function might have the following signature:

```javascript
function solveMazeBFS(startCell, targetCell) {
    // Implementation here
}
```

### Testing

Thoroughly test the solver to ensure it correctly finds the shortest path in various maze configurations. Handle edge cases like no available path or extremely complex mazes.

---

*Note: This section is a guideline and should be adapted based on the specific requirements and architecture of your project.*
