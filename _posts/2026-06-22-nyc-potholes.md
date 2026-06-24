---
title:  "Do 311 calls actually represent New Yorkers’ problems?"
layout: post
---

In a recent job interview for a New York City government data scientist position, I was asked: *"How could you tell if 311 calls represent the problems that most New Yorkers face?"* If you aren't familiar with 311, it's a phone number (and [web portal](https://portal.311.nyc.gov/)) that any citizen can dial to report non-emergency concerns to NYC agencies — noise complaints, heat and hot water outages, and street conditions like potholes. I didn't get the job, but the question lingered with me.

The question is important because NYC [employs roughly 400 people](https://citymeetings.nyc/meetings/new-york-city-council/2024-04-25-1000-am-committee-on-technology/chapter/what-is-the-total-number-of-employees-at-nyc-311/) and [spends tens of millions of dollars annually](https://www.ibo.nyc.ny.us/iboreports/311Apr08.pdf) to run 311. Over [200 city agencies and non-profits](https://www.nyc.gov/mayors-office/news/2023/03/mayor-adams-celebrates-20-years-nyc311-release-state-311-report) rely on the data — 50 million records and counting — to allocate resources, track problems, and shape policy. If 311 doesn't represent the people it's meant to serve, then every decision built on it carries that bias. 

The challenging part of the question is what "represent" *means* quantitatively. During the interview, we agreed to focus on pothole reports, so I did the same here. To compare 311 calls to something independent, I needed a proxy for ground truth. NYC's Department of Transportation (DOT) publishes a Closed Work Orders dataset, which logs every repair the agency completes. It isn't ground truth, but it's a second window into the same problem from a different vantage. It reflects what the city acts on. The **reporting gap**, then, is the difference between two signals: where citizens report potholes, and where the city repairs them.

**TL;DR:** Across 59 community districts and two years of data, **not a single district showed a statistically significant gap between citizens reports and city repairs.** The 311 system, at least for potholes, is doing its job.

<img src='/assets/images/nyc-potholes-figs/fig1_cds.svg'>

##### **Figure 1.** New York City's 59 community districts (CDs) were analyzed. CDs are NYC's official sub-borough planning units, with dedicated civic representation and populations in the 130-200k range. The map shows CDs colored by borough and demarcated by white boundaries. Faded colors show the 12 Joint Interest Areas (parks, airports, and other non-residential zones) excluded from analysis. Inset shows population size for each CD within each borough, with a label for each borough's total population.

To quantify the gap for each NYC community district (CD), I aggregated five open datasets, modeled 311 reports and DOT repairs per road-mile using demographics as predictors, and assessed where the two signals diverged. Technical details are in the table below and on my [GitHub](https://github.com/amnion/nyc-potholes). A Tableau dashboard for exploring the underlying data is coming soon.


| **Data** | [311 Service Requests](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2020-to-Present/erm2-nwe9) · [DOT Repairs](https://data.cityofnewyork.us/Transportation/Street-Pothole-Work-Orders-Closed-Dataset-/x9wy-ing4) · [Community Districts](https://data.cityofnewyork.us/City-Government/Community-Districts/5crt-au7u) · [Street Centerlines](https://data.cityofnewyork.us/City-Government/Centerline/inkn-q76z) · [ACS 5-year](https://www.nyc.gov/content/planning/pages/resources/datasets/american-community-survey) |
| **Stack** | SQL · Python · R · GeoPandas · matplotlib |
| **Model** | Negative binomial regression, offset by road-miles |
| **Inference** | Bootstrapped confidence intervals · Benjamini-Hochberg correction |
| **Code** | [GitHub](https://github.com/amnion/nyc-potholes) |
| **Dashboard** | Tableau Public *(coming soon)* |

In raw numbers, citizens reported 2-3 potholes for every one DOT logged as repaired — in every community district, with no exceptions (**Figure 2**). The constant 2-to-1 ratio is partly a data quirk: a single DOT work order can cover multiple potholes along a street segment, while each 311 call typically reports a single pothole. The more interesting question is whether the **gap** between these two signals varies systematically by district, or whether they vary in lockstep with the underlying demographics that predict the raw counts.

<img src='/assets/images/nyc-potholes-figs/fig2_scatter.svg'>

##### **Figure 2.** Total citizen pothole reports versus DOT work orders, one point per community district, summed over 2023-2024. Point color shows median income, and point size shows total road miles. Every district sits below the 1:1 line. Citizens report 2-3 potholes for every one the city's work-order system records as repaired, a ratio consistent across the income, density, and road-network gradient. 

To compare apples to apples, I built two statistical models in parallel: one predicting citizen 311 reports per road-mile, and the other predicting DOT repairs per road-mile. Each model used the same set of district characteristics as inputs: median household income, percentage renters, percentage foreign-born, and total population. Despite predicting different signals on different scales, both models extracted and made use of the same demographic patterns (**Figure 3**). For each predictor, estimated coefficients in the 311 and DOT models did not statistically differ. Higher-income districts generated more 311 calls and more DOT repairs. Districts with more renters generated more of both. Foreign-born share, to a lesser extent, predicted more of both. Whatever drove citizens to call 311 was the same thing that drove city operations to close work orders.

Notably, both signals scaled up with district income. Wealthier districts produced more 311 calls *and* more DOT work orders per road-mile, controlling for population and infrastructure. Civic engagement with municipal systems scaled with affluence on both sides of the citizen-government line.

<img src='/assets/images/nyc-potholes-figs/fig3_coefficients.svg'>

##### **Figure 3.** Standardized coefficients from two parallel negative binomial regressions: one predicting citizen 311 reports per road-mile, one predicting DOT work orders per road-mile. Points represent coefficient estimates, and lines show 95% confidence intervals.

The **gap** was in the *difference* between what each model predicts and what actually happened. If 311 reports exceeded model expectations in a district where DOT repairs didn't, that was a citizen-attention surplus. If DOT repairs exceeded expectations where 311 reports didn't, the city did more work than citizens reported. The two model residuals are what the **reporting gap** actually measured. **Figure 4** shows the two sets of highly correlated residuals (*r* = 0.88). Citizens reports and city repairs deviated from expectations in the same direction, in nearly every district. Six districts sat visibly off the diagonal — Mott Haven and Jackson Heights showed the largest "citizens report more" pattern; Elmhurst-Corona and Williamsburg-Greenpoint showed the opposite — but after correcting for the 59 simultaneous comparisons, **not one district's gap was statistically different from zero.** Across two years of data and all five boroughs, citizen and city pothole attention moved together.

<img src='/assets/images/nyc-potholes-figs/fig4_residuals.svg'>

##### **Figure 4.** Pearson residuals from the two negative binomial models, one point per community district. Distance from the dashed diagonal indicates divergence of the two signals: points above the line are districts where DOT activity exceeded model expectations more than 311 reports did, and vice versa. Red highlights show districts farthest from the diagonal, but the residual correlation was high (r = 0.88) and none of the per-district gaps were statistically different from zero after correction for multiple comparisons.

## Good news for 311
The question I ended up answering wasn't quite the one I started with. *"Do 311 calls represent New Yorkers' problems?"* became *"Do 311 reports and DOT repairs diverge systematically across community districts?"* because data can only answer quantifiable questions. That answer turned out to be no. At the district level, citizen and city pothole attention were remarkably harmonious.

For a civic data team, this is good news. It means that 311 data is structurally aligned with the city's own operational priorities at the community-district level. An analyst at OTI or a planner at DOT using 311 to allocate resources is building on a foundation that is at least internally consistent with where the city is already working.

This is also good news for citizens. A reasonable suspicion would be that wealthier districts get disproportionate attention from city services. My finding refutes that concern. Wealthier districts do report more potholes, and they do receive more repairs, but the ratio of repairs to reports is the same as in lower-income districts. The city responds to the signal it receives, at a rate that doesn't vary by district income. (Whether the signal itself is equally representative across income — whether lower-income residents are calling 311 less than they "should" — is a separate question that this analysis can't fully answer.)

## But aren't 311 and DOT measuring the same thing?
When I described this finding to my mother, she asked: "Aren't the city's repairs based on the 311 calls themselves? Of course they move together." She isn't wrong. Roughly 60% of DOT pothole work orders in this window originated from citizen-sourced channels, meaning that the city was often responding to the very 311 calls I treated as one of the two signals. A skeptic could argue that my analysis amounts to "the city responds to what citizens report, and what citizens report is what citizens report!"

Two responses here: 1) Even when DOT's work originates from a citizen call, the decision to dispatch a crew, complete the repair, and close the work order is the city's. A 311 call that goes unaddressed produces no work order. Harmony between the two means citizens are calling about real problems and the city is closing the loop. 2) The 40% of DOT work orders that originated from non-citizen channels — yard inspections, borough offices, traffic communications — showed the same relationship to demographics as the citizen-initiated portion. If the analysis were purely tautological, we'd expect the demographic patterns to vanish when we restricted to DOT-internal sources.

What the analysis *cannot* tell us is whether both signals are biased in the same direction relative to *true* underlying need. Both 311 and DOT measure attention, not incidence. A complete analysis of "representativeness" would require an independent need proxy. NYC DOT's [Street Pavement Rating dataset](https://data.cityofnewyork.us/Transportation/Street-Pavement-Ratings/6yyb-pb25), which rates every street segment on a 1-10 scale through ongoing inspections, would be a good pick for follow-up work.

## What about the pothole on MY street?
A reader on a street with a still-unfilled pothole might also be skeptical. This analysis works at the community-district level, where each unit aggregates hundreds of thousands of residents and tens of thousands of road segments. Individual potholes vary widely in how quickly they're addressed.

The encouraging finding is that you wouldn't get systematically better service in a different district. There's no district in NYC where, holding demographics and road network constant, the city responds harder, better, faster, or stronger than elsewhere. The distinction is between asking "is the system biased?" (no) and "is the system fast?" (sometimes yes, sometimes no). This analysis answers the first question, not the second.

## Future directions
This methodology generalizes anywhere two reporting systems share a base domain: two parallel count models with shared exposure offsets, and a comparison of residuals. It isn't specific to potholes, or even to civic data.

Noise pollution is a natural next extension. [NYU's Sounds of New York City (SONYC)](https://wp.nyu.edu/sonyc/) project operates a [city-wide noise sensor network](https://arxiv.org/abs/1903.03195) in partnership with NYC DEP, and DOHMH research has separately documented that 311 noise complaints [over-represent affluent Manhattan neighborhoods](https://www.nyc.gov/assets/doh/downloads/pdf/epi/databrief45.pdf) relative to where residents actually report noise disruption (via surveys) — the exact type of **gap** this analysis did not find. Other areas with independent comparison data, like tree complaints against [Parks Department forestry work orders](https://data.cityofnewyork.us/Environment/Forestry-Work-Orders/bdjm-n7q4), could reveal where 311 *is* representative and where it *isn't*. The NYC City Council Data Team has separately [studied response-time variation](https://council.nyc.gov/data/311-agency/) across agencies, finding differences in how quickly different parts of the city government close 311 service requests.

---
**Thank you:** to the [NYC OpenData team](https://opendata.cityofnewyork.us/) and members of the [Office of Technology and Information](https://www.nyc.gov/content/oti/pages/) for providing the data platform to make projects like this possible, and for an engaging interview conversation that inspired this project.

**GitHub:** [amnion/nyc-potholes](https://github.com/amnion/nyc-potholes)

**Data sources:**
* [311 Service Requests](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2020-to-Present/erm2-nwe9) (NYC OpenData)
* [Street Pothole Work Orders - Closed](https://data.cityofnewyork.us/Transportation/Street-Pothole-Work-Orders-Closed-Dataset-/x9wy-ing4) (NYC OpenData)
* [Community Districts](https://data.cityofnewyork.us/City-Government/Community-Districts/5crt-au7u) (NYC OpenData)
* [Street Centerlines](https://data.cityofnewyork.us/City-Government/Centerline/inkn-q76z) (NYC OpenData)
* [ACS 2019-2023 5-year estimates](https://www.nyc.gov/content/planning/pages/resources/datasets/american-community-survey) (NYC Dept. of City Planning)


**AI statement:** I used Claude (Opus 4.7; Anthropic) on this project. LLM usage was careful, intentional, and collaborative. Text and code were drafted first by me and revised with input from Claude. The project took ~60 hours of effort from start to finish. This was not a weekend vibe code. I used the time deliberately to work through the data, write code myself (especially for SQL practice), and nitpick every strategy, execution, and design choice. The slower pace paid off. I learned a ton, and Claude pointed me toward directions I wouldn't have known existed, which improved the project's scope.

---

*I'm always open to connecting. [Get in touch](mailto:jacobedwards.jae@gmail.com) or [see the rest of my work](/).*