---
title: "cave generation using cellular automata"
date: 2023-06-30
tags: [procedural generation, roguelikes]
categories: "gamedev"
summary: "a short introduction to cellular automata and how to use them to generate caves"
---

## introduction
Caves are nice or something and very popular in games like minecraft and terraria. In this post we will learn how to generate very simple caves using cellular automata.

## cellular automata

Cellular automata is a very simple model of computation. It consists of a grid of cells , each cell being able to be in one of a finite number of states. Usually the state of a cell is determined by the state of its neighbours, but its not necessary. Every timestep some rules are applied to the grid to determine the state of each cell in the next timestep.

Uhh, that's many words for a very simple concept. Let's see an example:

### conway's game of life

The most famous cellular automata is probably conway's game of life. It consists of a grid of cells, each cell being either alive or dead. The rules are:

- if a cell is alive and has 2 or 3 alive neighbours, it stays alive
- if a cell is dead and has exactly 3 alive neighbours, it becomes alive
- otherwise the cell dies or stays dead

You can see a simulation of the game of life [here](https://playgameoflife.com/).

## cave generation

Let's use $1$ to represent a wall and $0$ to represent empty space.

One idea for cave generation is to, you know, embrace the randomness and just generate a random grid of cells.

Let's see some code. I'm using python for this, but you can use any language you want.

```python
import random

function generateCave(width,height,fillProb):
    grid = [[0 for i in range(width)] for j in range(height)]
    for i in range(width):
        for j in range(height):
            if random.random() > fillProb:
                grid[i][j] = 1
    return grid

grid = generateCave(128,128,0.5)
```

And that looks like this:

<img src="/images/random_cave.png" style="width:60%">

Not very cave-like, is it? It's just a bunch of random dots. Let try to use cellular automata to make it look more like a cave.

### cellular automata cave generation

We will use a very simple cellular automata to generate caves. The rules are:

- if a cell has more than 5 alive neighbours, it becomes alive
- if a cell has less than 4 alive neighbours, it dies

Here an alive cell is a wall and a dead cell is empty space.

Let's see some code:

```python

def countAliveNeighbours(grid,x,y):
    count = 0
    for i in range(-1,2):
        for j in range(-1,2):
            neighbour_x = x+i
            neighbour_y = y+j
            if i == 0 and j == 0:
                continue
            elif neighbour_x < 0 or neighbour_y < 0 or neighbour_x >= len(grid) or neighbour_y >= len(grid[0]):
                count += 1
            elif grid[neighbour_x][neighbour_y] == 1:
                count += 1
    return count

def doSimulationStep(grid):
    newGrid = [[0 for i in range(len(grid[0]))] for j in range(len(grid))]
    for i in range(len(grid)):
        for j in range(len(grid[0])):
            aliveNeighbours = countAliveNeighbours(grid,i,j)
            if grid[i][j] == 1:
                if aliveNeighbours < 4:
                    newGrid[i][j] = 0
                else:
                    newGrid[i][j] = 1
            else:
                if aliveNeighbours > 5:
                    newGrid[i][j] = 1
                else:
                    newGrid[i][j] = 0
    return newGrid

def generateCave(width,height,fillProb,steps):
    grid = [[0 for i in range(width)] for j in range(height)]
    for i in range(width):
        for j in range(height):
            if random.random() > fillProb:
                grid[i][j] = 1
    for i in range(steps):
        grid = doSimulationStep(grid)
    return grid

grid = generateCave(128,128,0.5,5)
```

And here is how each step looks like:

<img src="/images/ca_cave.gif" style="width:60%">

We can see that the cellular automata makes shapes in the noise, and it smooths the shape out.
Let's also look at other `fillProb` values:

Anything below 0.4 is just a bunch of random dots, and anything above 0.6 is just a big blob.
<table>
<tr>
<td><img src="/images/ca_cave_0.4.gif" style="width:100%"></td>
<td><img src="/images/ca_cave_0.45.gif" style="width:100%"></td>
<td><img src="/images/ca_cave_0.5.gif" style="width:100%"></td>
<td><img src="/images/ca_cave_0.55.gif" style="width:100%"></td>
</tr>
</table>

### boundaries

Notice that the caves are touching the edges of the grid, and that's not very nice because there is a very clear cut.
To solve this we can make it less likely for the noise to generate when the cell is near the edge of the grid.

For this we want to create a "falloff" function that is $0$ at the edges of the grid and $1$ at the center of the grid.
We can get a few different falloff functions. Here are some:

```python
def elipseFalloff(x,y,width,height):
    scale_x = (x - width/2) / (width/2)
    scale_y = (y - height/2) / (height/2)
    return 1-math.sqrt(scale_x**2 + scale_y**2)

def linearFalloff(x,y,width,height):
    scale_x = (x - width/2) / (width/2)
    scale_y = (y - height/2) / (height/2)
    return max(abs(scale_x),abs(scale_y))
```

We can also manipulate them using a function like $f(x) = x^5$ to make them more or less steep.

Finally, we want where there fallout function is bigger to 
