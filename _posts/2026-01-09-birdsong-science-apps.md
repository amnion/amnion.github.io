---
title:  "data science tools"
layout: post
---

Collection of tools I built for data management, analysis, and visualization, primarily on large-scale time-series datasets from acoustic and electrophysiological experiments.

---

## Ephys Explorer
Custom 3D visualization tool for exploring how individual neurons in a living brain respond to sound in real time and across both hemispheres.

The animation shows 1,700 neurons lighting up as a bird hears one of its own species' songs. Each point in space is a neuron; its size shows how rapidly it's firing. The two clouds are the left and right auditory cortex. The sound's frequency spectrum scrolls in real time above the spectrogram, so you can watch the brain tracking the structure of the song as it unfolds, slowed down 100× so the dynamics are visible.

Built to support exploratory analysis across large multi-electrode recording sessions. The interface made it possible to spot spatial patterns, outliers, and stimulus-response structure that would be invisible in a table or a standard 2D plot.

<img src='/assets/images/ephys_explorer.gif'>

---

## SpikeJungle
Random forest classifier that automates the noisiest step in neural data collection: distinguishing real electrical signals from movement artifacts and equipment noise.

Manual cleaning of electrophysiology recordings is tedious, error-prone, and hard to scale. A single experiment can produce hours of data requiring expert review, spike-by-spike. SpikeJungle eliminated hundreds of hours of that work by training on ground truth labels from two published datasets ([Moore & Woolley 2019](https://www.nature.com/articles/s41593-019-0458-4); [So, Edwards & Woolley 2020](https://www.jneurosci.org/content/40/5/1015)) and generalizing well to new recordings.

The plot below shows a representative example. The subject started moving halfway through the recording session, flooding the channel with artifacts (red). The classifier separates them from real neural spikes (black) without manual intervention. This [manuscript](/assets/docs/spikejungle_writeup.pdf) gives more detail on the problem structure and modeling solution.

<img src='/assets/images/spike_jungle.png'>

---

## Ephys Decoder
What does a brain actually hear? This tool applies neural population decoding algorithms to reconstruct the sound information that a bird's auditory cortex encoded while listening to a song.

Click the left audio file to hear the real song stimulus. Click the right to hear that same song reconstructed entirely from the neural activity of the same neurons shown in the Ephys Explorer above. This is what hearing sounds like from the inside.

| [real song](/assets/docs/stim_real_proc.wav) | [reconstructed song](/assets/docs/stim_recon_proc.wav) |

The tool also implements latent space analysis to visualize the geometry of neural population dynamics during sound processing.

<img src='/assets/images/ephys_decoder.png'>

---

## SylLabeler
Database management and annotation tool for structuring raw audio data into labeled sequences suitable for NLP-style analysis.

Sequence modeling requires discrete, labeled units the same way NLP needs words before it can model sentences. For animal vocalizations, those units don't arrive pre-segmented: they have to be identified, classified, and tracked across tens of thousands of events and hundreds of subjects. SylLabeler replaced a fragmented, manual workflow with a single interface that handled segmentation, labeling, dimensionality reduction, and cluster-based classification in one place.

Used across multiple projects and adopted by other teams in the lab. The GIF below shows the interface in action.

<img src='/assets/images/syllabeler.gif'>

---

## Brain Maker
Prototype meta-analysis and network visualization tool for synthesizing findings across published anatomical studies.

The problem: decades of neuroscience research on auditory-vocal brain circuits exist scattered across hundreds of papers, with no unified, queryable database of the connectivity. I designed and built Brain Maker to help solve that. It's a structured interface for ingesting study metadata (tracer type, injection site, species, connectivity outcome) and rendering the known circuit as an interactive network graph.

The project reached a working prototype stage before I paused it to focus on dissertation work. In the interim, another research team independently pursued the same idea and released [oscine-net.org](https://oscine-net.org/), which I take as validation that the problem was real and the approach was sound. The screenshot below shows the data entry and network visualization interface.

<img src='/assets/images/screen_of_screen.png'>