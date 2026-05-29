---
title: "How to use third-party filament with Bambu AMS"
meta_title: ""
description: "this is meta description"
date: 2026-05-25T08:00:00Z
image: "/images/how to use third-party filament with Bambu AMS.jpg"
categories: ["3dprinting"]
author: "Ethan Pathwell"
tags: ["AMS upgrade", "Bambu Lab AMS", "third-party filament", "3D printing mods","Cell Spool Winder","filament re-spooling"] 
draft: false
---
Cell Spool Winder — Rewind Third-Party Filament for AMS Compatibility

Sometimes the fix isn't on the machine. Sometimes it's on the spool.

If you've been following along with the AMS upgrade journey at Build Path Lab, you already know about the AMS 2 Pro Saver Snag Cutter V5.0 — a snap-fit module that trims filament tails before they can jam your AMS. It's a solid hardware-level solution, and it works well. But even with it installed, occasional cutting failures were still happening.

The culprit wasn't the cutter. The culprit was the filament itself — or more specifically, the spool it came on.

Third-party filament spools can arrive warped, with bent edges, or wound in ways that create tension and tangle risk the moment the AMS starts pulling. The AMS was designed around Bambu Lab's own spool geometry and winding quality. When you deviate from that, you're introducing a variable the system wasn't designed to handle. Hardware mods can compensate for the symptoms. But what if you could eliminate the variable entirely?


That's the idea behind the [Cell Spool Winder](https://makerworld.com/en/models/561571-cell-spool-winder#profileId-481024 "Cell Spool Winder") — a printable tool discovered on MakerWorld that lets you rewind third-party filament directly onto official Bambu Lab spools.


{{< youtube -jXj9LqenKI>}}


## The Concept: Go Upstream
The logic here is clean. Bambu Lab spools are precisely sized and consistently wound. The AMS knows how to work with them. So instead of modifying the AMS to tolerate incompatible spools, you rewind the filament onto hardware the AMS already trusts.

It's a more labor-intensive approach than snapping on a cutter module — but if you're running third-party filament regularly and hitting AMS failures, it targets the root cause rather than the symptom.

## The Process, Step by Step 
### 1. Download and Print the Parts
The Cell Spool Winder files are available on MakerWorld. The part count is low, which keeps assembly straightforward. One note on materials: printing in ABS introduced a warping issue at the base of the parts, which caused the snap-fit clips to fail. If you're printing in ABS, dial in your enclosure temperature and first-layer adhesion carefully — or consider a more warp-resistant material like ASA or PETG for this one.

### 2. Assemble the Winder
Assembly is genuinely simple given how few components are involved. One thing to watch: the retaining ring parts come in different sizes. This isn't immediately obvious from the files, and it made the first assembly attempt unnecessarily difficult. Sort your parts carefully before you start snapping things together.

### 3. Wind the Filament 
This is the most nuanced step, and the tape is the critical variable.

You'll secure the filament to the Bambu Lab spool with adhesive tape at the start of the winding process. The tape needs to be strong enough to hold the filament in place as you begin winding — but weak enough that the AMS can pull the filament free from the tape and spool without resistance when it's time to feed.

That's a narrow target. Too strong and the AMS strains during load. Too weak and the initial wind slips before you get tension established.

Start at a slow speed to let the first layers seat properly. As you approach the tail end of the filament, you'll likely notice the last section has a curve to it. Trim this off. That curved tail is a direct contributor to AMS feed failures — it's believed to result from factories bending the filament to speed up initial winding on the production line. Removing it before you install the spool eliminates one more failure point.

### 4. Install and Print
With the filament re-wound onto a Bambu Lab spool and the tail trimmed clean, install it into your AMS as normal.

## What This Actually Solves

Re-spooling with the Cell Spool Winder addresses two distinct problems in one workflow:

### Tangle risk is eliminated at the source. 
By winding fresh onto a consistent, AMS-compatible spool, you remove the uneven tension and poor winding geometry that third-party spools often carry.

### The curved tail problem is resolved. 
That small bend at the end of a filament spool is easy to overlook and surprisingly damaging over time. Trimming it during re-spooling means it never enters your AMS.

The trade-off is time. This isn't a snap-and-forget upgrade — it's a pre-print workflow step. Whether that's worth it depends on how often you run third-party filament and how frequently you've been hitting AMS failures because of it.


## Honest Notes from the Field

ABS warping caused clip failures on the first print attempt. Material choice for the winder itself matters.

Retaining ring sizing is easy to miss — read the assembly notes carefully before you start.

The tape selection is genuinely tricky and may require some experimentation with different tape types.


## Is This Better Than the Snag Cutter?

It's a different layer of the solution, not a replacement. The Snag Cutter addresses what happens at the AMS inlet. The Cell Spool Winder addresses the spool before it ever enters the machine. Used together, they represent a comprehensive approach to third-party filament compatibility — hardware-level protection plus source-level quality control.

If you're only dealing with occasional issues, the Snag Cutter alone may be enough. If you're running high volumes of third-party filament, or specific brands that consistently cause problems, re-spooling is worth adding to your workflow.



### Where to Learn More
🌐 Website: [Build Path Lab](https://buildpathlab.github.io/Ethan_Pathwell.github.io/ "Build Path Lab Blog")

🖨️ Maker profile: [MakerWorld – Ethan Pathwell](https://makerworld.com/en/@Ethan_Pathwell "Build Path Lab MakerWorld")

📺 YouTube: [Ethan Pathwell](https://www.youtube.com/@Ethan_Pathwell "Build Path Lab Youtube")


