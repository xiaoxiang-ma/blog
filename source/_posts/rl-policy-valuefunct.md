---
title: Policies, Value functions, Optimality
date: 2020-06-22 15:31:56
tags:
- 笔记
- RL
categories: Data Science
mathjax: true
---

## 1. Policies

Formally, a policy is a mapping from states to probabilities of selecting each possible action. If the agent is following policy $\pi$ at time $t$, then $\pi(a | s)$ is the probability that $A_t=a$ if $S_t=s$.

**Deterministic** policy: A policy that maps each state to a single action.

**Stochastic** policy: A policy where multiple actions may be selected with non-zero probability. The probabilities are non-negative and sum to 1.

***Policies tell an agent how to behave in their environment.***

***Policy can depend only on the current state, and not other things like time or previous states.***

## 2. Value functions
Value functions estimate future returns under a specific policy.

### **State-value function**
The expected return when starting in s and following policy $\pi$ thereafter.
{% asset_img statevalue.png (G: return) %}
{% asset_img v.png  %}


### **Action-value function**
The value of taking action a in state s and following policy $\pi$ thereafter.
{% asset_img actionvalue.png  %}
{% asset_img q.png  %}

Value functions allow an agent to query the quality of its current situation instead of waiting to observe the long-term outcome. 

Benefits:
- The return is not immediately available.
- The return may be random due to stochasticity in both the policy and environment dynamics. 

The value function summarizes all the possible futures by averaging over returns. Ultimately, we care most about ***learning a good policy***. Value function enable us to judge the quality of different policies.

### Bellman equation for $v_\pi$

Expresses a relationship between the ***value of a state*** and the ***values of its successor states.***

<!-- It states that the value of the start state must equal the (discounted) value of the expected next state, plus the reward expected along the way.
(Refer to previous definitions of v) -->

The Bellman equation for the state value function gives the value of the current state as a sum over the values of all the successor states, and immediate rewards. 

{% asset_img bellman.png Bellman Equation %}


$\sum$ (Action $a$'s probability under current state $s$ $\times \sum$  (probability of next state *s'* given $a$ is taken under $s$) $\times$ (corresponding reward $r$ + discounted value of state *s'* ))


{% asset_img tree.png Explains 3.14 graphically %}


{% asset_img grid.png Example of finite MDP %}


### Using Bellman equation and computing $v$

{% asset_img computingV1.png "Simple case: only one future state for each action" %}
{% asset_img computingV2.png Now solve linear equations %}

[Excercises Answers](https://github.com/LyWangPX/Reinforcement-Learning-2nd-Edition-by-Sutton-Exercise-Solutions)

## 3. Optimality


There is always at least one policy that is better than or equal to all other policies. This is an optimal policy. Although there may be more than one, we denote all the optimal policies by $\pi *$.

### Optimal state value function ($v_*$)

{% asset_img optimalv.png %}


### Optimal action value function ($q_*$)
{% asset_img optimalq.png %}
{% asset_img optimal_graphical.png %}

### Optimal policy
{% asset_img optimalpolicy.png %}

