---
title: "Poster Presentation at SNS4SNS in Sophia Antipolis"
description: "Presenting our poster on rethinking NTN architecture with 6G-RUPA for scalable and energy-efficient LEO satellite networks."
date: 2026-02-06
lastmod: 2026-02-06
categories:
    - "news"
tags:
    - "6G-RUPA"
    - "NTN"
    - "Poster"
    - "SNS4SNS"
    - "LEO"
---

I recently headed to Sophia Antipolis to present our latest poster, **"Rethinking NTN Architecture: Leveraging 6G-RUPA for Scalable and Energy-Efficient LEO Networks,"** at the SNS4SNS event.

The core of the research is about tackling the "power vs. performance" wall in satellite mega-constellations like Starlink. Here's the quick breakdown of what I presented:

## The Problem

Traditional IP routing is too "heavy" for satellites. It requires massive forwarding tables that drain battery life and struggles to keep up when satellites are moving at thousands of miles per hour.

## Our Solution

We propose 6G-RUPA, a system that uses **topological addressing**. Instead of a fixed ID, each satellite gets an address based on its "neighborhood" in the constellation -- think of it like a dynamic zip code.

## The Result

Our simulations (using our open-source tool, **LEOPath**) show we can slash the size of forwarding tables and keep the network stable, even as satellites zoom in and out of range.

## The Trade-off

While data might take a slightly longer path, the energy savings and scalability for 6G are a massive net win.

---

It was great to discuss these trade-offs with the community in France. If you're interested in the math behind our hierarchical wrap-around distance formulas or want to try out the LEOPath simulator yourself, feel free to [reach out](/contact/)!
