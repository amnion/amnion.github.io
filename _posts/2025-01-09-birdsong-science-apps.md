---
title:  "Birdsong science apps"
layout: post
---

During my Ph.D., I wrote a lot of software for data management, analysis and visualization. Data were usually audio recordings of birds singing, or electrical recordings of birds' brain activity while they listened to songs. Below are short descriptions and screenshots of a few apps I wrote to help me work. They were written mostly using MATLAB's App Designer. Contact me if you are interested in using any for your own projects.

---

## Ephys Explorer
Interface for exploring single-neuron activity recorded from high-density electrodes implanted in the brains of songbirds. The animation below is a crop from the interface showing 1,698 neurons from the auditory cortices of 5 double-barred finches responding to a song of their own species, slowed down about 100x. Neurons are points in 3D brain space (stereotaxic coordinates) with point size showing spike rate. The two point clouds are the left and right brain hemispheres. The white line is a frequency power spectrum of the stimulus (0-10 kHz, left to right), and the stimulus song spectrogram is below with a red line showing the current moment in time. 

<img src='/assets/images/ephys_explorer.gif'>

---

## Ephys Decoder
Interface collecting multiple analyses of neural population decoding, including population trajectories with PCA ([Churchland et al. 2012](https://www.nature.com/articles/nature11129)) and stimulus reconstruction ([Mesgarani & Chang 2012](https://www.nature.com/articles/nature11020)).

This is cool: click the speaker on the left to hear an actual zebra finch song that a zebra finch listened to. Next, click the speaker on the right to hear the same song "reconstructed" from the spike activity of that zebra finch's auditory cortex neurons!

| real stimulus | reconstructed stimulus |
|----------------------------------------|
| [sound of real](/assets/docs/stim_real.mp4) | [sound of recon](/assets/docs/stim_recon.mp4) |

It's not great, but you can hear IT XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

<img src='/assets/images/ephys_decoder.png'>

---

## SylLabeler
Data annotation interface to help with labeling syllables in birdsong. Sequence analyses require discrete, labeled units (e.g. ABCABCABC). For speech this is intuitive because words and phonemes are discrete units. For instance, the probability that *"discrete"* comes before *"units"* is pretty high. For other animal vocalizations, like birdsong, units have to be classified and labeled based on their acoustic properties. I used this app for several projects to label and keep track of tens of thousands of syllables and dozens of tutor-pupil relationships. It also implements dimensionality reduction and basic clustering to help with the visual and acoustical classification of song syllables into types.

<img src='/assets/images/syllabeler.gif'>

---

## Brain Maker
In 2019 I had an idea for a side project to do a network meta-analysis on the known auditory-vocal connectivity between regions in the songbird brain. Despite decades of study, it is still unclear how tutors' song auditory information enters the song production and learning system, and I reasoned that a full picture of the known circuitry could help. I built this app as a tool to help aggregate details in published anatomical studies, like type of tracer used, volume injected, species, *etc.* I built the app and started inputting data, but never finished it. It seems [Savoy, Anderson and Gogola (2024)](https://link.springer.com/article/10.1186/s12868-024-00919-3) at [oscine-net.org](https://oscine-net.org/) had the same idea and did a better job, anyway!

<img src='/assets/images/screen_of_screen.png'>