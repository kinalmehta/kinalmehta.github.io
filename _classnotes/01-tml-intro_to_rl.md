---
title: "Introduction to RL"
excerpt: "Introduction to RL"
permalink: /classnotes/machine_learning/intro_to_rl
last_modified_at: 2020-09-24
---

## Introduction

Reinforcement learning is a set of algorithms which learn to act by **interacting** with the environment. The below diagram shows the overview of how the system works.

![RL World](/assets/images/classnotes/01_tml/01.png)

- Notations in RL:
  - $S_t$: State
  - $A_t$: Action given state $S_t$
  - $R_{t+1}$: Reward obtained by performing action $A_t$ in state $S_t$
  - $S_{t+1}$: Next State obtained by performing action $A_t$ in state $S_t$
  - $A_{t+1}$: Action given state $S_{t+1}$

## Agent's goal
- **Agent's goal** is to maximize the total reward obtained throughout the episode. This cumulative reward is called return in the RL literature and denoted using $G_t$ can be written as:

  $$
  G_t = R_{t+1} + R_{t+2} + R_{t+3} + \dots
  $$

## Types of tasks
- The environment/task can be divided into episodic and continuing tasks.
  - **Episodic tasks:** The tasks which has atleast one terminal state (eg. end of a game) and can be divided into separate episodes (eg. each play of the game is independent of other) are known as episodic tasks. Episodic tasks can be further classified as finite horizon task and infinite horizon task
    - *Finite horizon:* A task which terminates after a specific number of steps, no matter what current state the agent is in is called finite horizon task.
    - *Infinite horizon:* A task which is sure to terminate but there is no limitation on the number of steps it can take (can go upto infinite) is called infinite horizon task.
  - **Continuing tasks:** These tasks go on forever and there is no specific terminal state to be reached.

## Discounting
- As we see above, the task can be continuing or go on for infinite number of steps, the total return $G_t$ could become $\infin$. Hence a **discounting** factor $\gamma$ is introduced. Discounted return can be defined as follows:

  $$
  \begin{aligned}
  G_t &= R_{t+1} + \gamma*R_{t+2} + \gamma^2*R_{t+3} + \dots\\
  G_t &= \sum_{k=0}^{\infin} \gamma^{k}R_{t+k+1}
  \end{aligned}
  $$

- If $\gamma=0$, agent becomes myopic or short-sighted, and if $\gamma=1$, agent is called far-sighted
- Preference for immediate rewards can be incorporated.

## Markovian Assumption and MDP
- RL algorithms are designed assuming that the task at hand follows Markov Property.
- **Markov Property:** It states that the state and reward at next time step is dependent only on the current state and action taken at current time-step. Past history of the visited states and actions taken give no extra information.
- Alternatively it can also be written as "The future is independent of the past given the present."
- In mathematical form it can be written as follows
  
  $$
  Pr\{ R_{t+1}=r, S_{t+1}=s'| S_0, A_0, S_1, A_1, \dots, S_t, A_t\} = \\
  Pr\{ R_{t+1}=r, S_{t+1}=s'| S_t, A_t\}
  $$
- RL tasks that satisfy Markov property are called **Markov Decision Process (MDP)**.
- An MDP can be defined using the discount factor, states set, actions set, reward and environment dynamics.
  
  $$
  MDP = \{ S, A, P, R, \gamma \}
  $$

- If the environment directly observes the environment and has complete information about the environment, then it is called a **Fully Observable MDP**.
- If the agent indirectly observes the environment, than it is called **Partially Observable MDP**.
  - For eg. 
    - A robot with camera vision isn't told its absolute location
    - A poker playing agent only observes the public cards
  - Here the agent must construct its own state representation, eg.
    - Using complete history
    - Recurrent neural network

## Important probabilities defined for MDP
### State
- Probability of next state $s'$ and reward $r$ given current state $s$ and action $a$

  $$
  p(r,s'|s,a) = Pr\{ R_{t+1}=r, S_{t+1}=s' | S_t=s, A_t=a \}
  $$

- State transition probability
  
  $$
  \begin{aligned}
  p(s'|s,a) &= Pr\{ S_{t+1}=s' | S_t=s, A_t=a \} \\
            &= \sum_r Pr\{ R_{t+1}=r, S_{t+1}=s' | S_t=s, A_t=a \} \\
  p(s'|s,a) &= \sum_r p(r,s'|s,a)
  \end{aligned}
  $$

### Reward
- Expected reward given state and action

  $$
  \begin{aligned}
    r(s,a) &= \mathbb{E}[R_{t+1}=r | S_t=s, A_t=a] \\
           &= \sum_r r Pr\{ R_{t+1}=r | S_t=s, A_t=a \} \\
           &= \sum_r r \sum_{s'} Pr\{ R_{t+1}=r, S_{t+1}=s' | S_t=s, A_t=a \} \\
           &= \sum_r r p(r,s'|s,a)
  \end{aligned}
  $$

- Expected reward given state, action and resulting next state
  
  $$
  \begin{aligned}
    r(s,a,s') &= \mathbb{E}[R_{t+1}=r | S_t=s, A_t=a, S_{t+1}=s'] \\
           &= \sum_r r Pr\{ R_{t+1}=r | S_t=s, A_t=a, S_{t+1}=s' \} \\
           &= \sum_r r \frac{Pr\{ R_{t+1}=r, S_{t+1}=s' | S_t=s, A_t=a \}}{Pr\{S_{t+1}=s' | S_t=s, A_t=a \}} \\
           &= \sum_r r \frac{p(r,s'|s,a)}{p(s'|s,a)}
  \end{aligned}
  $$

- Another way of writing reward

  $$
  r(s,a) = \sum_{s'} r(s,a,s')p(s'|s,a)
  $$

## Policy
- Policy is a decision rule $\pi_t$ is the mapping from states to actions.
- **Policy** can be deterministic or stochastic.
- Deterministic policy gives which action to take given a state. A good example of of deterministic policy is greedy policy.
- Stochastic policy on the contrary, gives probability distribution over the action space. For example, $\varepsilon$-soft policy.
  
  $$
  \begin{aligned}
  \pi_t &: S \rightarrow A\\
  a &= \pi(s) \quad Deterministic \\
  \pi_t(a|s) &= P(A_t=a|S_t=s) \quad Stochastic
  \end{aligned}
  $$
- A policy can be stationary or non-stationary.
  - If the policy is same independent of the time, it is called stationary policy
  - If the policy is dependent on time-step and may take different action in same state based on time-step it is in, then its called non-stationary policy.

## Value Function

- Value function is a prediction of the expected future reward/return.
- It is used to evaluate the goodness/badness of states or state-action pairs.
- The values are conditioned on policy $\pi$.

### State Value function
- Expected return when an agent follows policy $\pi$ starting from state $s$.
- For each state $s \in S$, its value under policy $\pi$ is defined as 
  
  $$
  \begin{aligned}
    v_\pi(s) &= \mathbb{E}[G_0|S_0=s]\\
             &= \mathbb{E}[\sum_{k=0}^{\infin}\gamma^{k}R_{k+1}|S_0=s]
  \end{aligned}
  $$
- In **normalized** form it can be defined as follows
  
  $$
  \begin{aligned}
    v_\pi(s) &= (1-\gamma)\mathbb{E}[G_0|S_0=s]\\
             &= (1-\gamma)\mathbb{E}[\sum_{k=0}^{\infin}\gamma^{k}R_{k+1}|S_0=s]
  \end{aligned}
  $$

### Action Value function
- Expected return when starting from state $s$, by taking action $a$, and following policy $\pi$.

  $$
  \begin{aligned}
    p_\pi(s) &= \mathbb{E}[G_0|S_0=s, A_0=a]\\
             &= \mathbb{E}[\sum_{k=0}^{\infin}\gamma^{k}R_{k+1}|S_0=s, A_0=a]
  \end{aligned}
  $$
- In **normalized** form it can be defined as follows

  $$
  \begin{aligned}
    p_\pi(s) &= (1-\gamma)\mathbb{E}[G_0|S_0=s, A_0=a]\\
             &= (1-\gamma)\mathbb{E}[\sum_{k=0}^{\infin}\gamma^{k}R_{k+1}|S_0=s, A_0=a]
  \end{aligned}
  $$




## References
1. [David Silver lectures and slides](https://www.youtube.com/playlist?list=PLqYmG7hTraZBiG_XpjnPrSNw-1XQaM_gB)
2. [Introduction to RL textbook by Richard Sutton and Andrew Barto](http://www.incompleteideas.net/book/the-book-2nd.html)
3. [Algorithms for Reinforcement Learning by Csaba Szepesvari](https://sites.ualberta.ca/~szepesva/rlbook.html)




