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
