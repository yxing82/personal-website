---
title: "Notes on ML with Graphs"
date: 2026-05-02
categories: [Notes, Machine Learning]
tags: [graphs, ml]
math: true
---

## Traditional Machine learning

For traditional machine learning, people basically work on capturing features to make predictions. Specifically, researchers use hand-designed features.

Given graph $G = (V, E)$, we want to know how to learn a function $f: V \rightarrow \mathbb{R}$ 

In this post, we will talk about 3 types of predictions about the Graph:

- Node-level prediction
- Link-level prediction
- Graph-level prediction

## Section 2

$$
\mathcal{L} = \sum_{i=1}^{N} \ell(y_i, \hat{y}_i)
$$
