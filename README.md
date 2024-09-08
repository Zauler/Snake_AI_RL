# Snake Game with Deep Reinforcement Learning (DQN)

<div align="center">
  <img src="https://github.com/Zauler/Snake_AI_RL/blob/main/img/snake_rl_crop.gif" alt="Snake Game Demo">
</div>

## Overview
This project demonstrates a classic **Snake** game environment built using **Pygame** and integrated into **OpenAI's Gym** environment. The game is played by an AI agent trained using the **Deep Q-Networks (DQN)** algorithm—a popular method in **Reinforcement Learning (RL)**. The goal of the agent is to maximize its score by eating food while avoiding collisions with the walls and its own body.

The project combines **computer vision**, **game development**, and **deep reinforcement learning**. It includes the environment for the Snake game, the implementation of a **Convolutional Neural Network (CNN)** for learning, and the training/testing process using the DQN agent.

## ⚠️ Important

### Python Version

This project requires **Python 3.7**, **tensorflow 2.1.0**, and **Gym version 0.17.2** . Make sure you have the correct version installed. You also need to install the environment locally to be able to import it.


## Technologies Used

### 1. Pygame
- **Pygame** is used to create the **Snake** game, which serves as the environment for the RL agent. The game includes fundamental mechanics like movement, food spawning, and collision detection.
- It also provides real-time rendering of the game environment and the snake’s movement.

### 2. OpenAI Gym
- **OpenAI Gym** is used to define the Snake environment in a modular way that interacts with the RL algorithm.
- The environment follows the typical Gym structure with the `reset`, `step`, `render`, and `close` methods. It provides observations to the agent in the form of pixel-based image arrays.

### 3. Deep Reinforcement Learning (DQN)
- The agent is trained using **Deep Q-Networks (DQN)**, a value-based reinforcement learning algorithm developed by **DeepMind**.
- The architecture of the CNN used in this project is inspired by the **Atari DQN model** that processes high-dimensional visual input (pixel frames) to learn optimal game strategies.
- The CNN consists of multiple convolutional layers to extract features from the image inputs, followed by fully connected layers that output Q-values for each possible action the agent can take.

### 4. TensorFlow and Keras-RL
- **TensorFlow** is used as the backend for building and training the deep learning model. **Keras** is leveraged for creating the CNN architecture.
- **Keras-RL** is used to provide RL-specific functionality, such as the DQN agent, policies (e.g., Epsilon-Greedy), memory buffers (experience replay), and training/testing routines.

### 5. Numpy and Image Processing
- **Numpy** is used for various matrix operations and to handle image arrays that represent the current game state.
- The project also includes an **Image Processor** to preprocess the observations (convert raw game pixels into grayscale images, resize them, etc.), which is critical for feeding the right input into the CNN model.

## How It Works

### Environment (Snake Game)
The `SnakeEnv` class inherits from `gym.Env` and defines the snake's environment:

- **Actions**: The agent can move the snake in one of four directions (up, down, left, right).
- **Rewards**: The agent receives a reward of +1 for successfully eating food and -1 if the game ends (collision with the wall or snake's body).
- **Observations**: The environment provides the agent with the current game screen in the form of pixel images, allowing the agent to "see" the game.

### Deep Q-Network (DQN)
The **DQN Agent** is implemented using a **Convolutional Neural Network (CNN)** that processes the pixel-based observations:

- **Input**: The CNN takes as input a stack of frames, representing the recent game states, to give the agent temporal awareness.
- **Architecture**: The network consists of three convolutional layers, followed by fully connected layers, ending with an output layer representing the Q-values for each possible action.
- **Training**: The agent is trained over 1.5 million steps, where it learns to maximize the cumulative reward by selecting actions that lead to positive outcomes (eating food, avoiding death).

### Training and Testing
- During training, the agent plays multiple episodes of the Snake game, storing its experiences in a replay memory and updating its policy based on the Q-learning algorithm.
- Once the model is trained, the agent is tested in real-time, and the Snake game is rendered to visualize the agent's learned strategy.

## Summary of Steps to Install a Custom Gym Environment:

- Ensure your environment class follows the Gym API.
- Register the environment using gym.envs.registration.register.
- Package it using setup.py.
- Install the package using pip install -e . from the folder where setup.py is located.
- Use the environment by calling gym.make('Snake-v0').
