---
title:  "Laboratory in justice data science"
layout: post
---

In the spring of 2022 and 2024 I developed, taught and wrote the assignments for a new Columbia University course, *Laboratory in Justice Data Science*, led by [Geraldine Downey](https://psychology.columbia.edu/content/geraldine-downey) and [Niall Bolger](https://psychology.columbia.edu/content/niall-bolger). Graduate and undergraduate students developed serious analytical skills for influencing policy decisions. Below are details about my part of the course, including my full curriculum and assignments or R code.

Capstone projects were policy proposals that included deep analyses of issues such as the propagation of violence through New York gangs networks, migration of talent out of East Coast cities due to anti-LGBTQ policies ("brain drain"), and [geographic relationships between rates of police force use and domestic violence](https://journals.sagepub.com/doi/full/10.1177/10778012251369024).

See my teaching reviews here: 
[2022](/assets/docs/evals_jds_2022.pdf) |
[2024](/assets/docs/evals_jds_2024.pdf)

<img src='/assets/images/jds_screengrab.png'>

Feedback on my assignments included comments such as:
> I found this assignment very cool and I feel like I learned a lot. I'm glad that we use real world examples because I like that I think about the assignment even after it is turned in.

> Thank you again for all the amazing labs and very thoughtful assignments! This class is definitely one of the most amazing classes I have ever had. And it added a lot on my data analyzing skills, which I believe would be helpful for me.

---

|-----------------------------------------------------|
|  | Topic | Description | Data sources | Assignment |
|-----------------------------------------------------|
| 1 | Software choices | Why write code? Comparing and contrasting Python and R. | [Stanford Open Policing](https://openpolicing.stanford.edu/) | [Assignment 1](/jds assignments/A1 software choices.pdf)
| 2 | Online data | Getting data the easy and hard ways. APIs. Parsing HTML and building a spider. | [Wikipedia](https://www.wikipedia.org/) | [Assignment 2](/jds assignments/A2 online data.html)
| 3 | Data wrangling | Tables. Logical indexing and regular expressions. Learning different words for the same things (de-jargonization). | [NYC OpenData](https://opendata.cityofnewyork.us/) | [Assignment 3](/jds assignments/A3 data wrangling.html)
| 4 | Visualization I | Classic plots and classic blunders. Bar, box, and scatter. Tufte principles. Getting involved in land wars in Asia. | [NYC OpenData](https://opendata.cityofnewyork.us/) | [Assignment 4](/jds assignments/A4 data visualization I.html)
| 5 | Visualization II | Dimensions, and how to graph more than two of them. Making maps with shapefiles, APIs and custom R functions. | [Snow Cholera Map Data](https://blog.rtwilson.com/john-snows-famous-cholera-analysis-data-in-modern-gis-formats/) | [Assignment 5](/jds assignments/A5 data visualization II.html); [NYC Community Districts shapefile exercise](/jds assignments/SQF shapefile mapping.html)
| 6 | Predictive analytics I | Models, explaining and predicting. Random forests. Fairness and bias. | [*ProPublica:* COMPAS Recidivism](https://projects.propublica.org/datastore/#compas-recidivism-risk-score-data-and-analysis) | [Assignment 6](/jds assignments/A6 predictive analytics I.html)
| 7 | Predictive analytics II | Fairness and bias, again. Neural networks. The importance of scale and how to change it. "Garbage in, garbage out". | [*NIJ:* 2021 Recidivism Forecasting Challenge](https://nij.ojp.gov/funding/recidivism-forecasting-challenge) | [Assignment 7](/jds assignments/A7 predictive analytics II.html)
| 8 | Network analyses | Degrees, centrality and cohesion. Neighborhoods, contagion and cascades. Simulations for null hypothesis testing. | [Rostami & Mondani 2015](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0119309); [Andrew Wheeler's blog](https://andrewpwheeler.com/2020/10/25/open-source-criminology-related-network-datasets/) | [Lab 8 Code](/jds assignments/lab-8-r-code-networks.html)
| 9 | Mining social media | Quantifying meaning in words. Sentiment analysis. Lexicons, tokens, bigrams and clustering. | [*Science:* The spread of true and false news online](https://www.science.org/doi/10.1126/science.aap9559); [r/cats](https://www.reddit.com/r/cats/); [r/news](https://www.reddit.com/r/news/) | [Lab 9 Code](/jds assignments/lab-9-r-code.html)
| 10 | Meta-analysis | Pursuit of understanding. Theories, hypotheses, evidence. What is data, anyway? Prior plausibility and snake oil. | [Homeopathy meta-analysis](https://link.springer.com/article/10.1186/s13643-017-0445-3) | -