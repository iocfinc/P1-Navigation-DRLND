# Project 1 - Navigation

## Overview

This is the first project of the Deep Reinforcement Learning for Enterprise Nanodegree from Udacity. You can view the details on how to set up the project through the `README.md` file. The gist of the project is that we have to come up with a controller for the agent in Unity's Banana Collector environment.

Every time the agent gets a Yellow banana it is rewarded +1 and every Blue banana -1. The agent simply has to get as many yellow bananas as it can and avoid the blue bananas.

To limit the time spent training the agent, the environment is considered solved when the average reward is greater than 13.

## Approach

In this version of the project, we are using Unity's raycasting returns and the agent's parameters like velocity. Just a quick explanation on raycasting, it is similar to how radars work. A ray is cast from the agent to multiple directions. Once the ray hits an object it would return a signal to the agent. The returned signal will let the agent know what is in front of it and how far it is from the agent's current position and at what direction. This was the agent will know the state it is in. With this information, the agent can then decide which action to take.

For this project, I decided to make use of the Deep-Q Network to reach the objective. Making use of the previous DQN exercise as a template, I reconfigured the model structure and hyperparameters.

## Model Structure

For this project, the final version of the model structure has 2 hidden Fully Connected layers between the input and output. The input has 37 parameters, primarily the raycast returns. The output would be the probability for the  4 possible actions (up, down, left and right). In between, are two FC layers. FC1 has 256 nodes within it and it links the input and FC2. FC2 has 64 nodes within it and it connects FC1 and the output. The FC layers had a ReLU activation

## Hyperparameters

As I mentioned before, this project mostly borrows from the DQN exercises. The initial hyperparameter values were taken there and served as the baseline. Through some tests, the current hyperparameters were obtained. The majority of the hyperparameters remained, for example, the buffer sizes, batch size, Tau and Gamma values. One hyperparameter that was changed was the Learning rate which was increased from 0.0005 to 0.0001. The effect was that the agent was able to solve the environment slightly faster. This made sense considering that the learning rate dictates the speed of convergence of the solution.

## Results

The environment was considered solved at the 349th episode where the average score reached exactly 13. Continuing with the rest of the episodes, the agent was able to get to a maximum score of 26 and the highest average score was 16.5.

<p align='center'><img src="https://github.com/iocfinc/P1-Navigation-DRLND/blob/master/images/Rewards_Plot.png" alt="Rewards Plot"></p>

## Future Plans

It would be great to do the Pixel version of this project. The navigation using the Pixel version is based on what the agent sees instead of the current version where it depends on the input from raycasting and the agent's velocity. It would be fun to play around with the Pixel version next time and use CNNs to control the agent.