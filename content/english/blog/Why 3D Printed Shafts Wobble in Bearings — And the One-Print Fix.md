---
title: "Why 3D Printed Shafts Wobble in Bearings — And the One-Print Fix"
meta_title: ""
description: "this is meta description"
date: 2026-05-12T08:00:00Z
image: "/images/Why 3D Printed Shafts Wobble in Bearings — And the One-Print Fix.jpg"
categories: ["3D printing"]
author: "Ethan Pathwell"
tags: ["3D print bearing fit · shaft tolerance", "3D printing"] 
draft: false
---

If you've ever pressed a 3D printed shaft into a 608ZZ bearing only to watch it wobble or tilt, you're not alone — and you're not doing anything wrong. The problem is tolerance, and it's surprisingly easy to solve once you understand what's happening.

## The default assumption that breaks things

Most CAD guides suggest leaving 0.3 to 0.5 mm of clearance for 3D printed fits. Roughly 0.3 mm gives a tight fit, 0.5 mm is loose, and around 0.45 mm allows rotation. Those numbers work well in theory — but FDM printing doesn't care about theory.

When I designed a shaft for a 608ZZ bearing using standard clearance values, the fit was far too loose. The shaft wobbled and even tilted inside the bearing race, which completely defeats the purpose of using a bearing in the first place.


## The calibration model approach

Rather than guess-and-reprint, I built a simple calibration model with a range of labeled shaft and hole sizes. You print it once, test each size by pressing a bearing onto the shaft, check for wobble, and confirm the inner ring locks while the outer ring spins freely.

With ABS, the sweet spot turned out to be 8.2 mm for an 8 mm target. It's a firm press fit — you'll need a little force — but once seated, it behaves exactly like it should. For PETG, 8.1 mm works well for both shaft and hole fits around 8 mm components. Different plastics shrink differently, so the model takes the guesswork out entirely.


## Dialing it in through your slicer

Once you know your target dimension, adjustments are straightforward. In Bambu Studio, the "XY contour compensation" setting controls outer dimensions like shafts, while "XY hole compensation" adjusts hole sizes. You can also tweak directly in CAD — whatever fits your workflow.


Print the calibration model once and you'll have a material-specific reference you can reuse for every project. It's a small upfront investment that eliminates every "why doesn't this fit?" moment going forward.

[Download the free calibration model ](https://makerworld.com/en/models/2793240-3d-print-bearing-fit-shaft-tolerance-3d-printing#profileId-3106267 "3D print bearing fit · shaft tolerance 3D printing")

## Youtube video

{{< youtube 5_-kzyiLu1A >}}