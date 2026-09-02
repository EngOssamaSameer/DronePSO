# Drone Material Optimization using Particle Swarm Optimization (PSO)

## Overview

This project applies **Particle Swarm Optimization (PSO)** to a drone
material optimization problem.

The goal is to find the best combination of two materials, represented
by `x` and `y`, that minimizes the **drag and wobble** objective
function.

The optimization uses the **Booth function**:

``` text
f(x, y) = (x + 2y - 7)² + (2x + y - 5)²
```

The minimum is:

``` text
x = 1
y = 3
fitness = 0
```

For the drone example, this represents an optimal **1:3
aluminum-to-plastic ratio**.

## How PSO Works

Each particle represents a possible solution:

-   `x` and `y` --- the current position
-   `fitness` --- the quality of the current solution
-   `velocity` --- the current movement
-   `best_x`, `best_y` --- the particle's best position
-   `best_fitness` --- the particle's best fitness

At every iteration, each particle updates its movement using:

1.  **Inertia** --- keeps part of the previous velocity.
2.  **Cognitive component** --- moves toward the particle's own best
    position.
3.  **Social component** --- moves toward the swarm's best position.

The updated velocity is:

``` text
velocity = inertia + cognitive + social
```

The position is then updated using the new velocity.

## Project Structure

### `Particle`

The `Particle` class represents one candidate solution and handles:

-   Fitness calculation
-   Inertia calculation
-   Cognitive component
-   Social component
-   Acceleration
-   Velocity update
-   Position update

### `Swarm`

The `Swarm` class manages the particle population and handles:

-   Creating a random swarm
-   Creating a sample swarm
-   Finding the best particle
-   Running the PSO iterations

## Parameters

The notebook uses:

``` text
Inertia = 0.4
Cognitive constant = 0.3
Social constant = 0.7
Number of particles = 200
Number of iterations = 500
```

Random particles are initialized in the range `[-10, 10]`.

## Running the Notebook

Open:

``` text
drone-optimization.ipynb
```

Run the cells from top to bottom.

The PSO algorithm is executed with:

``` python
swarm = Swarm(
    INERTIA,
    COGNITIVE_CONSTANT,
    SOCIAL_CONSTANT,
    RANDOM_CHANCE,
    NUMBER_OF_PARTICLES,
    NUMBER_OF_ITERATIONS
)

swarm.run_pso()
```

## Expected Result

The algorithm should converge toward the minimum of the Booth function:

``` text
x ≈ 1
y ≈ 3
fitness ≈ 0
```

This corresponds to the example's optimal **1:3 aluminum-to-plastic
ratio**.

## Reference

The notebook uses the Booth function as the optimization objective and
references Wikipedia's article on test functions for optimization.
