---
title:  "laboratory in justice data science"
layout: post
---

In the spring of 2022 and 2024 I co-developed, co-taught and wrote the assignments for a new Columbia University course, *Laboratory in Justice Data Science*, with [Geraldine Downey](https://psychology.columbia.edu/content/geraldine-downey) and [Niall Bolger](https://psychology.columbia.edu/content/niall-bolger). Graduate and undergraduate students developed quantitative analytical skills for influencing policy decisions and evaluating social and criminal justice issues. I wrote and taught 20 hours of lectures and 7 assignments on data science principles, programming, communication and ethics.

Below is an example slide I used to open a discussion on the wrong and right ways to visualize data. Students learned to create graphics like this in R, and many other skills. We worked on skills spanning fundamentals like boolean indexing and regular expressions, to advanced modeling with random forests and neural networks. Each lesson was rooted in a justice-related issue that was assessed quantitatively, such as systemic racial bias in data used to create predictive models of crime. 

<img width=600 src='/assets/images/jds_screengrab.png'>

Students found my teaching style effective. Here are their evaluations of me (excerpts below): [2022](/assets/docs/evals_jds_2022.pdf) |
[2024](/assets/docs/evals_jds_2024.pdf)
> Have Jacob to thank for teaching me R! Such a helpful and knowledgeable TA

> Lowkey wish I could have just taken his part of the class.

I am most proud of the assignments I wrote for the course, and students found them valuable. Feedback on my assignments included comments such as:
> I found this assignment very cool and I feel like I learned a lot. I'm glad that we use real world examples because I like that I think about the assignment even after it is turned in.

> Thank you again for all the amazing labs and very thoughtful assignments! This class is definitely one of the most amazing classes I have ever had. And it added a lot on my data analyzing skills, which I believe would be helpful for me.

Students' capstone projects blew my mind each semester. Projects were policy proposals that included deep analyses of issues such as the propagation of violence through networks of gangs in Brooklyn, New York, migration of talent out of East Coast cities due to anti-LGBTQ policies ("brain drain"), and [geographic relationships between rates of police force use and domestic violence](https://journals.sagepub.com/doi/full/10.1177/10778012251369024).

---

Below is the full curriculum for my part of the course:

|------------------------------------------------------|
|  | Lecture | Description | Assignment | Data sources |
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
