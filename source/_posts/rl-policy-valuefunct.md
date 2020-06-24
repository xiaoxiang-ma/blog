---
title: Policies and Value functions
date: 2020-06-22 15:31:56
tags:
- 笔记
- RL
categories: Data Science
---

## Policies

Formally, a policy is a mapping from states to probabilities of selecting each possible action. If the agent is following policy pi at time t, then pi(a | s) is the probability that At= a if St= s.

**Deterministic** policy: A policy that maps each state to a single action.

**Stochastic** policy: A policy where multiple actions may be selected with non-zero probability. The probabilities are non-negative and sum to 1.

Policy can depend only on the current state, and not other things like time or previous states.

## Value functions

**State-value function**
The expected return when starting in s and following policy pi thereafter.
{% asset_img statevalue.png (G: return) %}
{% asset_img v.png  %}


**Action-value function**
The value of taking action a in state s under a policy pi.
{% asset_img actionvalue.png  %}
{% asset_img q.png  %}

Value functions allow an agent to query the quality of its current situation instead of waiting to observe the long-term outcome. 

Benefits:
1. The return is not immediately available
2. The return may be random due to stochasticity in both the policy and environment dynamics. 

The value function summarizes all the possible futures by averaging over returns. Ultimately, we care most about ***learning a good policy***. Value function enable us to judge the quality of different policies.

### Bellman equation for v pi

Expresses a relationship between the ***value of a state*** and the ***values of its successor states.***

It states that the value of the start state must equal the (discounted) value of the expected next state, plus the reward expected along the way.
(Refer to previous definitions of v)

{% asset_img bellman.png Bellman Equation %}


Sum of (Action a's probability under current state s * the sum of (probability of next state s' given a is taken under s * the sum of corresponding reward r and discounted value of state s'))


{% asset_img tree.png Tree %}

> Each open circle represents a state and each solid circle represents a **state–action** pair. Starting from state s, the root node at the top, the agent could take any of some set of actions -- three are shown in the diagram—based on its policy pi. From each of these, the environment could respond with one of several next states, s' (two are shown in the ﬁgure), along with a reward, r, depending on its dynamics given by the function p.

{% asset_img grid.png Example of finite MDP %}


### Using Bellman equation and computing v

{% asset_img computingV1.png "Simple case: only one future state for each action" %}
{% asset_img computingV2.png Now solve linear equations %}

