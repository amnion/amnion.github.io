---
title:  "spikejungle classifier"
layout: post
---

## Problem: large-scale noise in neuroscience
Neuroscientists recording electrical activity from brains produce continuous voltage signals containing two types of events: real neural spikes — electrical impulses neurons use to communicate — and noise coming from electrical interference or movement of the recording subject. Before any analysis can begin, the two must be separated. For many of the thousands of labs conducting such experiments, this is done manually by expert reviewers, event by event, hour by hour.

<img src='/assets/images/spikejungle_fig1.png'>

Left: a clean recording segment, with real spikes (black arrowheads) showing their characteristic waveform shape. Right: the same recording contaminated by motion artifacts (red arrowheads) — bursts of electrical noise that dwarf the real signal and must be removed before analysis.

Manual review doesn't scale. Across a single experiment, a recording session may contain tens of thousands of candidate events. Across a research program — multiple subjects, multiple sessions, multiple years — the volume becomes the bottleneck for progress. Review is also subjective: different reviewers draw the line differently, introducing inconsistency into the data that underlies published findings.

I built SpikeJungle to solve this.

## Solution: an ensemble classifier trained on expert work
SpikeJungle is a multiple-classifier system that automates noise removal from voltage recording data. The core idea is that rather than trusting any single model, three independent classifiers vote on each event (spike or noise) and the majority rules. Disagreement between classifiers is informative because it flags ambiguous cases for targeted review.

The system was trained and validated on two labeled datasets totaling 155 GB and 411 million observations. These were real experimental data, not benchmarks. Training classes were severely imbalanced: 93% of events were real spikes and 7% were noise. Standard training caused models to never predict noise. I corrected this by training on balanced random subsets sampled without replacement, equalizing class representation while preserving the statistical properties of each class.

I systematically compared 5 feature extraction strategies — raw waveforms, wavelets, wavelet scattering, PCA, and hand-engineered features — across 3 classifier families: Support Vector Machines (SVM), Random Forests (RF), and Kernel Density Estimates (KDE). Raw waveforms and wavelets outperformed hand-engineered features across the board, with Random Forest and SVM performing best overall.

<img src='/assets/images/spikejungle_fig8.png'>

The full pipeline on a real recording. Panel A: raw input data visualized as a heatmap — each row is one candidate event, time on the x-axis, voltage on the y-axis. The wide horizontal bands of fluctuation are noise clusters. Panel B: predictions from each of the three classifiers (SVM, RF, KDE) aligned to the input — black rows are predicted spikes, light rows are predicted noise. Panel C: the same data plotted as voltage traces over time, with noise events flagged in red by each classifier independently, and removed by majority vote in the final panel. Panel D: accepted spike waveforms (black) and rejected noise waveforms (red). Panel E: agreement statistics — in this example, all three classifiers agreed on 87.97% of predictions.

Full pipeline on a real recording channel with noise. (a) Raw input events as a heatmap - rows are candidate events. Time is on the x-axis and color is mean voltage (low to high). (b) Predictions from of each classifier (SVM, RF, KDE) aligned to the input in (a). Light blue rows are where the signal passes the "noise-check". Black rows are where a model rejected the event. (c) Shows the same events as in (a-b) over time. Movement artifacts by the subject are obvious as "streaks" or "tears" running down the panels in (c). (d) Waveforms of accepted (black) and rejected (red) events. (e) Agreement statistics. Here, the 3 classifiers agreed on 87.97% of predictions.

## Results
Across 32 experiments on new, unseen data, unanimous classifier agreement ranged from 74–92%. The system successfully isolated noise clusters while retaining real spikes. But, the most important validation wasn't accuracy on held-out data. It was biological: I confirmed that the stimulus response of neurons — the signal that drives scientific conclusions — was preserved after cleaning, not degraded by it.

<img src='/assets/images/spikejungle_fig9.png'>

Validation on a real experiment. Panel A: the audio waveform of a birdsong stimulus presented to the subject. Panels B and C: raster plots of one neuron's spike responses to the same stimulus, before (B) and after (C) classifier-based noise removal. Each tick mark is a spike; each row is one trial. The temporal structure of the neural response — the patterns that encode information about the stimulus — is preserved after cleaning. The noise is gone; the signal is intact.

SpikeJungle eliminated hundreds of hours of manual review labor across multiple ongoing research projects and was adopted by three independent research teams. It is available on [GitHub]().

---

*The full write-up, including feature engineering comparisons, classifier architectures, and validation methodology, is available as a [PDF here](/assets/docs/spikejungle_writeup.pdf).*