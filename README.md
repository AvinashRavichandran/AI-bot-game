# AI-bot-game
OpenAI Gym provides a simple interface for interacting with and managing any arbitrary dynamic environment. OpenAI Universe is a platform that lets you build a bot and test it out.

# Step 1: Installation
Ensure you have Python installed. Install Gym, Universe and other required libraries using pip.
```
// Install python using brew
brew install python3
// Install the required OpenAI libraries
pip3 install gym
pip3 install numpy incremental
brew install golang libjpeg-turbo 
pip install universe
```
Everything in Universe (the environments) runs as containers inside Docker.

# Step 2: Code the Game Bot
The Game Bot is coded in Python, so we start by importing the only two dependencies needed: Gym and Universe. We use Neon Race Cars, as the test environment. 
```
import gym
import universe
```

# Step 3: Reinforcement Learning

Now we add the game bot logic that uses the reinforcement learning technique. This technique observes the game’s previous state and reward.
It then comes up with an action to perform on the environment. The goal is to make its next observation better (in our case — to maximize the game score). This action is chosen and performed by an agent (Game Bot) with the intention of maximizing the score. It’s then applied on the environment. 
The environment records the resulting state and reward based on whether the action was beneficial or not (did it win the game?).

Now we can retrieve the list of observations for each environment initialized using the env.reset() method.
```
observation_n = env.reset()
```
The next step is to create a game agent using an infinite loop, which continuously performs some action based on the observation.
```
while True:
action_n = [[('KeyEvent', 'ArrowUp', True)] for ob in observation_n]
```

We then use the env.step() method to use the action to move forward one time step. This is a very basic implementation of reinforced learning.
```
observation_n, reward_n, done_n, info = env.step(action_n)
```

The step method here returns four variables:
1) observation_n: Observations of the environment
2) reward_n: If your action was beneficial or not: +1/-1
3) done_n: Indicates if the game is over or not: Yes/No
4) info: Additional info such as performance and latency for debugging purposes

 Use the env.render() method to start the bot.
 
 # Step 4: Run the Game Bot
 Ensure Docker is running and run the bot. See it in action beating other cars
 ```
 python gamebot.py
 ```
 
 ![Alt Text](https://media.giphy.com/media/vFKqnCdLPNOKc/giphy.gif)
