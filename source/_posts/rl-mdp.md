---
title: Finite Markov Decision Processes & Rewards
date: 2020-06-18 15:00:13
tags: 
- 笔记
- RL
categories: Data Science

---

MDPs are a classical formalization of sequential decision making, where actions inﬂuence not just immediate rewards, but also subsequent situations, or states, and through those future rewards. 

Thus MDPs involve delayed reward and the need to tradeoff immediate and delayed reward. Whereas in bandit problems we estimated the value q ⇤ (a) of each action a, in MDPs we estimate the value q ⇤ (s, a) of each action a in each state s, or we estimate the value v ⇤ (s) of each state given optimal action selections. 

{% asset_img mdp0.png cycle %}

For a problem, as long as you can identify States, Actions, and Rewards. It can be framed using RL.

## *dynamics* of MDP
{% asset_img mdp1.png dynamics of the MDP %}

## Recycling Robot example

{% asset_img mdp2.png MDP graph %}

## Rewards & Goals

The reward signal is your way of communicating to the robot ***what*** you want it to achieve, not ***how*** you want it achieved

**Episodic** tasks: Tasks that have a set terminal state. e.g. a chess game.

**Continuing** tasks: Tasks that can continue forever. e.g. balance a pole.
**Discounting**: Decrease future rewards by discounting factor. Infinite sum of rewards remain bounded.

{% asset_img G0.png Return denoted as G %}
{% asset_img G1.png Infinite sum when gamma < 1 and >0 %}
