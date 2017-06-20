
---
title: "Maps"
output: 
  html_document:
    self_contained: no
---

```{r echo=FALSE, message=FALSE, warning=FALSE}
library(leaflet)

df <- data.frame(lat=runif(20, min=33.8, max=33.9),
                 lng=runif(20, min=-84.1, max=-84.0))
                 
                 
my_map <- df %>%
    leaflet() %>%
    addMarkers() %>%
    addTiles()
 
my_map

```


               
```{r, echo=FALSE, warning=FALSE}

library(devtools)
library(rMaps)
library(htmlwidgets)
library(knitr)


## Welcome to GitHub Pages

---
title: ""
output: html_document
---

##Detecting local Zika virus transmission in the continental United States: a comparison of surveillance strategies

**Authors**

Steven Russell, Kyle Ryff, Carolyn Gould, Stacey Martin, Michael Johansson 

**Table of Contents**  

[Abstract](#abstract)  
[Intro](#intro)  
[Methods](#methods)  
[Results](#results)  
[Discussion](#discussion)  
[References](#references)

<a name="abstract">  </a>
**Abstract**

*Introduction*

The 2015-2017 Zika virus (ZIKV) epidemic in the Americas has driven efforts to strengthen surveillance systems and to develop interventions, testing, and travel recommendations. In the continental U.S. and Hawaii, where limited transmission has been observed, detecting local transmission is a key public health objective. We assessed the effectiveness of three general surveillance strategies for this situation: testing all pregnant women twice during pregnancy, testing blood donations, and testing symptomatic people who seek medical care in an emergency department (ED).

*Methods*

We developed a simulation model for each surveillance strategy and simulated different transmission scenarios with varying population sizes and infection rates. We then calculated the probability of detecting transmission, the number of tests needed, and the number of false positive test results. 

*Results*

The probability of detecting ZIKV transmission was highest for testing ED patients with Zika symptoms, followed by pregnant women and blood donors, in that order. The magnitude of the difference in probability of detection between strategies depended on the incidence of infection. Testing ED patients required fewer tests and resulted in fewer false positives than surveillance among pregnant women. The optimal strategy identified was to test ED patients with at least two Zika virus disease symptoms. This case definition resulted in a high probability of detection with relatively few tests and false positives. 

*Discussion*

In the continental U.S. and Hawaii, where local ZIKV transmission is rare, optimizing the probability of detecting infections while minimizing resource usage is particularly important. Local surveillance strategies will be influenced by existing public health system infrastructure, but should also consider the effectiveness of different approaches. This analysis demonstrated differences across strategies and indicated that testing symptomatic ED patients is generally a more efficient strategy for detecting transmission than routine testing of pregnant women or blood donors. 

<a name="intro">  </a>
**Introduction**

In 2015 and 2016, Zika virus (ZIKV) spread through the Americas, with the first cases confirmed in early 2015 in Brazil [1] and 48 countries and territories reporting confirmed locally acquired infections by the end of 2016 [2]. Prior to its emergence in the Americas, ZIKV was a relatively obscure arboviral disease, with the first documented outbreak occurring on the island of Yap in 2007 [3]. While ZIKV infection appeared to be relatively benign in the Yap outbreak, the study of subsequent outbreaks in French Polynesia and the Americas provided evidence that ZIKV infection was associated with adverse outcomes, including Guillain-Barré syndrome [4-6] and congenital birth defects [7]. These severe manifestations have driven efforts to identify areas where transmission is ongoing to target interventions, testing, and travel recommendations.

Many areas of the Americas were also impacted by the emergence of chikungunya virus in 2013-2014 and have endemic dengue virus transmission [8], two arboviruses transmitted by the same Aedes mosquito vectors. These areas were at risk of ZIKV transmission and most experienced large Zika outbreaks. In the continental United States, however, Zika, chikungunya, and dengue viruses have each been repeatedly introduced into areas inhabited by Ae. aegypti and Ae. albopictus, yet transmission has only been sporadically identified [9-13]. The climate of the southern U.S. is suitable for Zika virus transmission but living conditions (e.g., air conditioning) restrict human-mosquito interaction, likely limiting transmission [14].

Although the risk of widespread mosquito-borne transmission in the continental U.S. and Hawaii is low, locally acquired cases have been reported in Florida and Texas [12, 13]. In August 2016, the Food and Drug Administration (FDA) issued revised recommendations for testing all donated blood products in the United States [15]. These recommendations were implemented to protect the blood supply but could also serve as a surveillance strategy to detect asymptomatic or pre-symptomatic Zika virus infections and monitor transmission as has been done in Puerto Rico [16]. However, this is not the only possible strategy for detecting local ZIKV infections in areas at risk for mosquito-borne transmission [17]. Locally implemented surveillance systems should consider several factors: the sensitivity (probability of detecting transmission should it occur), the specificity (avoidance of false-positive test results requiring follow-up), and the resources needed for conducting surveillance (e.g. laboratory testing capacity).

We assessed the likely effectiveness of three general surveillance strategies that could be used to detect ZIKV transmission in areas of the continental U.S. and Hawaii at risk of local mosquito-borne transmission. The first strategy is to test all pregnant women twice during pregnancy (1st and 2nd trimester), as was previously recommended in areas with known ongoing risk [18]. This would align surveillance with the population of greatest concern, but it limits testing to that group and it is possible that transmission could be detected earlier in other populations. The second strategy is to use the results of blood donation screening, which is already being conducted as recommended by the FDA. Blood donation is only permitted for healthy individuals, so this strategy would only detect asymptomatic or pre-symptomatic infections. The population tested is also limited to the population seeking to donate; the U.S. averages about 4.3-4.7 blood donations per 100 people per year [19, 20]. The third strategy is to test symptomatic people who seek medical care. In Yap and French Polynesia, serosurvey results suggest that only a small proportion of infected individuals were symptomatic and sought care [3, 21, 22] and symptoms were possibly non-specific. Nonetheless, there may be a higher probability of detecting infections among people seeking care, which we limit to emergency department (ED) visits for the purposes of the current study.

<a name="methods">  </a>
**Methods**

We first identified available data for critical components of each of the three surveillance strategies, which are described below and summarized in Table 1. For the purposes of this assessment, pregnant women were assumed to be tested solely with a serological assay to detect anti-ZIKV IgM, which is currently included in the algorithm for asymptomatic pregnant women with ongoing risk for exposure to Zika virus as part of routine obstetric care [18]. Data on Zika IgM ELISA test sensitivity and specificity are limited, but based on studies assessing IgM ELISA test performance for dengue viruses [23-26], we assumed the test would have a sensitivity of 80-99%. In the context of the continental U.S., where dengue is not endemic and the potential cross-reactivity of related flaviviruses is of limited concern, we assumed a specificity of 80-95%. We estimated that IgM antibodies would be detectable in an infected person for a period of 2-4 months [27-29]. Live birth rates across U.S. states vary from 9 to 17 per 1,000 persons per year [30]. We assumed that testing would occur only in pregnant women (excluding pregnancies that do not reach full term) and that women would be tested twice during pregnancy, in the first and second trimesters.

In the context of surveillance, we assumed that blood donations would be tested with highly specific blood donor screening nucleic acid tests (BDS-NAT) such as the cobas [31] and Procleix [32] assays. We assumed that these assays could detect ZIKV RNA for 11-17 days, the median time to ZIKV RNA clearance [28], and would have a specificity of greater than 99.99, using a range of 99.99-100% [31, 32]. Clinical sensitivity of the these assays has not been characterized, but analytical sensitivity is higher than typical RT-PCR tests [33] and we assumed it would be in the range of 98-100% based on clinical sensitivity estimates for the West Nile virus individual NAT assay [34]. A recent study estimated that approximately 13,639,000-14,835,000 whole blood and apheresis red blood cell units were collected in the U.S. in 2013 [19]. With a population of 316,128,839 U.S. residents [20], the estimated rate of donation was 43-47 donations per 1,000 persons per year. We assumed that 60-80% of individuals infected with ZIKV would be asymptomatic and therefore eligible for blood donation [3, 21, 22].

For the purposes of this study, we assumed that symptomatic ED patients would be tested exclusively by serum RT-PCR, with no IgM testing. Since ED patients typically present while symptomatic and viral RNA is estimated to be detectable for a median of 11-17 days [28], we assumed that all ZIKV infected ED patients would have detectable RNA. We assumed that the RT-PCR test has a sensitivity of 80-95%, based on the confidence interval for 118 out of 134 patients who tested positive by RT-PCR within 7 days of symptom onset in a recent study [28]. We assumed that the specificity of the RT-PCR test would be greater than 99% and used a range of 99-100% [35]. We focused on patients with five symptoms associated with ZIKV infection: fever, headache, rash, arthralgia and conjunctivitis [36]. First, we estimated that 0.7%-1% of the population visits an ED in a given week [37]. Then, we used data extracted from the National Syndromic Surveillance Program’s BioSense Platform [38] on aggregated chief complaints for 1-2 million ED visits on a weekly basis over the period from the week starting May 29, 2015 to the week starting May 28, 2016. Only national-level aggregate data from U.S. states were used. For each symptom and combination of symptoms, we found the range of weekly frequencies at which that symptom or combination was reported. For example, across all the weeks, a minimum of 3.6% and a maximum of 6.7% of ED patient records included fever in the chief complaint description. Ranges for each symptom and combination of symptoms are provided in Supplemental Table 1. We then estimated the probability of ZIKV-infected individuals seeking care in the EDs. We assumed that 20-40% of ZIKV infections will exhibit symptoms [3, 21, 22], 10-50% of people with symptomatic infections will seek care [3, 21, 22], and 5-50% of care-seeking individuals will visit an ED [39]. Among those patients, we assumed that symptoms would be distributed with the same proportions found among symptomatic ZIKV-infected people seeking care in Puerto Rico [36] (Supplemental Table 1). 

To account for uncertainty and variability in each parameter, we used the range of likely values to create uniform sampling distributions and drew 10,000 samples of each parameter from its respective distribution under transmission scenarios and population sizes using the following formula to calculate $p_{detect}$, the weekly probability of detecting at least one ZIKV infection:

$p_{detect} = 1-(1-p_{ZIKV}p_{test}ds)^N$,

Where $p_{ZIKV}$ is the weekly probability of being infected with ZIKV, $p_{test}$ is the weekly probability of being tested, d is the duration (in weeks) of detectible RNA or antibodies, s is the sensitivity of the assay, and N is the population size. $p_{ZIKV}$ and $N$ were fixed for individual simulations, with $p_{ZIKV}$ ranging from 1 infection per 100,000 per week to 1 infection per 1,000 per week and N fixed at 10,000, 100,000, or 1,000,000. The assay specific variables, d and s, were simulated from uniform distributions over the range specified in Table 1 with the exception that d was assumed to be 1 for ED patients, as they would only be tested when presenting with symptoms. For pregnant women, $p_{test}$ is twice the number of new pregnancies per week (to account for two tests per pregnancy) divided by the total population size. For blood bank donors, $p_{test}$ is the product of the weekly probability of blood donation per person and the probability of infection being asymptomatic. For ED patients, $p_{test}$ is the product of the proportion of ZIKV infected people who have any symptoms, the proportion of those who seek care at an ED, and the proportion of those who have each specific symptom or set of symptoms. 

For each strategy, the expected number of tests required, T, is a binomial sample from the population, N, with probability, $p_{test}$. The expected number of false positive tests is a binomial sample with probability 1-specificity from the total number of tests, T. The proportion of total infections detected is $p_{test}ds$. We summarized the results using the 25th and 75th percentiles to identify 50% uncertainty intervals, and the 2.5th and 97.5th percentiles to identify 95% uncertainty intervals. The code used to generate the estimates is provided in the Supplemental Materials. 


```{r, echo=FALSE, message=FALSE, warning=FALSE, results="hide"}

library(dplyr)
library(repmis)

# Loading data from 'Zika Simulation Code.R'

source_data("https://github.com/StevenRussell/Zika/blob/master/R%20data%20files/full_estimates.Rdata?raw=True")
source_data("https://github.com/StevenRussell/Zika/blob/master/R%20data%20files/full_estimates_syndrome.Rdata?raw=True")

p <- summary.stats[summary.stats$incidence == .001 & summary.stats$population == 100000 & summary.stats$type == "pregnant",]
b <- summary.stats[summary.stats$incidence == .001 & summary.stats$population == 100000 & summary.stats$type == "blood",]
sr <- summary.stats[summary.stats$incidence == .001 & summary.stats$population == 100000 & summary.stats$type == "rash",]
shr <- summary.stats[summary.stats$incidence == .001 & summary.stats$population == 100000 & summary.stats$type == "head+rash",]
s2 <- summary.stats[summary.stats$incidence == .001 & summary.stats$population == 100000 & summary.stats$type == "2 or more",]
s3 <- summary.stats[summary.stats$incidence == .001 & summary.stats$population == 100000 & summary.stats$type == "3 or more",]
sr1 <- summary.stats[summary.stats$incidence == .001 & summary.stats$population == 100000 & summary.stats$type == "rash + 1",]

#------------------------------------------------------------------------------------------------------------------------------#
#                                                 Calculating values                                                           #
#------------------------------------------------------------------------------------------------------------------------------#

# Expected probability of detection (50% UI)

v1 <- paste0(signif(sr$p.detect.m, 2)*100, "% (50% UI: ", signif(sr$p.detect.l50, 2)*100, "%, ", signif(sr$p.detect.u50, 2)*100, "%)")
v2 <- paste0(signif(shr$p.detect.m, 2)*100, "% (50% UI: ", signif(shr$p.detect.l50, 2)*100, "%, ", signif(shr$p.detect.u50, 2)*100, "%)")
v3 <- paste0(signif(p$p.detect.m, 2)*100, "% (50% UI: ", signif(p$p.detect.l50, 2)*100, "%, ", signif(p$p.detect.u50, 2)*100, "%)")
v4 <- paste0(signif(b$p.detect.m, 2)*100, "% (50% UI: ", signif(b$p.detect.l50, 2)*100, "%, ", signif(b$p.detect.u50, 2)*100, "%)")

# For a population of 1 million (50% UI)

b.1mil <- summary.stats[summary.stats$incidence == .001 & summary.stats$population == 1000000 & summary.stats$type == "blood",]

v5 <- paste0(signif(b.1mil$p.detect.m, 2)*100, "% (50% UI: ", signif(b.1mil$p.detect.l50, 2)*100, "%, ", signif(b.1mil$p.detect.u50, 2)*100, "%)")

# Expected tests

v6 <- paste0(signif(b$tests.m, 2), " (95% UI: ", signif(b$tests.l95, 2), ", ", signif(b$tests.u95, 2), ")")
v7 <- paste0(signif(p$tests.m, 2), " (95% UI: ", signif(p$tests.l95, 2), ", ", signif(p$tests.u95, 2), ")")
v8 <- paste0(signif(sr$tests.m, 2), " (95% UI: ", signif(sr$tests.l95, 2), ", ", signif(sr$tests.u95, 2), ")")
v9 <- paste0(signif(shr$tests.m, 2), " (95% UI: ", signif(shr$tests.l95, 2), ", ", signif(shr$tests.u95, 2), ")")

v10 <- paste0(signif(b.1mil$tests.m, 2), " (95% UI: ", signif(b.1mil$tests.l95, 2), ", ", signif(b.1mil$tests.u95, 2), ")")

# Expected false positives

v11 <- paste0(signif(p$fp.m, 2), " (95% UI: ", signif(p$fp.l95, 2), ", ", signif(p$fp.u95, 2), ")")
v12 <-paste0(signif(b$fp.m, 2), " (95% UI: ", signif(b$fp.l95, 2), ", ", signif(b$fp.u95, 2), ")")
v13 <-paste0(signif(sr$fp.m, 2), " (95% UI: ", signif(sr$fp.l95, 2), ", ", signif(sr$fp.u95, 2), ")")
v14 <-paste0(signif(shr$fp.m, 2), " (95% UI: ", signif(shr$fp.l95, 2), ", ", signif(shr$fp.u95, 2), ")")

# Expected proportion detected

v15 <- paste0(signif(sr$num.zikv.ppl.detected.m , 2), " (95% UI: ", signif(sr$num.zikv.ppl.detected.l95 , 2),
       ", ", signif(sr$num.zikv.ppl.detected.u95 , 2), ")")
v16 <- paste0(signif(shr$num.zikv.ppl.detected.m , 2), " (95% UI: ", signif(shr$num.zikv.ppl.detected.l95 , 2),
       ", ", signif(shr$num.zikv.ppl.detected.u95 , 2), ")")
v17 <- paste0(signif(p$num.zikv.ppl.detected.m , 2), " (95% UI: ", signif(p$num.zikv.ppl.detected.l95 , 2),
       ", ", signif(p$num.zikv.ppl.detected.u95 , 2), ")")
v18 <- paste0(signif(b$num.zikv.ppl.detected.m , 2), " (95% UI: ", signif(b$num.zikv.ppl.detected.l95 , 2),
       ", ", signif(b$num.zikv.ppl.detected.u95 , 2), ")")

```

<a name="results">  </a>
**Results**

We first analyzed four general surveillance strategies: testing pregnant women, testing blood donors, testing ED patients with rash (the most common Zika symptom), and testing ED patients with rash and headache (the most common combination of Zika symptoms). Regardless of population size and infection rate, the probability of detection was highest for testing ED patients with rash, followed by ED patients with both rash and headache, pregnant women, and blood donors, in order (Figure 1). In a population of 10,000 people with infection rates up to 1 ZIKV infection per 1,000 people, the weekly probability of detection never reached 25% for any system. In larger populations, the weekly probability of detection increased as the total number of infections increased. In a population of 100,000 people with an incidence rate of 1 ZIKV infection per 1,000 people (or equivalently, in a population of 1 million people with an incidence rate of 1 ZIKV infection per 10,000 people), the highest probability of detecting transmission occurred when testing symptomatic ED patients. Testing ED patients with rash resulted in a weekly probability of detection of `r v1`, compared to a probability of detection of `r v2` when testing ED patients with both rash and headache, `r v3` when testing pregnant women, and `r v4` when testing blood donors. In a population of 1 million with an incidence of 1 ZIKV infection per 1,000 people, testing pregnant women or ED patients in either group resulted in probabilities of detection higher than 99%, while testing blood donors resulted in a probability of detection of `r v5`. 

<img src="https://github.com/StevenRussell/Zika/blob/master/Figures/Figure%201.png?raw=true" alt="Drawing" style="width: 672px;"/>

The expected number of tests also varied between systems (Figure 2A). In a population of 100,000, surveillance among blood donors would require the highest number of tests, an estimated `r v6` NAT tests per week. Testing pregnant women would require `r v7` IgM ELISA tests per week, testing ED patients with rash would require `r v8` RT-PCR tests per week, and testing ED patients with rash and headache would require only `r v9` RT-PCR tests per week. For smaller and larger populations, the number of tests scaled directly with population sizes. For example, in a population of 1 million people, `r v10` NAT tests would be expected for blood donor surveillance (not shown). The number of tests performed does not correlate exactly with the probability of detection. For example, while fewer tests are required for surveillance among pregnant women compared to blood donors, the longer detection window leads to a higher probability of detection. 

<img src="https://github.com/StevenRussell/Zika/blob/master/Figures/Figure%202.png?raw=true" alt="Drawing" style="width: 672px;"/>

With little or no local transmission, tests are performed mostly on people who are not infected and some of those tests result in false positives, with the number of false positives being dependent on the specificity of the assay. The assay with the lowest specificity was the IgM ELISA, which was considered for surveillance among pregnant women. This resulted in the high median number of false positive test results — 6.0 (95% UI: 2.4, 11.0) per week in a population of 100,000 (Figure 2B). In contrast, both the BDS-NAT and RT-PCR assays are highly specific and have reduced rates of false positives compared to the IgM ELISA assay. Testing ED patients with rash would result in an estimated 0.22 (95% UI: 0.01, 0.47) false positive tests per week, while testing ED patients with both rash and headache would result in an estimated 0.006 (95% UI: 0.0003, 0.01) false positives per week, and testing blood donors with the BDS-NAT assay would result in an expected 0.004 (95% UI: 0.0002, 0.008) false positive tests per week. In strategies that use a limited number of highly specific tests, a positive result can accurately predict a true infection. Even at low infection rates, a single test administered on an ED patient with rash and headache had a high positive predictive value (Figure 3, Supplemental Figure 2).

<img src="https://github.com/StevenRussell/Zika/blob/master/Figures/Figure%203.png?raw=true" alt="Drawing" style="width: 672px;"/>

The expected proportion of infections detected in any strategy was low. The highest proportion of detection occurred when testing all ED patients with rash, in which 1.6% of all ZIKV infections (95% UI: 0.29, 5.0) would be detected (Figure 2C). Testing ED patients with rash and headache was second highest, with 1.1% of infections detected (95% UI: 0.2, 3.4), followed by pregnant women, 0.5% of infections (95% UI: 0.3%, 0.9%), and blood donors, 0.1% of infections (95% UI: 0.1%, 0.2%). ED patient testing resulted in a higher probability of detection, fewer tests, and fewer false positives, so we investigated alternative case definitions for surveillance. The number of RT-PCR tests required (Figure 4A) depends on the number of ED patients who meet each case definition. Among Zika-like symptoms in ED patients that we analyzed, fever, rash, and headache were most commonly reported; 3.7-6.7% reported fever, 4.3-6.1% reported rash, and 2.7-3.6% reported headache (Supplemental Table 1). Combinations of these symptoms were rare, 0.9-1.6% had two or more of these five symptoms and 0.3-0.7% had three or more of these five symptoms. Additionally, 0.6-0.9% has rash plus at least one of the other four symptoms.

<img src="https://github.com/StevenRussell/Zika/blob/master/Figures/Figure%204.png?raw=true" alt="Drawing" style="width: 672px;"/>

The surveillance case definition also determines the likelihood of testing and therefore the probability of detection (Figure 4B). Among ZIKV infected individuals, rash was the most common symptom (86-87%), followed by headache (65-67%), arthralgia (60-61%), fever (51-53%), and conjunctivitis (16-17%) (Supplemental Table 1). Multi-symptom combinations were also common; 82-83% of infected individuals had two or more of these five symptoms and 61-62% had three or more of these five symptoms. Additionally, 75-76% had rash plus at least one of the other four symptoms. Accordingly, the probability of detection was highest when testing for ED patients with rash, followed by testing patients with two or more symptoms, rash and one other symptom, and so on.

As shown in Figures 1 and 2, testing of symptomatic ED patients with rash outperformed testing of pregnant women with a higher probability of detection and fewer false positive test results. The alternative cases definitions of (a) at least two symptoms, (b) at least three symptoms, and (c) rash plus at least one additional symptom, were almost as effective at detecting transmission as testing anyone with rash (Figure 5A, Table 2). In a population of 100,000 people with a weekly incidence rate of 1 ZIKV infection per 10,000 people, the median estimated probability of detection for the multi-symptom case definitions was 11-14% compared to 15% for all patients with rash. Meanwhile, the multi-symptom case definitions required far fewer tests; an average of 0.3-0.9 (95% UI) tests per week for patients with three or more symptoms, 4.5-8.2 (95% UI) tests per week for patients with rash plus another symptom, and 7-15 (95% UI) tests per week for patients with two or more symptoms (Figure 5B).

<img src="https://github.com/StevenRussell/Zika/blob/master/Figures/Figure%205.png?raw=true" alt="Drawing" style="width: 672px;"/>

<a name="discussion">  </a>
**Discussion**

In areas of the US and Hawaii where there is potential risk of ZIKV transmission, detecting transmission should it occur is a key public health objective [17]. This poses a challenge for surveillance systems: to balance the probability of detecting ZIKV transmission with the resources needed to carry out surveillance when infections may be rare. An efficient surveillance system should have high sensitivity (a relatively high probability of detecting infections) and high specificity (a low probability of a positive test result in an individual without infection).

Comparing three general surveillance systems, we found that none of them was likely to detect even 5% of all infections that occur, reflecting the difficulty in detecting ZIKV transmission because a high proportion of infections are mild or asymptomatic. However, the most important feature of any surveillance system is not the ability to detect all cases, but the ability to detect at least one locally transmitted case and thus prompt public health authorities to conduct enhanced surveillance and recommend appropriate prevention measures in that location. Among these strategies, the system for testing individuals presenting in EDs had a higher probability of detecting at least one ZIKV infection than systems designed to detect infection in pregnant women or blood donors. 

The numbers of tests required and false positive results were also lowest for ED patients with testing limited to RT-PCR. The number of tests was highest for blood donors, though this does not represent an added testing burden as blood donation screening is already implemented to protect the blood supply [15]. The number of false positive tests was highest among pregnant women because of the relatively low specificity of the IgM ELISA. In any system, the number of tests and false positive results will depend on the diagnostic testing algorithm that is used. For example, both IgM ELISA and RT-PCR testing could be implemented to increase sensitivity. For ED patients, the addition of IgM ELISA testing would increase the number of tests and false positives. The testing algorithm for pregnant women considered here also only represents one possible algorithm. Challenges with cross-reactivity and low specificity have prompted CDC to recommend a combination of diagnostic tests for pregnant women with exposure risk [40]. Complications of third trimester ZIKV infection have prompted recommendations for third trimester testing for those women [41]. If these changes were implemented in a surveillance system to detect transmission, the probability of detection, the number of tests, and the number of false positives would increase.

We found that the most common Zika symptom, rash, was also common among ED patients, being reported in 4-6% of ED visit chief complaints. However, far fewer ED patients met narrower case definitions of (i) two or more Zika symptoms (rash, headache, arthralgia, fever, or conjunctivitis), (ii) three or more Zika symptoms, or (iii) rash plus at least one other symptom. With these multiple symptom case definitions, we found that the probability of detection was almost equivalent to using rash alone, but the number of tests required and false positives were reduced substantially. This strategy thus represents a good combination of high probability of detection and low resource use. 

This analysis only considered three general options for surveillance. It was intended not as an exhaustive review of all possibilities, but as a comparison of broadly applicable strategies with data that were available. The optimal strategy identified was to detect symptomatic infections with at least two Zika symptoms among patients presenting to the ED. However, this exact strategy may not be feasible nor optimal for any given location. For example, if RT-PCR testing is unavailable it would not be viable. If people do not tend to seek care in EDs, there may be alternative ways to try to capture cases. A jurisdiction may also choose to combine multiple approaches as part of a surveillance strategy. The analysis also did not consider the costs of assays or other resources (e.g. personnel, transportation, or laboratory supplies) needed to perform surveillance; costs could vary between systems and jurisdictions and therefore would be important to consider as part of any implementation plan. Furthermore, in areas where transmission has been detected and for travelers to areas of risk these strategies do not replace existing guidance for testing symptomatic persons or asymptomatic pregnant women [18].

The results presented here are general, but highlight key factors to consider and demonstrate how different approaches can be compared. Specifically, a surveillance system for local transmission of Zika virus in the continental U.S. and Hawaii is targeting a pathogen that is likely rare, such that extensive testing may be needed to detect transmission should it occur. In this situation, optimizing the probability of detecting infections while minimizing resource usage is particularly important. Directly comparing approaches through simulation, as done here, can highlight important tradeoffs and can inform a thorough analysis of potential surveillance strategies.



<a name="references">  </a>
**References**

1.	Campos GS, Bandeira AC, Sardi SI. Zika virus outbreak, Bahia, Brazil. Emerging Infectious Diseases. 2015;21(10):1885-6.
2.	Pan American Health Organization / World Health Organization. Zika Epidemiological Update, 29 December 2016 Washington, D.C. Available from: http://www2.paho.org/hq/index.php?option=com_docman&task=doc_view&Itemid=270&gid=37579&lang=en.
3.	Duffy MR, Chen T-H, Hancock WT, Powers AM, Kool JL, Lanciotti RS, et al. Zika virus outbreak on Yap Island, federated states of Micronesia. New England Journal of Medicine. 2009;360(24):2536-43.
4.	Cao-Lormeau V-M, Blake A, Mons S, Lastère S, Roche C, Vanhomwegen J, et al. Guillain-Barré Syndrome outbreak associated with Zika virus infection in French Polynesia: a case-control study. The Lancet. 2016;387(10027):1531-9.
5.	Dos Santos T, Rodriguez A, Almiron M, Sanhueza A, Ramon P, de Oliveira WK, et al. Zika virus and the Guillain–Barré syndrome—case series from seven countries. New England Journal of Medicine. 2016;375(16):1598-601.
6.	Krauer F, Riesen M, Reveiz L, Oladapo OT, Martínez-Vega R, Porgo TV, et al. Zika virus infection as a cause of congenital brain abnormalities and Guillain-Barré syndrome: systematic review: DATASET. 2016.
7.	Rasmussen SA, Jamieson DJ, Honein MA, Petersen LR. Zika virus and birth defects—reviewing the evidence for causality. New England Journal of Medicine. 2016;374(20):1981-7.
8.	Musso D, Gubler DJ. Zika virus: following the path of dengue and chikungunya? The Lancet. 2015;386(9990):243-4.
9.	Adalja AA, Sell TK, Bouri N, Franco C. Lessons learned during dengue outbreaks in the United States, 2001–2011. Emerging Infectious Diseases. 2012;18(4):608-14.
10.	Centers for Disease Control and Prevention. Locally acquired Dengue--Key West, Florida, 2009-2010. MMWR Morbidity and mortality weekly report. 2010;59(19):577.
11.	Kendrick K, Stanek D, Blackmore C. Notes from the field: transmission of chikungunya virus in the continental United States—Florida, 2014. MMWR Morbidity and Mortality Weekly Report. 2014;63(48):1137.
12.	Likos A, Griffin I, Bingham A, et al. Local Mosquito-Borne Transmission of Zika Virus — Miami-Dade and Broward Counties, Florida, June–August 2016. MMWR Morbidity and Mortality Weekly Report. 2016;65(38); 1032-1038.
13.	Texas Department of State Health Services. Texas Announces Local Zika Virus Case in Rio Grande Valley 2016 [updated November 28, 2016]. Available from: http://www.dshs.texas.gov/news/releases/2016/20161128.aspx.
14.	Reiter P, Lathrop S, Bunning M, Biggerstaff B, Singer D, Tiwari T, et al. Texas lifestyle limits transmission of dengue virus. Emerging Infectious Diseases. 2003;9(1):86-9.
15.	Food and Drug Administration. FDA News Release: FDA advises testing for Zika virus in all donated blood and blood components in the US 2016. Available from: http://www.fda.gov/NewsEvents/Newsroom/PressAnnouncements/ucm518218.htm.
16.	Kuehnert MJ. Screening of blood donations for Zika virus infection—Puerto Rico, April 3–June 11, 2016. MMWR Morbidity and Mortality Weekly Report. 2016;65.
17.	Centers for Disease Control and Prevention. Zika CDC Interim Response Plan: May 2017. Available from: https://www.cdc.gov/zika/pdfs/zika-draft-interim-conus-plan.pdf.
18.	Oduyebo T. Update: interim guidelines for health care providers caring for pregnant women and women of reproductive age with possible Zika virus exposure—United States, 2016. MMWR Morbidity and Mortality Weekly Report. 2016;65.
19.	Chung KW, Basavaraju SV, Mu Y, van Santen KL, Haass KA, Henry R, et al. Declining blood collection and utilization in the United States. Transfusion. 2016.
20.	United States Census Bureau. Annual Estimates of Resident Population for Selected Age Groups by Sex for the United States, States, Counties, and Puerto Rico Commonwealth and Municipios: April 1, 2010 to July 1, 2013. Available from: https://factfinder.census.gov/faces/tableservices/jsf/pages/productview.xhtml?src=bkmk.
21.	Aubry M, Teissier A, Huart M, Merceron S, Vanhomwegen J, Roche C, et al. Zika Virus Seroprevalence, French Polynesia, 2014–2015. Emerging Infectious Diseases. 2017;23:669-72.
22.	Gallian P, Cabié A, Richard P, Paturel L, Charrel RN, Pastorino B, et al. Zika virus in asymptomatic blood donors in Martinique. Blood. 2017;129(2):263-6.
23.	Hunsperger EA, Yoksan S, Buchy P, Nguyen VC, Sekaran SD, Enria DA, et al. Evaluation of commercially available anti-dengue virus immunoglobulin M tests. Emerging Infectious Diseases. 2009;15(3):436-40.
24.	Groen J, Koraka P, Velzing J, Copra C, Osterhaus AD. Evaluation of six immunoassays for detection of dengue virus-specific immunoglobulin M and G antibodies. Clinical and diagnostic laboratory immunology. 2000;7(6):867-71.
25.	Guzman MG, Jaenisch T, Gaczkowski R, Hang VTT, Sekaran SD, Kroeger A, et al. Multi-country evaluation of the sensitivity and specificity of two commercially-available NS1 ELISA assays for dengue diagnosis. PLOS Neglected Tropical Diseases. 2010;4(8):e811.
26.	Centers for Disease Control and Prevention. Zika MAC-ELISA: Instructions for Use 2016. Available from: https://www.fda.gov/downloads/MedicalDevices/Safety/EmergencySituations/UCM488044.pdf.
27.	Centers for Disease Control and Prevention. Fact Sheet for Health Care Providers: Interpreting Zika MAC-ELISA Results 2016. Available from: https://www.cdc.gov/zika/pdfs/zika-mac-elisa-fact-sheet-for-hcp.pdf.
28.	Paz-Bailey G, Rosenberg ES, Doyle K, Munoz-Jordan J, Santiago GA, Klein L, et al. Persistence of Zika Virus in Body Fluids—Preliminary Report. New England Journal of Medicine. 2017.
29.	Rabe IB. Interim guidance for interpretation of Zika virus antibody test results. MMWR Morbidity and Mortality Weekly Report. 2016;65.
30.	Hamilton B, Martin J, Osterman M, Curtin S, Matthews TJ. Births: Final Data for 2014. National Vital Statistics Reports: 2015.
31.	Galel SA, Williamson PC, Busch MP, Stanek D, Bakkour S, Stone M, et al. First Zika‐positive donations in the continental United States. Transfusion. 2017.
32.	Williamson PC, Linnen JM, Kessler DA, Shaz BH, Kamel H, Vassallo RR, et al. First cases of Zika virus–infected US blood donors outside states with areas of active transmission. Transfusion. 2017.
33.	Stone M, Lanteri MC, Bakkour S, Deng X, Galel SA, Linnen JM, et al. Relative analytical sensitivity of donor nucleic acid amplification technology screening and diagnostic real‐time polymerase chain reaction assays for detection of Zika virus RNA. Transfusion. 2017.
34.	Pai A, Kleinman S, Malhotra K, Lee‐Haynes L, Pietrelli L, Saldanha J. Performance characteristics of the Food and Drug Administration–licensed Roche Cobas TaqScreen West Nile virus assay. Transfusion. 2008;48(10):2184-9.
35.	Centers for Disease Control and Prevention. Trioplex Real-time RT-PCR Assay 2017 [updated March 1, 2017]. Available from: https://www.cdc.gov/zika/pdfs/trioplex-real-time-rt-pcr-assay-instructions-for-use.pdf.
36.	Dirlikov E. Update: Ongoing Zika Virus Transmission—Puerto Rico, November 1, 2015–April 14, 2016. MMWR Morbidity and Mortality Weekly Report. 2016;65.
37.	National Center for Health Statistics. National Hospital Ambulatory Medical Care Survey: 2011 Emergency Department Summary Tables 2011. Available from: https://www.cdc.gov/nchs/data/ahcd/nhamcs_emergency/2011_ed_web_tables.pdf.
38.	National Syndromic Surveillance Program (NSSP). BioSense Platform 2016. Available from: https://www.cdc.gov/nssp/biosense/.
39.	Centers for Disease Control and Prevention. Combined NAMCS and NHAMCS: Annual number and percent distribution of ambulatory care visits by setting type according to diagnosis group: United States, 2009-2010. Available from: https://www.cdc.gov/nchs/data/ahcd/namcs_summary/2010_namcs_web_tables.pdf.
40.	Centers for Disease Control and Prevention. Guidance for U.S. Laboratories Testing for Zika Virus Infection 2016. Available from: https://www.cdc.gov/zika/pdfs/laboratory-guidance-zika.pdf.
41.	Centers for Disease Control and Prevention. Prolonged IgM Antibody Response in People Infected with Zika Virus: Implications for Interpreting Serologic Testing Results for Pregnant Women  [updated May 5, 2017]. Available from: https://emergency.cdc.gov/han/han00402.asp.


You can use the [editor on GitHub](https://github.com/StevenRussell/TB-Dekalb/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted

1. Numbered

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/StevenRussell/TB-Dekalb/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
