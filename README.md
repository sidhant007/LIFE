# LIFE

- Designing and implementing a variant of genetic algorithm(NEAT, or Neuro-Evolution of Augmenting Topologies) for a life simulation involving a basic organism which ages and requires food
- Problem Statement - To design a simulation in which agents are able to navigate in a 2d world so as to maximize their lifetime. Their lifetime is essentially defined by how much food they are able to eat while moving through the map and how many times can they avoid danger zones which drain their energy.
  - Each agent is depicted by a yellow circle.
  - Initally the energy level of each agent is 100 points each.
  - After every passing iteration they can move in their x and y axis by atmost +/- 10 px.
  - After each such iteration their enery reduces by 1 point. As their energy tends to 0, they tend to become transparent over time, for a better visual feedback, so that we are only concerned about the alive agents.
  - On obtaining a food particle (depicted by green circle) their energy increased by +a amount.
  - If they pass through a danger zone (depicted by red circle), their energy decreases by -b amount.
  - The aim of the agent is to try to life for the longest period of time possible. We consider one iteration as the smallest unit of time.
  - Currently in the game there are "f" food particles, each of them provide "a" amount of energy. There are "d" danger zones, each of which drains "b" amount of energy. And finally there are "k" agents in each iteration.
- Current method of solving -
  - Using a genetic algorithm, spawn k agents each with a unique randomly generate identity.
  - This unique identiy of each agent is actually a neural network. It is a x layers neural network.
  - It takes in the input as the current (x, y) coordinates of the agent, along with the distance to the nearest food particles and danger particles in each of the "rotated quadrants". So the first layer has 4(no. of rotated quadrants) * 2(food particle + danger particle) * 2(x coordinate + y coordinate) = 16 nodes.
  - "rotated quadrants" is defined as normal quadrants on a graph but rotated by 45 degrees in anti-clockwise direction.
  - Now each agents runs through the simulation and decides in which direction to go in each iteration using the decisions its neural network makes.
  - After this we assign a distribution to all the agents on the basis of their lifetime.
  - This can be considered as a single iteration of the genetic algorithm
  - Now we will cross - breed and mutate between these agents based on the distribution and generate a new off-spring generation of k new agents.
  - The cross - breeding and mutation primarily happens on the basic level of mixing 2 neural networks belonging to different agents. This is done by swapping weights of the neural nets.
  - The distribution broadly refers to the odds of a certain agent of the parent generation being selected to generate an offspring. The intuition is that if an agents performs good, then that agent is more likely to have contribution in the next generation of agents as compared to an agents which had a shorter lifespan.
  - We keep on running these iterations of genetic algorithm to improvise our results.
- Current Benchmarks -
    [WIP]
- This project was done mainly after reading about genetic algorithms and neural networks through online courses and blogs. The simulation itslef works and the agents gradually improve their scores but I cannot mathematically reason out as to why it works due to insufficient theoretical knowledge about genetic algorithms.
