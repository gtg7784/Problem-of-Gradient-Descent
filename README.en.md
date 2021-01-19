# Problem of Gradient Descent


## What is Gradient Descent?

Gradient Descent is one of ways to solve Optimization problem to find parameters that optimize the function value of Objective function.

It is a method to find optimal parameters by moving with a step size defined in the opposite direction of the gradient of the cost function to find the minimum value location of the objective function.

In order to find the location of the global minimum(minimum value of the Objective function) that is Optimal parameters, Moving Gradient Descent in defined size of steps in the direction opposite the gradient of the Cost function.

In order to find the location of the minimum value of the Objective function, we find the cost function by moving in small steps with the step size defined in the direction opposite the gradient of the cost function.

The slope covered in the previous sentence means a vector that is partial to a parameter, and the key of Gradient Descent is to repeatedly move this parameter little by little.

But it has two problems. I would like to summarize these two problems below.

## Local Minima(Minimum) Problem

The goal of Optimizer is find location of Global extreme value (Global Maximum, Minimum) of the Cost Function.

However, there are cases in which the Optimizer misunderstands that some Local minimum is Global minimum.

This is because, from the viewpoint of the Optimizer, the Local minimum found by going down the slope at the time can be judged as the Global minimum.

For example,

![Wikipedia Local Extremum](https://upload.wikimedia.org/wikipedia/commons/thumb/6/68/Extrema_example_original.svg/440px-Extrema_example_original.svg.png)

Optimizer goes down left to right, finding Local minimum that is right side, it have to pass the Global Maximum to find the Global Minimum, but doesn't pass the Global mimimum and misunderstand the Local minimum as the Global minimum.

Because, even though the Global minimum has not been reached, it is flattened at a certain point, and the Loss increases and stops when proceeding further.

## Oscillation Problem

Oscillation Problem is when learning rate is high, Optimizer use more time while goes back and forth near the minimum value.

## Solutions

We can fix those problem by Momemtum.

Momemtum is that gives 'inertia' in process of moving through Gradient Decentm It is a way to move som additional distance in that direction, remembering the way it moved in the past.

### Solving Local Minima

If you fall into the Local Minima Problem, the gradient becomes 0 and it cannot move, but through the Momemtum, inertia is added to the previously moved direction, so expect to exit the Local Mimima Problem and move to the Global Minima.

### Oscillation

In the situation where the Optimizer moves to the optimum point, the step size that can be moved in one step is limited, so suppose that there is a case that there is a case of continuous vibration from side to side.

Through the momemtum method, inertia is attached to the direction of frequent movement, and even if it vibrates, it moves further in the direction to the optimum point, so it can move faster than Optimizer.

### Side Effect of Momentum

Using Momentum, it is necessary to store the ![epsilon](https://latex.codecogs.com/svg.latex?\epsilon) and theother variables that has moved in the past to memory.
