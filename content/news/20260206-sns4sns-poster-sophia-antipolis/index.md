---
title: "Poster Presentation at SNS4SNS in Sophia Antipolis"
description: "We presented a poster at SNS4SNS (Sophia Antipolis) on rethinking NTN routing with 6G-RUPA for scalable, energy-efficient LEO networks."
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

I traveled to Sophia Antipolis to present our poster at **SNS4SNS**:

"Rethinking NTN Architecture: Leveraging 6G-RUPA for Scalable and Energy-Efficient LEO Networks"

If you just want the key idea: we show how to make routing in LEO mega-constellations lighter-weight by replacing bulky, frequently changing IP forwarding state with a topological address that follows the constellation geometry.

The core of the research is about tackling the "power vs. performance" wall in satellite mega-constellations like Starlink. Here's the quick breakdown of what I presented:

## Why this matters

LEO networks have an uncomfortable combination of constraints: fast topology changes, strict energy budgets, and a need to scale to very large constellations. Traditional IP-style routing can become too "heavy" in this setting because it relies on large forwarding tables and frequent updates to react to mobility.

## What we propose

We explore **6G-RUPA** using **topological addressing**. Instead of treating each satellite as a fixed identifier that the network must constantly track, the address reflects a satellite's *position in the constellation graph* (you can think of it as a "dynamic zip code" tied to the neighborhood).

## What we observe

Using our simulator **LEOPath**, we see that this approach can significantly reduce forwarding state while keeping the network stable as satellites move and links appear/disappear.

## The trade-off

The trade-off is that paths can be slightly longer in some cases, but the reduction in routing overhead and the energy/scalability benefits are compelling for future NTN designs.

---

## Poster (PDF)

{{< pdf src="sns4sns_poster_6grupa_ntn.pdf" title="SNS4SNS poster: Rethinking NTN Architecture with 6G-RUPA" height="920" >}}

It was great to discuss these trade-offs with the community in France. If you'd like more details (e.g., the hierarchical wrap-around distance formulas) or want to try **LEOPath**, feel free to [reach out](/contact/).
