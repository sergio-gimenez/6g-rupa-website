---
title: "LEOPath Released: An Open-Source LEO Routing Simulator"
description: "We published LEOPath, a Python-based simulation framework to analyze and compare routing algorithms in LEO satellite constellations."
date: 2026-01-09
lastmod: 2026-02-09
categories:
    - "news"
tags:
    - "LEOPath"
    - "Simulator"
    - "LEO"
    - "NTN"
    - "Routing"
    - "Open Source"
    - "6G-RUPA"
---

[
![LEOPath logo](https://raw.githubusercontent.com/Fundacio-i2CAT/LEOPath/main/leopath_logo.png)
](https://github.com/Fundacio-i2CAT/LEOPath)

We published **LEOPath**, an open-source, Python-based simulation framework for analyzing and comparing routing algorithms in **LEO satellite constellations**.

- GitHub: <https://github.com/Fundacio-i2CAT/LEOPath>
- PyPI: <https://pypi.org/project/leopath/>

## What LEOPath is for

LEOPath is designed for **topology/routing-state generation** in time-varying LEO networks. It helps you study how a constellation evolves over time (satellite movement, changing ISLs/GSLs) and how different routing approaches behave.

Some highlights:

- **Realistic constellation modeling** using TLEs + SGP4 propagation
- **Dynamic network state** (time-varying ISLs and ground-station visibility)
- **Pluggable routing algorithms**, including a link-state shortest-path baseline and our 6G-RUPA-inspired topological routing
- **Ground station support** and configurable attachment policies
- **Visualization pipeline** (Cesium-based 3D views)

## What LEOPath is not

LEOPath intentionally does *not* simulate a full end-to-end protocol stack or packet-level effects (e.g., TCP behavior, detailed PHY/MAC, queueing). Instead, it focuses on generating forwarding state and network dynamics that you can analyze directly or feed into other tooling.

## Quick start

Install the package:

```bash
pip install leopath
```

Or run simulations via Docker (recommended by the project):

```bash
git clone https://github.com/Fundacio-i2CAT/LEOPath.git
cd LEOPath

# Example: run a simulation with a provided config
./run-simulations.sh run -c leopath/config/ether_simple.yaml

# Generate a visualization
./run-simulations.sh visualise -c leopath/config/ether_simple.yaml
```

Note: the Cesium visualization requires a **Cesium Ion access token** (see the repository README).

## Why this matters for our work

Our current NTN research needs tooling that is easy to run, easy to extend, and explicit about *routing state* and *control overhead* in large constellations. LEOPath is the simulator we use to explore these design points (including topological routing ideas connected to **6G-RUPA**).

If you try it out (or want to plug in a new routing algorithm), we would love feedback and contributions via GitHub issues and pull requests.
