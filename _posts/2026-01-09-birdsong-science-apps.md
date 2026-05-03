---
title:  "data science tools"
layout: post
---

Collection of tools and GUIs I built for data management, analysis, and visualization, primarily on large-scale time-series datasets from acoustic and electrophysiological experiments.

---

## Ephys Explorer
Custom 3D visualization tool for exploring how individual neurons in a living brain respond to sound in real time and across both hemispheres.

The animation shows 1,700 neurons lighting up as a bird hears one of its own species' songs. Each point in space is a neuron; its size shows how rapidly it's firing. The two clouds are the left and right auditory cortex. The sound's frequency spectrum scrolls in real time above the spectrogram, so you can watch the brain tracking the structure of the song as it unfolds, slowed down 100× so the dynamics are visible.

Built to support exploratory analysis across large multi-electrode recording sessions. The interface made it possible to spot spatial patterns, outliers, and stimulus-response structure that would be invisible in a table or a standard 2D plot.

<img src='/assets/images/ephys_explorer.gif'>

---

## Ephys Decoder
What does a brain actually hear? This tool applies neural population decoding algorithms to reconstruct the sound information that a bird's auditory cortex encoded while listening to a song.

Click the left audio file to hear the real song stimulus. Click the right to hear that same song reconstructed entirely from the neural activity of the same neurons shown in the Ephys Explorer above. This is what hearing sounds like from the inside.

| [🔊 real song](/assets/docs/stim_real_proc.wav) | [🔊 reconstructed song](/assets/docs/stim_recon_proc.wav) |

The tool also implements latent space analysis to visualize the geometry of neural population dynamics during sound processing.

<img src='/assets/images/ephys_decoder.png'>

---

## SylLabeler
Database management and annotation tool for structuring raw audio data into labeled sequences suitable for NLP-style analysis.

Sequence modeling requires discrete, labeled units the same way NLP needs words before it can model sentences. For animal vocalizations, those units don't arrive pre-segmented: they have to be identified, classified, and tracked across tens of thousands of events and hundreds of subjects. SylLabeler replaced a fragmented, manual workflow with a single interface that handled segmentation, labeling, dimensionality reduction, and cluster-based classification in one place.

Used across multiple projects and adopted by other teams in the lab. The GIF below shows the interface in action.

<img src='/assets/images/syllabeler.gif'>
