# WEB OF HEROES — WEEK 2: EXTRACTION

**Network science with a pulse.**

A real Marvel network — 303 characters, 1,434 real links scraped from Wikipedia — turned into a single-life extraction game where the danger isn't random. It's computed live from actual network structure.

---

## The premise

A hero called **EXTRACTION** is hiding somewhere in this network — a different one every attempt. Find them before you're **AMBUSHED**. You have one life.

- **EXTRACTION = WIN**
- **AMBUSHED = GAME OVER**

There's no hidden dice roll disguised as difficulty. Every risk number on screen is computed from the real graph you're standing inside.

## How ambush risk actually works

```
risk(node) = 5% + (degree(node) / max_degree) × 75%
```

Spider-Man's real degree is 106 — the highest in the entire network. Stepping toward him is close to the riskiest move available. A character with degree 1 or 2 is close to safe. This isn't flavor text — it's the literal Week 2 lesson (hubs behave structurally differently from peripheral nodes) made into a thing you feel before every single move instead of a fact you read once.

The corridor list shows every neighbor's real degree and a color-coded risk % (green/amber/red) before you commit. The extraction target is marked the moment it's in range. Checking before you move isn't optional flavor — it's the actual strategy.

## Controls

| Input | Action |
|---|---|
| **← / →** (or A/D) | Turn |
| **↑** (or W) | Step into whatever's centered in your crosshair |
| **↓** (or S) | Retreat one step back along your own trail (always safe) |
| **Click** | Click any connected hero directly in the 3D view, or pick one from the corridor list |

## Layout

The 3D view sits in a horizontal band across the top. Below it, two panels sit side by side: **Week 2** (green) on the left, **Mission** (gold) on the right. Both scroll independently and collapse into a single stacked column on narrow screens.

## Tools

- **🔍 Extraction Intel** — fetches the real, live Wikipedia article for your current target (not a summary, not flavor text) and automatically highlights any other real character mentioned in it in green — an actual clue about which direction to head, pulled straight from the source. Opens full-screen on click.
- **Expandable minimap** — click the small trajectory map bottom-right of the 3D view to open it full-screen. Every hero you've visited so far is individually marked and labeled, not just your current position.

## The Week 2 lab panel

Start with **📖 THE WHOLE STORY**, a full walkthrough pulling live numbers from this exact network: why network scientists build simple models at all, the random graph as a baseline, what it gets wrong (clustering), how Watts–Strogatz fixes that with shortcuts, what it still gets wrong (hubs), how Barabási–Albert fixes that with preferential attachment, and how shuffling turns any of these models into an actual statistical test.

Then six numbered experiments let you run each concept yourself, live, on the graph you're currently standing inside:

1. **Random baseline** — compare real average degree against the G(n,p) prediction
2. **Short paths** — trace shortest paths between your current hero and a random target
3. **Clustering gap** — compute a specific hero's local clustering coefficient by hand
4. **Hubs (BA model)** — grow a toy network with preferential attachment and compare its biggest hub to Spider-Man's real 106
5. **Null model test** — a degree-preserving shuffle, run seven times, to check whether Marvel's real clustering is actually unusual
6. **Friendship paradox** — sample random node/neighbor pairs and watch the paradox show up in real data

Six experiments, tracked in a notebook progress bar, independent of whether you live or die on any given attempt. Click the experiment panel itself to read the current result full-screen.

## Why this instead of a slide about hubs

A histogram says Spider-Man has degree 106. Standing in a room with 106 real beacons ringing outward, knowing one wrong step toward the wrong one ends the run — that's the same fact, felt instead of read.

## Tech

Vanilla JS + Three.js. No build step, no backend, one HTML file.

```bash
git clone https://github.com/ramprabumithra/Social-Graphs-Marvel.git
cd Social-Graphs-Marvel
python3 -m http.server 8000
```

Extraction Intel needs a real server origin (not a double-clicked `file://` page) since it makes a live network request — the command above handles that.

## The data

Real Wikipedia scrape, frozen as a Week 1 snapshot: **303 nodes**, **1,434 undirected edges** (deduplicated from 1,784 directed citations), 1 giant component of 277 nodes, one 9-node island, 17 true isolates. Highest real degree: **Spider-Man, 106**.

---

*Built for a Social Graphs & Interactions course — same dataset, different execution.*
