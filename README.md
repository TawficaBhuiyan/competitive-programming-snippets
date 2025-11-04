# 🧩 Competitive Programming Snippets (C++)

This repository contains my personal collection of **Data Structures and Algorithms** implemented in C++ for competitive programming.  
Each snippet is designed for **reusability, readability, and speed**, following standard CP templates.

---

## 📂 Folder Overview

| Folder | Description |
|--------|--------------|
| `C++_Template/` | My base competitive programming template. |
| `Algorithms/` | Core algorithm implementations (Sorting, Graph, DP, etc.). |
| `DataStructures/` | Frequently used data structures (Segment Tree, DSU, BIT). |
| `Snippets/` | Small reusable code snippets and helper functions. |

---

## 🧠 Purpose
This repository is part of my **continuous DSA learning journey**.  
It serves as both a **personal toolkit** for contests and a **public showcase** of my structured approach to algorithmic coding.

---

## ⚙️ Language & Environment
- **Language:** C++17 / C++20  
- **Editor:** Visual Studio Code  
- **Platforms Tested On:** Codeforces, AtCoder, LeetCode, LightOJ  

---

## 🪶 Example Snippets

### 🔹 Dijkstra's Shortest Path (`Algorithms/Graph/dijkstra.cpp`)
```cpp
/*------------------------------------------------------------
| Algorithm: Dijkstra's Shortest Path
| Author: Tawfica Bhuiyan
| Description: Finds the shortest distance from a source node
|              to all other nodes in a weighted graph using a
|              priority queue (min-heap).
| Time Complexity: O((V + E) log V)
-------------------------------------------------------------*/

#include <bits/stdc++.h>
using namespace std;

#define int long long

vector<int> dijkstra(int n, int src, vector<vector<pair<int,int>>>& adj) {
    vector<int> dist(n, LLONG_MAX);
    priority_queue<pair<int,int>, vector<pair<int,int>>, greater<>> pq;
    dist[src] = 0;
    pq.push({0, src});
    while(!pq.empty()) {
        auto [d,u] = pq.top(); pq.pop();
        if(d != dist[u]) continue;
        for(auto [v,w]: adj[u]) {
            if(dist[v] > d + w) {
                dist[v] = d + w;
                pq.push({dist[v], v});
            }
        }
    }
    return dist;
}
