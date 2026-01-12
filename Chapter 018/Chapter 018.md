
# CHAPTER 18: Reinforcement Learning

Reinforcement Learning berbeda dari supervised learning: agent belajar through trial dan error, menerima rewards atau penalties untuk actions.

## Konsep Dasar RL

**Reinforcement Learning** melibatkan:
- **Agent**: system yang belajar
- **Environment**: world yang agent interact dengan
- **State**: current situation
- **Action**: agent dapat melakukan
- **Reward**: feedback untuk actions

### Goals:
Maximize cumulative reward over time.

## Policy Search

**Policy Search** mengoptimasi policy (mapping dari observations ke actions):
- Policy dapat deterministic atau stochastic
- Objective: maximize expected cumulative reward

### Neural Network Policies:
- Policy adalah neural network yang takes observations sebagai input
- Outputs action probabilities (stochastic) atau action directly (deterministic)
- Training menggunakan policy gradient methods

## OpenAI Gym

**OpenAI Gym** adalah standard environment interface untuk RL:
- Provides various environments (CartPole, Atari, robotics, etc.)
- Consistent API untuk environment interaction
- Essential untuk RL research dan education

## Markov Decision Processes (MDPs)

**MDPs** adalah mathematical framework untuk RL:
- State space S
- Action space A
- Transition probability P(s'|s,a)
- Reward function R(s,a,s')
- Discount factor γ (0 ≤ γ ≤ 1)

## Temporal Difference Learning

**Temporal Difference (TD) Learning** combines ideas dari Monte Carlo dan dynamic programming:
- Learn value functions dari bootstrapping (using estimated future values)
- Update rules: V(s) ← V(s) + α[r + γV(s') - V(s)]
- More efficient than pure Monte Carlo

## Q-Learning

**Q-Learning** learns action-value function Q(state, action):
- Q(s,a) = expected cumulative reward untuk taking action a di state s
- **Bellman equation**: Q(s,a) = E[r + γ * max Q(s',a')]
- Off-policy learning (learns optimal policy while following exploratory policy)

### Exploration vs Exploitation:
- **Exploitation**: choose best known action
- **Exploration**: try unknown actions untuk discover better policies
- **Epsilon-greedy**: dengan probability ε explore, else exploit

## Deep Q-Learning (DQN)

**Deep Q-Networks** use neural networks untuk approximate Q-function:
- Function approximation enables learning complex policies
- Challenges:
  - **Instability**: bootstrapping dapat cause divergence
  - **Correlation**: consecutive samples highly correlated

### Stabilization Techniques:

#### Fixed Q-Value Targets
- Use separate network untuk compute targets
- Periodically copy weights dari training network
- Breaks correlation dengan targets

#### Experience Replay
- Store past transitions di memory buffer
- Sample randomly untuk training
- Breaks correlation antara samples

#### Double DQN
- Reduce overestimation bias di Q-learning
- Use current network untuk select action, target network untuk evaluate

#### Prioritized Experience Replay
- Prioritize learning dari important transitions
- Weighted sampling dari memory

#### Dueling DQN
- Separate streams: value stream dan advantage stream
- Combines untuk Q-values
- Learn value of state independent dari actions

## Policy Gradient Methods

**Policy Gradient** directly optimize policy parameters:
- Use gradient ascent (not descent!)
- Gradient direction: ∂J/∂θ ∝ E[∇ log π(a|s) Q(s,a)]

### REINFORCE Algorithm
- Compute policy gradients dari trajectory rewards
- Monte Carlo approach (full trajectory needed)
- High variance, slow learning

## Actor-Critic Methods

**Actor-Critic** combines policy (actor) dengan value function (critic):
- **Actor**: policy network untuk action selection
- **Critic**: value network untuk estimating value
- Critic reduces variance dalam policy gradient estimates
- More efficient than pure policy gradient

### Algorithms:
- A3C (Asynchronous Advantage Actor-Critic)
- PPO (Proximal Policy Optimization)
- TRPO (Trust Region Policy Optimization)

## Advanced Topics

### Multi-agent RL
- Multiple agents learning simultaneously
- Cooperation vs competition
- Challenges: non-stationary environment

### Meta-learning
- Learning to learn efficiently
- Transfer knowledge across tasks

### Hierarchical RL
- Learning at multiple levels of abstraction
- Options framework

## TF-Agents

**TF-Agents** adalah TensorFlow library untuk RL:
- Reusable components untuk environment, agents, networks
- Efficient implementations
- Distributed training support

## Kesimpulan

Reinforcement Learning adalah powerful framework untuk learning sequential decision-making. Deep RL enables learning complex policies untuk challenging problems. Active research area dengan continuous innovations.
