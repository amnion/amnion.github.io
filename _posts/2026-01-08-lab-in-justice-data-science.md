---
title:  "laboratory in justice data science"
layout: post
---

We built this course around the conviction that data skills are best learned when the data matter. Each lesson was grounded in a real policy problem. Examples included racial bias in recidivism prediction algorithms, geographic patterns of police use of force, and the spread of misinformation through social networks. Students left able to wrangle, model, visualize, and explain what their results meant for people. Two of their capstones reached publication, including one in a peer-reviewed journal.

*Laboratory in Justice Data Science* ran in spring 2022 and 2024 at Columbia, co-designed and taught with [Geraldine Downey](https://psychology.columbia.edu/content/geraldine-downey) and [Niall Bolger](https://psychology.columbia.edu/content/niall-bolger). I wrote and taught 20 hours of original lectures and 7 hands-on assignments covering the full stack: APIs and web scraping, data wrangling, visualization, predictive modeling, algorithmic fairness, NLP, network analysis, and meta-analysis. All in R, on real datasets with real policy stakes. Students rated my teaching highly: [2022](/assets/docs/evals_jds_2022.pdf) · [2024](/assets/docs/evals_jds_2024.pdf). Below are three lessons that highlight the breadth and depth of skills and issues covered:

| --- |
| [COMPAS fairness](/jds assignments/A6 predictive analytics I.html) | [NIJ recidivism](/jds assignments/A7 predictive analytics II.html) | [Geospatial analysis](/jds assignments/A5 data visualization II.html) |
| --- |
| <img src='/assets/images/thumb_jds_1.png'> | <img src='/assets/images/thumb_jds_2.png'> | <img src='/assets/images/thumb_jds_3.png'> |
| **Random forests + algorithmic fairness audit.** Train a random forest on real recidivism data, then audit it for racial bias. Does the model make different kinds of errors for Black and White defendants? |  **Neural networks + feature interpretation.** Build neural networks from scratch on a national recidivism dataset. Students interrogate which input variables carry predictive power and which may be racial proxies in disguise. |  **Mapping tools + advanced ggplot2.** From John Snow's 1854 cholera map to live NYC arrest records — heat maps, shapefiles, and pulling data directly from city APIs. |

**What students said:**
> I found this assignment very cool and I feel like I learned a lot. I'm glad that we use real world examples because I like that I think about the assignment even after it is turned in.

> Thank you again for all the amazing labs and very thoughtful assignments! This class is definitely one of the most amazing classes I have ever had. And it added a lot on my data analyzing skills, which I believe would be helpful for me.

Students produced original policy proposals as capstone projects. Examples of what they built:

• Geospatial analysis of the relationship between police use-of-force rates and domestic violence incidence across NYC precincts. [Published](https://journals.sagepub.com/doi/full/10.1177/10778012251369024) in the peer-reviewed journal *Violence Against Women*.

• Risk analysis of cybersecurity breaches in relation to AI, indicating that low-income regions of the US are at the highest security risk. [Published](https://www.culawreview.org/) in the *Columbia Undergraduate Law Review*.

• Network analysis of violence propagation through gang affiliations in Brooklyn, using graph centrality to identify highest-leverage intervention points.

• Demographic analysis of talent migration out of East Coast cities in response to anti-LGBTQ legislation, showing "brain drain" in economic and human capital terms.
 
**Most students entered the course with little to no coding experience. All of them exited with serious data chops.** Gabriella declared Statistics as a major and went on to work with Columbia's Center for Justice for several years. Haleigh used what she learned about R and NLP to pursue a Master's in Global Media and Communications at the London School of Economics. Gianna honed in on geospatial analysis and went on to obtain a Master's in Urban Data Science at NYU.

These outcomes are what the course was for.

---

**The full curriculum for my part of the course is below.** Each `lecture` links to my Powerpoint slides, each `assignment` to the R markdown document students worked from, and each `data source` to the real-world data used.

|------------------------------------------------------|
|  | Lecture | Description | Assignment | Data source |
|------------------------------------------------------|
| 1 | [Software choices](/assets/jds ppts/lab 1 ppt - software choices.pdf) | Why write code? Comparing and contrasting Python and R. | [Assignment 1](/jds assignments/A1 software choices.pdf) | [Stanford Open Policing](https://openpolicing.stanford.edu/)
| 2 | [Online data](/assets/jds ppts/lab 2 ppt - online data sources.pdf) | Getting data the easy and hard ways. APIs. Parsing HTML and building a spider. | [Assignment 2](/jds assignments/A2 online data.html) | [Wikipedia](https://www.wikipedia.org/)
| 3 | [Data wrangling](/assets/jds ppts/lab 3 ppt - data wrangling.pdf) | Tables. Logical indexing and regular expressions. Learning different words for the same things (de-jargonization). | [Assignment 3](/jds assignments/A3 data wrangling.html) | [NYC OpenData](https://opendata.cityofnewyork.us/)
| 4 | [Visualization I](/assets/jds ppts/lab 4 ppt - effective visualization I.pdf) | Classic plots and classic blunders. Bar, box, and scatter. Tufte principles. Getting involved in land wars in Asia. | [Assignment 4](/jds assignments/A4 data visualization I.html) | [NYC OpenData](https://opendata.cityofnewyork.us/)
| 5 | [Visualization II](/assets/jds ppts/lab 5 ppt - effective visualization II.pdf) | Dimensions, and how to graph more than two of them. Making maps with shapefiles, APIs and custom R functions. | [Assignment 5](/jds assignments/A5 data visualization II.html); [NYC Districts exercise](/jds assignments/SQF shapefile mapping.html) | [Snow's 1854 Cholera Map Data](https://blog.rtwilson.com/john-snows-famous-cholera-analysis-data-in-modern-gis-formats/)
| 6 | [Predictive analytics I](/assets/jds ppts/lab 6 ppt - predictive analytics I.pdf) | Models, explaining and predicting. Random forests. Fairness and bias. | [Assignment 6](/jds assignments/A6 predictive analytics I.html) | [*ProPublica:* COMPAS Recidivism](https://projects.propublica.org/datastore/#compas-recidivism-risk-score-data-and-analysis)
| 7 | [Predictive analytics II](/assets/jds ppts/lab 7 ppt - predictive analytics II.pdf) | Bias and fairness. Neural networks. The importance of scale and how to change it. "Garbage in, garbage out". | [Assignment 7](/jds assignments/A7 predictive analytics II.html) | [*NIJ:* 2021 Recidivism Forecasting Challenge](https://nij.ojp.gov/funding/recidivism-forecasting-challenge)
| 8 | [Network analyses](/assets/jds ppts/lab 8 ppt - social network analysis.pdf) | Centrality and cohesion. Neighborhoods, contagion and cascades. Simulations for null hypothesis testing. | [Lab 8 Code](/jds assignments/lab-8-r-code-networks.html) | [Rostami & Mondani 2015](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0119309); [Andrew Wheeler's blog](https://andrewpwheeler.com/2020/10/25/open-source-criminology-related-network-datasets/)
| 9 | [Mining social media](/assets/jds ppts/lab 9 ppt - mining social media.pdf) | Quantifying meaning in words. Sentiment analysis. Lexicons, tokens, bigrams and clustering. | [Lab 9 Code](/jds assignments/lab-9-r-code.html) | [*Science:* The spread of true and false news online](https://www.science.org/doi/10.1126/science.aap9559); [r/cats](https://www.reddit.com/r/cats/); [r/news](https://www.reddit.com/r/news/)
| 10 | [Meta-analysis](/assets/jds ppts/lab 10 ppt - meta-analysis.pdf) | Pursuit of understanding. Theories, hypotheses, evidence. What is "data", anyway? Prior plausibility and snake oil. | - | [Homeopathy meta-analysis](https://link.springer.com/article/10.1186/s13643-017-0445-3)

*All slides, assignments, and code linked above are available for reuse with attribution. Want to talk about applied data science teaching, curriculum design, or teaching in the age of LLMs? [Get in touch](mailto:jacobedwards.jae@gmail.com) or [see the rest of my work](/).*