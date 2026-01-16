---
title:  "Birdsong science apps"
layout: post
---

During my Ph.D., I wrote a lot of software for data management, analysis and visualization. Data were usually audio recordings of birds singing, or electrical recordings of birds' brain activity while they listened to songs. Below are short descriptions and screenshots of a few programs I wrote to help me work, which were mostly written using MATLAB and R. Contact me if you are interested in using any for your own projects.

---

## Ephys Explorer
Interface for exploring single-neuron activity recorded from high-density electrodes implanted in the brains of songbirds. The animation below is a crop from the interface showing 1,698 neurons from the auditory cortices of 5 double-barred finches responding to a song of their own species, slowed down about 100x. Neurons are points in 3D brain space (stereotaxic coordinates) with point size showing spike rate. The two point clouds are the left and right brain hemispheres. The white line is a frequency power spectrum of the stimulus (0-10 kHz, left to right), and the stimulus song spectrogram is below with a red line indicating the current moment in time. 

<img src='/assets/images/ephys_explorer.gif'>

---

## SpikeJungle
Random forest model used as a noise reduction step in electrophysiological experiments. The model separates real spikes from noise and movement artifacts. I trained it using ground truth data published in [Moore & Woolley 2019](https://www.nature.com/articles/s41593-019-0458-4) and [So, Edwards & Woolley 2020](https://www.jneurosci.org/content/40/5/1015). The model performed very well and saved me hundreds of hours of work.

Model output for a recording channel of a single neuron is shown in the plot below. The subject started moving about halfway through the experiment (clusters of vertical points). The model successfully distinguished movement artifacts (red) from real spikes (black). This [manuscript](/assets/docs/spikejungle_writeup.pdf) gives more detail on the model training, use and visualization.

<img src='/assets/images/spike_jungle.png'>

---

## Ephys Decoder
Interface collecting multiple analyses of neural population decoding, including a type of latent space analysis ([Churchland et al. 2012](https://www.nature.com/articles/nature11129)) and stimulus reconstruction ([Mesgarani & Chang 2012](https://www.nature.com/articles/nature11020)).

This is cool: click the sound on the left to hear the actual double-barred finch song stimulus shown in the Ephys Explorer animation above. Next, click the sound on the right to hear the song "reconstructed" from the spikes of the neurons shown in the same plot!

| [real stimulus](/assets/docs/stim_real.mp4) | [reconstructed stimulus](/assets/docs/stim_recon.mp4) |

<img src='/assets/images/ephys_decoder.png'>

---

## SylLabeler
Data annotation interface to help with labeling syllables in birdsong. Sequence analyses like those used in NLP require discrete, labeled units (e.g. ABCABCABC). For text or speech, this is intuitive because words are already discrete units. For other animal vocalizations, like birdsong, units have to be classified and then labeled based on their acoustic similarities and differences. I made and used this app for several projects to label and keep track of tens of thousands of syllables and dozens of tutor-pupil relationships. It also implements dimensionality reduction and basic clustering to help with classifying song syllables into types.

<img src='/assets/images/syllabeler.gif'>

---

## Brain Maker
In 2019 I had an idea for a side project to do a network meta-analysis on the known connectivity of auditory and vocal regions in the songbird brain. Despite decades of study, it is still unclear how the auditory memory of a tutor's song enters the song production and learning system, and I reasoned that a full picture of the known circuitry could help. I built this app as a tool to help aggregate details in published anatomical studies, like type of tracer used, volume injected, species, *etc.* I built the app and started inputting data, but never finished it. Seems [Savoy, Anderson and Gogola (2024)](https://link.springer.com/article/10.1186/s12868-024-00919-3) at [oscine-net.org](https://oscine-net.org/) had the same idea and did a better job, anyway!

<img src='/assets/images/screen_of_screen.png'>