---
title:  "Noise signatures of real and AI-generated speech and music"
layout: post
---

This post is a work-in-progress!

Being able to tell what is real versus AI-generated is getting harder each day. I was inspired by this [TED talk by Hany Farid](https://www.ted.com/talks/hany_farid_how_to_spot_fake_ai_photos) that describes differences in the distribution of noise in real versus AI-generated images. Real images have a smooth noise distribution because of the physics of light and lenses. AI-generated images have peaked noised distributions because of the diffusion algorithm used to create them. These differences can be easily visualized using a 2D Fourier transform on the image residuals.