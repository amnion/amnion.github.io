---
title:  "scientific visualizations"
layout: post
---

I take pride in turning complex quantitative results into clear and impactful visual stories. The figures below are from my published research on birdsong, sequenced behaviors, and auditory neuroscience.

<img src='/assets/images/datavis_dissertation_brainschematic.png'>

##### Like us, songbird brains contain two interacting systems for vocal communication: one for song production and one for perception, with auditory circuits critical for recognition and learning. My research found that what a bird learns to sing — the sounds of individual syllables — is shaped by experience, while how those syllables are organized in time is constrained by genetics.

---

<img width=600 src='/assets/images/datavis_SciRep.png'>

Birds learn to sing by copying a tutor, but does that also determine how syllables are sung in order (syntax)? To find out, I built a model inspired by natural language processing that predicts a bird's song sequence using only species-level acoustic rules, without ever seeing the tutor's song. This figure shows how a prediction is generated and evaluated from the model. The color grids (top) show how each syllable's acoustic features are matched against species-typical patterns to generate a predicted sequence. The spectrograms (bottom) compare the model's prediction against what the bird actually sang, with a quantitative match score. On average, the model predicted song sequences as accurately as the tutor's own song did — suggesting that syntax in birdsong is shaped by species identity. Like large language models that learn the statistical rules of human language, this model learns the statistical rules of a species' songs — and the approach generalizes to detecting and comparing sequential structure in any complex audio signal, including speech.

**Edwards JA**, Woolley SMN. **2026**. [A species rules syntax model accurately organizes birdsong syllables into songs](https://www.nature.com/articles/s41598-026-44602-5). *Scientific Reports*. In press (*available online*).

---

<img src='/assets/images/datavis_JNeuro.png'>

Birdsong, like speech, has two separable layers: the sounds of individual syllables, and their sequential order (syntax). To pull these apart, I analyzed the songs of birds that were tutored by a different species — then measured whether their song syntax matched their tutor or their own species. This figure shows the comparisons of these songs. Cross-tutored birds learned and sang the foreign syllables, but arranged them in sequences like their own species — sequences they had never heard. Syllables are shaped by experience; syntax is shaped by species' genetics. We supported this finding further by analyzing the songs of untutored birds and genetic hybrids of two species. The findings suggest that sequential organization in learned vocal behavior is somehow encoded in the genome, and have implications for understanding the biological separation of speech sounds from syntax, or grammar, in humans.

**Edwards JA**, Rivera M, Woolley SMN. **2025**. [The temporal organization of learned vocal behavior is predicted by species rather than experience](https://www.jneurosci.org/content/45/11/e0576242025). *Journal of Neuroscience* 45: e0576242025

---

<img src='/assets/images/datavis_dissertation_ephys.png'>

When you hear a sentence or a songbird hears a song, the auditory brain faces two tasks: recognizing the individual sounds, and tracking the timing at which they arrive. This figure shows recordings from individual neurons in the auditory cortex of three songbird species, captured while birds listened to songs. Each tick mark in the raster plots (bottom) is a single neuron firing; each row is one repetition of the same sound. The colored spectrograms above show what the bird was hearing at each moment. The recordings revealed a separation of neural processes that mirrored the hierarchical structure of the behavior: the acoustics of individual syllables were encoded by individual neurons, while the species-specific timing of song was encoded in the precise timing of neurons acting in a circuit. The brain separates "what" from "when" at different levels of its wiring. This separation may explain why birds raised on a foreign tutor's song learn the foreign syllables but sequence them with the timing of their own species — a finding with direct parallels to the neuroscience of human speech perception.

**Edwards JA**. **2025**. [Play with the changes: Innate rules for learned vocal communication in songbirds](https://academiccommons.columbia.edu/doi/10.7916/7bt6-xb79). *PhD Dissertation*. Columbia University.