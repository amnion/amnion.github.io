---
title:  "spikejungle classifier"
layout: post
---

*A 3-classifier ensemble (SVM, Random Forest, KDE) that automated quality screening of voltage recordings, trained on 411M+ labeled observations across 155 GB. Eliminated hundreds of hours of manual review per research program and was adopted by 3 independent research teams as standard tooling.*

**At a glance**

| Role | Sole designer, builder, and deployer |
| Stack | MATLAB, scikit-learn-style ensemble methods, custom feature pipelines |
| Training data | 411M+ labeled observations · 155 GB · 2 published datasets |
| Validation | 32 unseen experiments · 74-92% inter-classifier agreement |
| Deployment | Adopted by 3 indepent research teams, plus my own |
| Code | [GitHub](https://github.com/amnion/spikejungle) (*repository forthcoming*) · [Full technical write-up (PDF)](/assets/docs/spikejungle_writeup.pdf) |

## The problem
Brain recordings produce continuous voltage signals containing two kinds of events: real neural spikes (the actual signal) and noise from electrical interference and subject movement. Across thousands of labs worldwide, the two are still separated **by hand** — expert reviewers screening events one by one, hour by hour.

This doesn't scale. A single experiment generates tens to hundreds of thousands of candidate events. A research program — multiple subjects, multiple sessions, multiple years — generates tens of millions. Manual review becomes the bottleneck for the entire scientific process. It is also subjective: different reviewers draw the noise/signal line differently, introducing inconsistency into the published record.

<img src='/assets/images/spikejungle_fig1.png'>

*Left: a clean recording segment with real spikes (black arrowheads). Right: the same recording contaminated by motion artifacts (red arrowheads) — bursts of electrical noise that dwarf the real signal.*

I built SpikeJungle to remove this bottleneck.

---

## What I built
A multiple-classifier system that automates noise removal. Three independent classifiers vote on each candidate event; majority rules; disagreement between classifiers is itself informative because it flags ambiguous events for targeted human review.

**Three classifiers, by design.** Single-model systems fail in opaque ways on edge cases. An ensemble where models disagree gives you a built-in confidence signal: 3-way agreement is high-confidence; 2-vs-1 splits are routed to human review; this turns "this model gave a wrong answer" into "this event is genuinely ambiguous." 

**Class imbalance was a real problem.** 93% of events were real spikes; 7% were noise. Standard training caused models to never predict the minority class — they learned to optimize accuracy by always saying "spike." I solved this with balanced subsampling without replacement: each training round sampled equal-sized subsets from each class, preserving within-class statistical properties while equalizing representation across classes.

**Five feature representations × three classifier families.** I systematically compared raw waveforms, wavelets, wavelet scattering, PCA, and hand-engineered features against SVM, Random Forest, and KDE. Raw waveforms and wavelets outperformed hand-engineered features across the board; RF and SVM performed best overall. The hand-engineered features — the kind a domain expert would design first — were the worst performers, which is itself an interesting finding about where ML beats domain intuition.

<img src='/assets/images/spikejungle_fig8.png'>

*Full pipeline on one recording channel. A: raw input events as a heatmap; rows are candidate events, x-axis is time, color is voltage. B: predictions from each classifier (SVM, RF, KDE) aligned to the input — light rows accepted, black rows rejected. C: the same events plotted over time, with classifier-rejected noise highlighted in red and the cleaned majority-vote output in the bottom panel. D: accepted spike waveforms (black) vs. rejected noise (red). E: classifier agreement statistics — in this example, all three classifiers agreed on 87.97% of predictions.*

## Results
Across 32 unseen experiments, unanimous 3-classifier agreement ranged from 74–92%. The system isolated noise clusters while retaining real spikes.

But accuracy on held-out data wasn't the validation that mattered most. **The validation that mattered was biological:** the actual signal — neurons' temporal responses to stimuli, which is what the science depends on — had to survive cleaning intact. If cleaning the noise also degraded the signal, the tool would be worse than useless.

<img src='/assets/images/spikejungle_fig9.png'>

*Stimulus-response validation. A: audio waveform of a birdsong stimulus. B–C: raster plots of one neuron's response to the same stimulus, before (B) and after (C) classifier-based cleaning. Each tick is a spike; each row is one trial. The temporal structure that encodes information about the stimulus is preserved. Noise is gone; signal is intact.*

**Impact:** SpikeJungle eliminated hundreds of hours of manual review labor across multiple ongoing research programs (an estimated 4–5 hours saved per experiment, across 300+ experiments) and was adopted by **3 independent research teams** besides my own as standard preprocessing. The disagreement-flagging design meant teams could trust the system on the easy cases (most events) and focus expert review on the genuinely ambiguous ones — where their judgment was actually adding value.

---

*Full technical write-up with feature engineering comparisons, hyperparameter search, and validation methodology is available [as a PDF](/assets/docs/spikejungle_writeup.pdf).*

*Want to talk about ML for sensor data? [Get in touch](mailto:jacobedwards.jae@gmail.com) or [see the rest of my work](/).*

---