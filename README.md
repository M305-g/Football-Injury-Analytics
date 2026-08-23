# Football-Injury-Analytics: Evaluating Injury Burden, Player Availability and Post Injury Performance
Football Injury Analytics examines how injury burden affects player availability and performance. Using player injury, profile, and performance data, the project applies Excel, Python, statistical analysis, and Tableau to identify injury patterns, performance differences, and positional risks, supporting evidence-based decisions for medical, performance and coaching staff.

## Executive Summary

Player injuries represent a major operational and competitive challenge in professional football. Their impact extends beyond the number of injury incidents, affecting player availability, match participation, workload management, and potentially competitive performance. This project applies a data-driven framework to evaluate the relationship between injury burden, player availability, performance outcomes, and player characteristics.

The analysis integrates three complementary football datasets: **Player Profile, Player Performance, and Player Injury**. The datasets were prepared and cleaned using Excel and Python, with Python used extensively for transformation, validation, integration, exploratory analysis, and statistical testing. No missing values were artificially imputed in order to preserve the integrity of the original data.

The analysis identified substantial variation in injury burden. The injury dataset contained **143,085 injury records involving 34,561 unique players**. Injury duration had a mean of **51.7 days** and a median of **22 days**, while games missed had a mean of **6.6** and a median of **3**.

Player-season analysis showed substantial differences in injury burden, with **11,201 player-seasons experiencing more than 180 days missed**. Increasing injury burden was accompanied by progressively lower competitive exposure and performance. Mean appearances declined from **34.6 in the Low-burden group to 23.3 in the High-burden group**, while mean minutes played declined from **806.6 to 502**.

Statistical analysis confirmed significant overall differences across injury-burden groups for appearances, minutes played, goals, and assists, with all Kruskal–Wallis tests producing **p < 0.001**. Injury duration also differed significantly across playing positions (**H = 47.600, p < 0.001**), while performance outcomes differed significantly across positions for appearances, minutes played, goals, and assists.

The project therefore demonstrates that injury burden should not be evaluated solely through injury frequency. Combining injury duration, games missed, availability, performance, and player position provides a more comprehensive framework for assessing competitive risk and supporting evidence-based football decisions.

## Impact of the Project

The project's core contribution is a burden-classification framework (Low/Moderate/High/Very High) that lets medical and performance staff triage players by cumulative absence risk rather than reacting to individual injury events one at a time. This reframes injury management from incident-tracking to portfolio-risk management across a squad.

### What I Have Contributed to This Project

I contributed an integrated analytical approach that connects **medical information with football performance data**. The project moves from raw injury records to player-season injury burden and then connects this burden with player availability, performance, and positional characteristics.

The project also demonstrates the ability to:

* Prepare and clean large football datasets.
* Validate injury-duration measures using calculated fields.
* Standardise season information for player-season analysis.
* Integrate player profile, injury, and performance datasets.
* Conduct exploratory data analysis.
* Apply non-parametric statistical tests to football data.
* Translate statistical findings into football-specific insights.
* Develop stakeholder-specific recommendations.
* Design a decision-support framework applicable to professional football environments.

The practical value of the project is therefore not limited to producing charts or statistical outputs. It demonstrates how heterogeneous football data can be transformed into **actionable performance intelligence**.

## Project Objective

To quantify the competitive impact of player injuries by evaluating **injury burden, player availability, and performance outcomes**, in order to support evidence-based medical, performance, and squad-management decisions.

## Research Questions

1. **Which injury patterns create the greatest competitive risk through reduced player availability?**

2. **How does injury burden influence player performance before and after returning to competition?**

3. **Which player profiles are associated with increased injury risk and greater performance disruption?**

The available analysis primarily evaluates injury burden, availability, positional differences, and performance-group differences. A true longitudinal pre-injury versus post-injury comparison was not performed; therefore, conclusions concerning post-injury performance are limited to the relationships supported by the available player-season data.

## Stakeholders

### Medical Staff

Responsible for injury surveillance, injury-severity assessment, rehabilitation planning, return-to-competition management, and identifying players experiencing high injury burden.

### Performance Staff

Responsible for player availability monitoring, workload management, performance analysis, and integration of medical and performance information.

### Head Coach

Responsible for squad selection, rotation, workload decisions, tactical planning, and interpreting player performance in the context of availability and injury burden.

## Dataset Overview

The datasets do not specify a single competition; they aggregate player records across multiple professional leagues and seasons rather than one national league or tournament.

The project uses three complementary datasets.

### Player Profile Dataset

The Player Profile dataset provides player-level characteristics, including **Player ID, date of birth, and main playing position** among other profile attributes.

Before cleaning, the dataset contained:

**92,671 rows × 35 columns**

After Excel-based cleaning and column selection, it contained:

**92,671 rows × 19 columns**

The dataset provided the player-profile dimension required to investigate positional differences in injury burden and performance.

### Player Performance Dataset

The Player Performance dataset contains player-season competitive performance information, including:

* Player ID
* Season
* Appearances
* Minutes played
* Goals
* Assists

Before cleaning, the dataset contained:

**1,878,719 rows × 20 columns**

After the Excel stage, the working dataset contained:

**1,048,575 rows × 20 columns**

Python was subsequently used for further cleaning and transformation, including the creation of the standardised **`Season name cleaned`** field.

### Player Injury Dataset

The Player Injury dataset contains injury-event information, including:

* Player ID
* Season
* Injury reason
* Injury dates
* Days missed
* Games missed

Before cleaning, the dataset contained:

**143,195 rows × 7 columns**

After cleaning and transformation, it contained:

**143,085 rows × 9 columns**

The final injury dataset contained **143,085 injury records involving 34,561 unique injured players**.

## Tools & Technologies

### Microsoft Excel

Used for initial dataset inspection, cleaning, structural preparation, and removal/selection of unnecessary fields.

### Python

Used extensively for data cleaning, transformation, validation, integration, exploratory analysis, and statistical analysis.

### Pandas

Used for data manipulation, grouping, aggregation, merging, missing-value assessment, and creation of analytical datasets.

### SciPy

Used for non-parametric statistical testing, including **Kruskal–Wallis** and **Mann–Whitney** procedures.

### Tableau

Used to convert the analytical results into interactive dashboards and decision-support visualizations.

## Data Preparation & Cleaning

Data preparation was performed in two stages: **initial Excel cleaning followed by Python-based cleaning, transformation, and validation**.

Excel was used as the initial preparation environment. Tasks that required more complex transformation, validation, or processing—particularly within the large Player Performance and Player Injury datasets—were subsequently performed in Python.

No missing values were artificially imputed in any of the datasets. Missing observations were retained to avoid introducing assumptions or fabricated information and to preserve data-quality integrity.

### Player Performance Preparation

The Player Performance dataset required substantial processing because of its large size and inconsistent season representations.

A new **`Season name cleaned`** field was created to standardise season naming and support reliable player-season analysis.

The dataset also contained substantial missingness in some performance variables. These values were retained rather than artificially filled.

### Player Injury Preparation

The Player Injury dataset was enhanced with additional quality-control fields:

* **Calculated days missed**
* **Days missed check**

These fields were created to compare and validate injury-duration information derived from the available injury dates against the recorded duration.

The final injury dataset contained **143,085 records**.

## Data Integration

The three datasets were integrated primarily through **Player ID**, which provided the player-level linkage between profile, injury, and performance information.

The integration enabled three major analytical relationships:

**Player Profile + Player Injury**
Used to investigate whether injury burden differed according to characteristics such as playing position.

**Player Profile + Player Performance**
Used to establish position-specific performance profiles.

**Player Injury + Player Performance**
Used to evaluate injury burden in relation to player availability and competitive performance.

The integrated analytical workflow therefore followed:

**Player Profile → Injury Burden → Player Availability → Performance**

The injury and performance datasets did not have identical temporal coverage. The injury dataset contained **43 seasons**, while the performance dataset contained **54 seasons**. This difference was retained as a data limitation rather than being artificially corrected.

## Exploratory Data Analysis

### EDA 1 — Overall Injury Burden

The injury dataset contained **143,085 injury records involving 34,561 unique players**.

Days missed had:

* Mean: **51.7 days**
* Median: **22 days**
* Q1: **10 days**
* Q3: **53 days**
* Maximum: **8,655 days**

Games missed had:

* Mean: **6.6 games**
* Median: **3 games**
* Q1: **1 game**
* Q3: **7 games**
* Maximum: **208 games**

The results demonstrate substantial variation in injury duration and competitive absence.

**Statistical status:** Descriptive EDA; no formal relationship test was performed.

**Insight:** Injury frequency alone does not adequately represent competitive injury burden. Duration and games missed provide additional information about the practical impact of injuries.

### EDA 2 — Injury Patterns and Severity

The most frequent injury reason was **Unknown injury**, with 27,011 records. However, severe injuries generated disproportionately large absence durations.

Cruciate ligament tears recorded:

* 4,034 injury records
* 964,136 total days missed
* Mean: **239 days missed**
* Median: **218 days missed**

Knee injuries recorded 5,537 cases and generated **499,508 total days missed**, while Achilles tendon rupture had a mean absence of approximately **203 days**.

**Statistical status:** Descriptive analysis; no independent statistical group comparison was performed.

**Insight:** Frequency and severity represent different dimensions of competitive risk. A relatively uncommon injury can create a substantial competitive burden because of prolonged absence.

### EDA 3 — Player-Season Injury Burden

The player-season injury dataset contained **93,194 player-season observations**.

Average injury burden per player-season was:

* Injury count: **1.5**
* Days missed: **79**
* Games missed: **10**

The burden distribution showed:

| Burden Group | Player-Seasons | Mean Days Missed | Median Days Missed | Mean Games Missed | Median Games Missed |
| ------------ | -------------: | ---------------: | -----------------: | ----------------: | ------------------: |
| Low          |         36,429 |             15.4 |                 15 |               2.5 |                   2 |
| Moderate     |         31,960 |             53.9 |                 51 |               8.1 |                   8 |
| High         |         13,604 |              126 |                122 |                17 |                  16 |
| Very High    |         11,201 |              303 |                248 |                32 |                  30 |

**Statistical status:** Descriptive burden classification.

**Insight:** Injury burden is highly concentrated, with a substantial subgroup experiencing very high levels of absence. This supports risk stratification rather than treating every injured player-season as equivalent.

### EDA 4 — Injury Burden and Player Availability

Injury burden demonstrated negative associations with player availability.

The main exploratory relationships were:

* Total days missed vs appearances: **r = −0.30**
* Total games missed vs appearances: **r = −0.29**
* Total days missed vs minutes played: **r ≈ −0.10**
* Total games missed vs minutes played: **r ≈ −0.10**
* Total days missed vs total games missed: **r = 0.60**

**Statistical status:** Correlation analysis confirmed the direction and strength of these observed associations.

**Insight:** Greater injury burden shows a weak-to-moderate negative association with appearances (r ≈ −0.30) and a negligible association with total minutes played (r ≈ −0.10). This suggests injury burden more strongly predicts whether a player is selected than how much they play once selected — a distinction relevant for squad rotation versus starting-XI decisions.

### EDA 5 — Injury Burden and Competitive Performance

Performance declined descriptively as injury burden increased.

| Injury Burden | Mean Appearances | Mean Minutes | Mean Goals | Mean Assists |
| ------------- | ---------------: | -----------: | ---------: | -----------: |
| Low           |             34.6 |        806.6 |        3.4 |          2.4 |
| Moderate      |             31.5 |          693 |        3.0 |          2.0 |
| High          |             23.3 |          502 |        2.0 |          1.4 |

Kruskal–Wallis testing confirmed statistically significant differences across injury-burden groups:

* Appearances: **H = 9090, p < 0.001**
* Minutes played: **H = 1406.57, p < 0.001**
* Goals: **H = 1094.6, p < 0.001**
* Assists: **H = 1342.5, p < 0.001**

**Insight:** Increasing injury burden is associated with significant differences in competitive exposure and performance outcomes.

### EDA 6 — Playing Position and Injury Duration

Injury burden differed descriptively by playing position.

| Main Position | Injury Records | Injured Players | Mean Days Missed | Median Days Missed |
| ------------- | -------------: | --------------: | ---------------: | -----------------: |
| Defender      |         50,224 |          11,619 |             52.0 |                 22 |
| Midfield      |         42,465 |          10,208 |             51.5 |                 22 |
| Attack        |         41,044 |           9,709 |             46.9 |                 22 |
| Goalkeeper    |          9,391 |           3,025 |             57.7 |                 25 |

Kruskal–Wallis testing confirmed a statistically significant difference in injury duration across playing positions:

**H = 47.600, p = 2.5877504851791225 × 10⁻¹⁰**

Therefore, **p < 0.001**.

**Insight:** Injury duration varies significantly across playing positions, supporting the use of position-specific injury surveillance.

The Kruskal–Wallis result confirms an overall positional difference but does not identify which specific position pairs differ.

### EDA 7 — Playing Position and Performance

Performance differed descriptively across playing positions.

Mean performance values were:

| Main Position | Appearances | Minutes Played | Goals | Assists |
| ------------- | ----------: | -------------: | ----: | ------: |
| Attack        |        29.8 |            449 |     6 |       3 |
| Defender      |        29.6 |            632 |     1 |       1 |
| Goalkeeper    |        31.5 |          1,811 |     0 |       0 |
| Midfield      |        30.0 |            623 |   2.5 |       2 |

Kruskal–Wallis testing confirmed statistically significant differences across positions:

* Appearances: **H = 78.634, p = 6.026 × 10⁻¹⁷**
* Minutes played: **H = 4403.275, p < 0.001**
* Goals: **H = 17,496, p < 0.001**
* Assists: **H = 9494.353, p < 0.001**

**Insight:** Player position is strongly associated with differences in performance profiles. Raw performance metrics should therefore be interpreted within positional context.

### EDA 8 — Injury Burden and Performance Profile

The combined analysis showed a consistent descriptive pattern in which higher injury burden was accompanied by lower competitive exposure and lower raw performance output.

Low-burden players recorded:

* 34.6 appearances
* 806.6 minutes
* 3.4 goals
* 2.4 assists

High-burden players recorded:

* 23.3 appearances
* 502 minutes
* 2 goals
* 1.4 assists

Median values demonstrated the same pattern.

**Statistical status:** The statistical confirmation for this relationship comes from the EDA 5 Kruskal–Wallis analysis, where all four outcomes differed significantly across injury-burden groups (**p < 0.001**). No duplicate statistical test was required.

**Insight:** The combined descriptive and statistical evidence indicates that higher injury burden is associated with substantially different competitive exposure and performance outcomes.

## Statistical Analysis

The statistical analysis was designed to determine which observed EDA patterns were sufficiently supported by formal statistical testing.

Because the outcome distributions and group structures did not justify reliance on parametric assumptions, non-parametric methods were used.

### Confirmed Relationships

**Injury burden vs performance**

Kruskal–Wallis testing showed significant overall differences between injury-burden groups for appearances (H = 9090), minutes played (H = 1406.57), goals (H = 1094.6), and assists (H = 1342.5), all p < 0.001. Given the large sample size (n = 93,194 player-seasons), statistical significance was expected even for modest effects; effect sizes (epsilon-squared) should be calculated in future iterations to determine practical magnitude alongside statistical significance.

**Position vs injury duration**

* **H = 47.600**
* **p = 2.588 × 10⁻¹⁰**
* **p < 0.001**

**Position vs performance**

Significant overall differences were identified for:

* Appearances — **H = 78.634, p < 0.001**
* Minutes played — **H = 4403.275, p < 0.001**
* Goals — **H = 17,496, p < 0.001**
* Assists — **H = 9494.353, p < 0.001**

These results confirm the presence of overall group differences but do not establish which individual pairs differ.

Importantly, statistical significance is interpreted as evidence of an association or group difference, **not evidence of causation**.

## Tableau Dashboards & Visualizations

The Tableau component translates selected analytical findings into interactive visualizations that support evidence-based decision-making across medical, performance, and coaching contexts.

**Dashboard 1 — Injury Burden & Competitive Impact**

This dashboard provides an overview of the scale, distribution, and competitive impact of player injuries.

Key visualizations:

Injury Records by Season — shows how injury records are distributed across seasons.
Total Days Missed by Injury Reason — identifies injury reasons associated with the greatest cumulative loss of playing time.
Games Missed by Injury Reason — highlights injury reasons associated with the greatest number of missed games.

Primary stakeholders: Medical Staff and Performance Staff.

**Dashboard 2 — Injury Burden & Player Performance**

This dashboard was intended to visualize the relationship between injury burden and player performance, particularly appearances, minutes played, goals, and assists.

However, these performance visualizations were not included in the final Tableau implementation because the Tableau-ready performance file available for visualization did not contain all the required performance variables used during the EDA and statistical analysis.

Primary stakeholders: Performance Staff and Head Coach.

**Dashboard 3 — Positional Injury Profile**

This dashboard examines differences in injury burden across playing positions.

Key visualization:

Total Days Missed by Playing Position — compares cumulative injury-related days missed across defenders, midfielders, attackers, and goalkeepers.

This visualization reflects the statistically significant positional difference in days missed identified through the Kruskal–Wallis analysis.

Primary stakeholders: Medical Staff, Performance Staff, and Head Coach.

## Key Findings & Insights

### Finding 1 — Injury burden is highly heterogeneous

The large variation in days missed and games missed demonstrates that injury count alone is insufficient for evaluating competitive risk.

**Insight:** Injury surveillance should incorporate both frequency and severity.

### Finding 2 — High injury burden is concentrated in a substantial player-season subgroup

More than 11,000 player-seasons experienced more than 180 days missed.

**Insight:** A targeted high-burden monitoring system can help identify players requiring greater medical and performance attention.

### Finding 3 — Greater injury burden is associated with reduced availability

Days missed and games missed showed negative relationships with appearances.

**Insight:** Player availability should be monitored alongside injury burden rather than treated as a separate operational issue.

### Finding 4 — Injury burden is associated with significant differences in performance

All four performance outcomes tested across injury-burden groups were statistically significant.

**Insight:** Injury burden should be considered when interpreting player performance and competitive contribution.

### Finding 5 — Injury duration differs significantly by playing position

The Kruskal–Wallis test demonstrated a statistically significant overall positional difference in days missed.

**Insight:** Injury surveillance and rehabilitation planning can benefit from position-specific context.

### Finding 6 — Performance profiles are position-dependent

All four performance outcomes differed significantly across positions.

**Insight:** Player performance should be evaluated against appropriate positional benchmarks rather than using a single benchmark across the squad.

## Stakeholder-Specific Recommendations

### Medical Staff

1. Implement an injury-burden monitoring framework based on **injury count, days missed, and games missed** rather than injury count alone.
2. Prioritise players within **High and Very High injury-burden categories** for enhanced medical review.
3. Develop position-specific injury surveillance because injury duration differed significantly across playing positions.
4. Use calculated injury-duration checks as part of ongoing data-quality assurance.
5. Integrate injury-burden history into rehabilitation and return-to-competition planning.

### Performance Staff

1. Integrate injury burden with player-availability monitoring.
2. Track appearances and minutes alongside injury burden to identify reductions in competitive exposure.
3. Incorporate injury burden into workload and performance-monitoring frameworks.
4. Use position-specific performance benchmarks because performance outcomes differ significantly by position.
5. Monitor players returning from high injury burden closely when evaluating their competitive output.

### Head Coach

1. Consider injury burden when making squad-selection and rotation decisions.
2. Avoid interpreting performance metrics without considering player availability and playing position.
3. Use injury-burden information as one component of workload and squad-management decisions.
4. Maintain contingency options for positions where injury burden may create greater availability risk.
5. Combine medical, performance, and tactical information rather than relying on a single performance indicator.

## AFCON Relevance & Practical Application

Although this analysis is not based specifically on AFCON tournament data, the framework is transferable to tournament environments such as the **Africa Cup of Nations**.

AFCON environments can create particular challenges because teams operate with limited squad depth, intensive competition schedules, travel demands, and relatively short recovery periods.

The findings can therefore support:

* **Squad availability planning** before and during tournaments.
* Identification of players with substantial historical injury burden.
* Position-specific medical and performance monitoring.
* Workload and rotation planning.
* Return-to-competition monitoring.
* Contingency planning for high-risk positions.
* Integration of medical and performance intelligence into squad decisions.

The project therefore provides a transferable framework that could be adapted by a national team to support **injury surveillance, player availability management, and tournament preparation**.

## Limitations

Several limitations should be considered when interpreting the findings.

First, the injury and performance datasets had different temporal coverage. The injury dataset contained **43 seasons**, whereas the performance dataset contained **54 seasons**.

Second, missing values were retained rather than imputed. Although this protects data integrity, it may reduce the number of observations available for some analyses.

Third, some injury records had an **Unknown injury** classification, limiting the precision of injury-specific interpretation.

Fourth, the statistical analyses establish **associations and group differences rather than causality**. A significant Kruskal–Wallis result does not demonstrate that injury burden directly caused a reduction in performance.

Fifth, the analysis did not constitute a true longitudinal pre-injury versus post-injury performance study. The available results primarily examine injury burden, player availability, positional differences, and performance differences across groups.

Sixth, player performance can be influenced by many factors not captured in the available datasets, including tactical role, team quality, competition level, playing time opportunity, transfers, coaching changes, and workload exposure.

Seventh, position categories were limited to four broad groups (Goalkeeper, Defender, Midfield, Attack). This masks meaningful sub-positional variation (e.g., full-back vs. center-back, winger vs. striker) that likely carries distinct injury and performance profiles.

Eighth, Some planned visualizations were intentionally not included rather than being recreated using different or incomplete variables. The EDA and statistical analyses were conducted at specific analytical levels, including player-season level, and some variables used in those analyses—such as injury-burden categories, appearances, minutes played, goals, and assists—were not available in the Tableau-ready datasets in the required form.

Therefore, these visualizations were excluded to maintain data integrity, analytical consistency, and reproducibility. The corresponding statistical findings remain documented in the EDA and Statistical Analysis sections of this project.

Finally, the post-hoc pairwise statistical outputs were not retained as confirmatory evidence because their execution produced unreliable/duplicated results. Therefore, the portfolio reports the robust **overall Kruskal–Wallis findings** rather than making unsupported claims about specific group pairs.

## Future Improvements / Next Steps

Future development of the project could incorporate additional variables and more advanced longitudinal analysis.

Potential extensions include:

* Training and match workload data.
* GPS and physical-performance metrics.
* Injury recurrence.
* Injury severity classification.
* Player exposure data.
* Age and career stage.
* Competition level.
* Tactical role.
* Position-specific workload.
* True pre-injury versus post-injury performance comparisons.
* Multivariable regression or longitudinal modelling.
* Predictive modelling for injury burden and player availability.

These additions would allow the framework to move from descriptive and inferential analysis toward **predictive and prescriptive football performance intelligence**.

## Conclusion

This project demonstrates how football injury data can be transformed into a structured decision-support framework linking **injury burden, player availability, performance, and player profile**.

The analysis showed substantial variation in injury burden and identified a significant subgroup of player-seasons experiencing very high levels of absence. Injury burden was associated with reduced player availability, while statistically significant differences were observed across injury-burden groups for appearances, minutes played, goals, and assists.

Playing position was also significantly associated with differences in injury duration and performance outcomes. These findings demonstrate the importance of considering both injury burden and positional context when evaluating competitive risk.

The practical contribution of the project is its integration of **medical and performance intelligence**. For Medical Staff, it supports injury surveillance and prioritisation. For Performance Staff, it provides a framework for integrating availability and injury burden into performance monitoring. For the Head Coach, it provides additional evidence to support squad selection, rotation, and workload decisions.

The framework is also transferable to tournament environments such as AFCON, where player availability and squad depth can have significant competitive implications.

Overall, the project demonstrates that effective football injury analytics should move beyond simply counting injuries. A more useful approach is to connect **injury severity → availability → performance → decision-making**, while maintaining appropriate statistical caution and recognising the limitations of observational football data.


MWANAHAMISI JUMA

Football Performance Analytics

+255787338398

mwanahamis050@gmail.com

Tableau Dashboard 1


https://public.tableau.com/app/profile/mwanahamisi.juma/viz/InjuryBurdenandPlayerPerfomance/InjuryBurdenandPlayerPerformance?publish=yes

Tableau Dashboard 2


https://public.tableau.com/app/profile/mwanahamisi.juma/viz/InjuryBurdenandPlayerPerfomance/InjuryBurdenandCompetitiveImpact?publish=yes

Linkedin 

www.linkedin.com/in/mwanahamisi-juma-00576b394
