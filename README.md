# 🎯 WEB OF HEROES — WEEK 2: EXTRACTION

**Network science with a pulse.**

A real Marvel network — 303 characters, 1,434 real links scraped from Wikipedia — turned into a single-life extraction game where the danger isn't random. It's computed live from actual network structure.

---

## The premise

Somewhere in this network, some heroes have turned. Find the **EXTRACTION** point before you're **AMBUSHED**. You have one life.

- **EXTRACTION = WIN**
- **AMBUSHED = GAME OVER**

There's no hidden dice roll disguised as difficulty. Every risk number on screen is computed from the real graph you're standing inside.

## How ambush risk actually works

```
risk(node) = 5% + (degree(node) / max_degree) × 75%
```

Spider-Man's real degree is 106 — the highest in the entire network. Stepping toward him is close to the riskiest move available. A character with degree 1 or 2 is close to safe. This isn't flavor text — it's the literal Week 2 lesson (hubs behave structurally differently from peripheral nodes) made into a thing you feel before every single move instead of a fact you read once.

The corridor list shows every neighbor's real degree and computed risk % before you commit. The extraction target is marked the moment it's in range. Checking before you move isn't optional flavor — it's the actual strategy.

## Controls

| Input | Action |
|---|---|
| **← / →** | Turn |
| **↑** | Step into whatever's centered in your crosshair |
| **↓** | Retreat one step back along your own trail (always safe) |
| **Click** | Click any connected hero directly, or pick one from the corridor list |

## The Week 2 lab panel

Alongside the extraction attempt, a live experiment console runs real computations against the same graph:

- **G(n,p)** — compare real average degree against the random-graph prediction
- **Small world** — trace shortest paths between the character you're standing on and a random target
- **Clustering** — compute local clustering coefficient for your current room, live
- **Hubs** — grow a toy network with preferential attachment and compare its biggest hub to Spider-Man's real one
- **Shuffle test** — a degree-preserving null model, run seven times, to check whether Marvel's real clustering is actually unusual
- **Friendship paradox** — sample random node/neighbor pairs and watch the paradox show up in real data

Six experiments, tracked in a notebook progress bar, independent of whether you live or die on any given attempt.

## Why this instead of a slide about hubs

A histogram says Spider-Man has degree 106. Standing in a room with 106 real beacons ringing outward, knowing one wrong step toward the wrong one ends the run — that's the same fact, felt instead of read.

## Tech

Vanilla JS + Three.js. No build step, no backend, one HTML file.

```bash
git clone https://github.com/ramprabumithra/Social-Graphs-Marvel.git
cd Social-Graphs-Marvel
python3 -m http.server 8000
```

## The data

Real Wikipedia scrape, frozen as a Week 1 snapshot: **303 nodes**, **1,434 undirected edges** (deduplicated from 1,784 directed citations), 1 giant component of 277 nodes, one 9-node island, 17 true isolates. Highest real degree: **Spider-Man, 106**.

---

*Built for a Social Graphs & Interactions course — same dataset every week, a different way to sit inside it each time.*
