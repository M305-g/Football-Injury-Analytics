**Football Injury Analytics: Evaluating Injury Burden, Player Availability, and Post-Injury Performance**

I built this project to look at how injury burden affects player availability and performance. Using player injury, profile, and performance data, I combined Excel, Python, statistical analysis, and Tableau to identify injury patterns, performance differences, and positional risks — aimed at supporting evidence-based decisions for medical, performance, and coaching staff.

## Executive Summary

Injuries are one of the biggest operational and competitive challenges a football club deals with, and their impact goes well beyond the injury count itself — it shows up in availability, match participation, workload management, and potentially in performance too. I wanted to build a framework that actually connects those dots: injury burden, availability, performance outcomes, and player characteristics, rather than treating them as separate problems.

I integrated three datasets — Player Profile, Player Performance, and Player Injury — cleaning and preparing them in Excel and Python, with Python doing most of the heavy lifting for transformation, validation, integration, exploratory analysis, and statistical testing. I made a deliberate call not to artificially fill in missing values anywhere, because I wanted to preserve the integrity of the original data rather than paper over gaps with assumptions.

What I found was a huge amount of variation in injury burden. The injury dataset held 143,085 injury records across 34,561 unique players. Injury duration averaged 51.7 days (median 22), and games missed averaged 6.6 (median 3).

At the player-season level, the differences were stark — 11,201 player-seasons involved more than 180 days missed. As injury burden rose, competitive exposure and performance dropped with it: mean appearances fell from 34.6 in the Low-burden group to 23.3 in the High-burden group, and mean minutes played fell from 806.6 to 502.

I ran Kruskal–Wallis tests across injury-burden groups for appearances, minutes played, goals, and assists, and every one came back significant (p < 0.001). Injury duration also varied significantly by playing position (H = 47.600, p < 0.001), and so did performance across positions for all four outcomes.

What this tells me is that injury burden shouldn't be judged by injury count alone. Bringing duration, games missed, availability, performance, and position into one framework gives a much more complete picture of competitive risk than counting incidents ever could.

## Impact of the Project

The core thing I built here is a burden-classification framework — Low, Moderate, High, Very High — that lets medical and performance staff triage players by their cumulative absence risk instead of reacting to each injury as a one-off event. That's a real shift: from tracking individual incidents to managing injury risk across the whole squad like a portfolio.

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

This isn't just charts and p-values — it's a demonstration of how disconnected football data can become genuinely actionable intelligence.

## Project Objective

To quantify the competitive impact of player injuries by evaluating **injury burden, player availability, and performance outcomes**, in order to support evidence-based medical, performance, and squad-management decisions.

## Research Questions

1. **Which injury patterns create the greatest competitive risk through reduced player availability?**

2. **How does injury burden influence player performance before and after returning to competition?**

3. **Which player profiles are associated with increased injury risk and greater performance disruption?**

I want to be upfront here: what I actually have is an evaluation of injury burden, availability, positional differences, and performance-group differences — not a true longitudinal pre-injury-vs-post-injury comparison. So my conclusions on post-injury performance are limited to what the player-season data can actually support.

## Stakeholders

### Medical Staff

Responsible for injury surveillance, injury-severity assessment, rehabilitation planning, return-to-competition management, and identifying players experiencing high injury burden.

### Performance Staff

Responsible for player availability monitoring, workload management, performance analysis, and integration of medical and performance information.

### Head Coach

Responsible for squad selection, rotation, workload decisions, tactical planning, and interpreting player performance in the context of availability and injury burden.

## Dataset Overview

These datasets aren't tied to a single competition — they aggregate player records across multiple leagues and seasons rather than one national league or tournament.

**Player Profile**— player-level characteristics including Player ID, date of birth, and main playing position. Started at 92,671 rows × 35 columns, and after Excel cleaning and column selection came down to 92,671 rows × 19 columns. This is what let me look at positional differences in injury burden and performance.

**Player Performance** — player-season competitive data: Player ID, season, appearances, minutes played, goals, assists. Started at 1,878,719 rows × 20 columns, dropped to 1,048,575 rows × 20 columns after the Excel stage, and I then used Python for further cleaning and transformation — including building a standardized "Season name cleaned" field.

**Player Injury** — injury-event data: Player ID, season, injury reason, injury dates, days missed, games missed. Started at 143,195 rows × 7 columns, ended at 143,085 rows × 9 columns after cleaning. The final dataset covers 143,085 injury records across 34,561 unique injured players.

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

I worked in two stages: Excel first, then Python for anything that needed more complex transformation, validation, or processing — which ended up being most of the work on the large Player Performance and Player Injury datasets.

I made a firm call across all three datasets not to artificially impute missing values. Filling gaps with assumptions felt like it would compromise data-quality integrity more than it would help, so I kept missing observations as missing.

**Player Performance.** This dataset needed the most work, mainly because of its size and inconsistent season formats. I built a "Season name cleaned" field to standardize season naming so player-season analysis would actually be reliable. There was real missingness in some performance variables here too — I kept it rather than filling it in.

**Player Injury.** I added two quality-control fields — Calculated days missed and Days missed check — specifically to cross-check the injury-duration figures against the raw injury dates. The final dataset held 143,085 records.

## Data Integration

I linked all three datasets primarily through Player ID, which gave me the player-level connection between profile, injury, and performance information. That let me build three key relationships:

**Profile + Injury** — whether injury burden differs by characteristics like playing position.

**Profile + Performance** — position-specific performance profiles.

**Injury + Performance** — how injury burden relates to availability and competitive performance.

Which gives the overall workflow: Player Profile → Injury Burden → Player Availability → Performance.

One thing worth flagging: the injury and performance datasets don't cover the same time span — injury data spans 43 seasons, performance data spans 54. I left that mismatch as a documented limitation rather than forcing an artificial correction.

## Exploratory Data Analysis

**EDA 1 — Overall Injury Burden.** Across 143,085 injury records and 34,561 unique players, days missed averaged 51.7 (median 22, Q1 10, Q3 53, max 8,655), and games missed averaged 6.6 (median 3, Q1 1, Q3 7, max 208). This is purely descriptive — I haven't run a formal relationship test here yet. What it tells me: injury count alone badly undersells competitive burden. Duration and games missed add real information about what an injury actually costs a team.


**EDA 2 — Injury Patterns and Severity.** "Unknown injury" was the single most common category (27,011 records), but severity mattered more than frequency for total impact. Cruciate ligament tears — 4,034 records — generated 964,136 total days missed, averaging 239 days per case (median 218). Knee injuries (5,537 cases) racked up 499,508 total days missed, and Achilles tendon ruptures averaged around 203 days. Again, this is descriptive rather than a formal group comparison. What stands out: frequency and severity are two different risks. A rare injury can still be a major competitive burden if the recovery time is long enough.


**EDA 3 — Player-Season Injury Burden.** Across 93,194 player-season observations, the average burden was 1.5 injuries, 79 days missed, and 10 games missed per season. Breaking that into burden groups:

Low: 36,429 player-seasons, mean 15.4 days missed (median 15), mean 2.5 games missed (median 2)
Moderate: 31,960 player-seasons, mean 53.9 days missed (median 51), mean 8.1 games missed (median 8)
High: 13,604 player-seasons, mean 126 days missed (median 122), mean 17 games missed (median 16)
Very High: 11,201 player-seasons, mean 303 days missed (median 248), mean 32 games missed (median 30)

This is a descriptive classification, but it makes the case clearly: injury burden is heavily concentrated, with a real subgroup of players carrying a very high load. That's exactly why I think risk stratification makes more sense than treating every injured player-season the same.


**EDA 4 — Injury Burden and Player Availability.** I found negative relationships between burden and availability: total days missed vs. appearances (r = −0.30), total games missed vs. appearances (r = −0.29), total days missed vs. minutes played (r ≈ −0.10), total games missed vs. minutes played (r ≈ −0.10), and total days missed vs. total games missed (r = 0.60). I ran correlation analysis to confirm the direction and strength here. What this suggests to me: heavier injury burden more strongly predicts whether a player gets selected at all (r ≈ −0.30) than how much they play once they are selected (r ≈ −0.10) — a distinction that matters differently for rotation decisions versus starting-XI decisions.


**EDA 5 — Injury Burden and Competitive Performance.** Performance dropped as burden rose:

Low burden: 34.6 mean appearances, 806.6 mean minutes, 3.4 mean goals, 2.4 mean assists
Moderate burden: 31.5 mean appearances, 693 mean minutes, 3.0 mean goals, 2.0 mean assists
High burden: 23.3 mean appearances, 502 mean minutes, 2.0 mean goals, 1.4 mean assists

I ran Kruskal–Wallis tests across all four outcomes and every one came back significant: appearances (H = 9090), minutes played (H = 1406.57), goals (H = 1094.6), assists (H = 1342.5), all p < 0.001. Rising injury burden clearly comes with a meaningful drop in both exposure and output.


**EDA 6 — Playing Position and Injury Duration.**

Defender: 50,224 injury records, 11,619 injured players, mean 52.0 days missed (median 22)
Midfield: 42,465 injury records, 10,208 injured players, mean 51.5 days missed (median 22)
Attack: 41,044 injury records, 9,709 injured players, mean 46.9 days missed (median 22)
Goalkeeper: 9,391 injury records, 3,025 injured players, mean 57.7 days missed (median 25)

Kruskal–Wallis confirmed a significant difference across positions (H = 47.600, p ≈ 2.59 × 10⁻¹⁰, so p < 0.001). Injury duration genuinely does vary by position, which is why I think position-specific injury surveillance is worth building out. One caveat worth being upfront about: this test tells me there's an overall difference, not which specific position pairs actually differ from each other.


### EDA 7 — Playing Position and Performance

Attack: 29.8 appearances, 449 minutes played, 6 goals, 3 assists
Defender: 29.6 appearances, 632 minutes played, 1 goal, 1 assist
Goalkeeper: 31.5 appearances, 1,811 minutes played, 0 goals, 0 assists
Midfield: 30.0 appearances, 623 minutes played, 2.5 goals, 2 assists

All four outcomes differed significantly by position: appearances (H = 78.634, p ≈ 6.03 × 10⁻¹⁷), minutes played (H = 4403.275), goals (H = 17,496), assists (H = 9494.353) — all p < 0.001. This confirms what I'd expect: position drives performance profile strongly enough that raw metrics really only make sense read within positional context.

**EDA 8 — Injury Burden and Performance Profile,** Combined. Putting EDA 5 and EDA 7 together, the pattern holds up consistently: higher burden means lower exposure and lower output, and the medians tell the same story as the means. I didn't need to run a separate test here — the EDA 5 Kruskal–Wallis results already establish this statistically across all four outcomes (p < 0.001 throughout). Together, the descriptive and statistical evidence point the same direction: heavier injury burden comes with meaningfully different competitive exposure and performance.

## Statistical Analysis

I designed this section to check which patterns from the EDA actually held up under formal testing. Given the shape of the outcome distributions and group structures, parametric assumptions didn't hold, so I used non-parametric methods throughout.

Injury burden vs. performance. Kruskal–Wallis testing showed significant differences across burden groups for appearances (H = 9090), minutes played (H = 1406.57), goals (H = 1094.6), and assists (H = 1342.5), all p < 0.001. I want to flag something important here: with a sample this large (93,194 player-seasons), statistical significance was almost guaranteed even for fairly modest effects. A useful next step would be calculating effect sizes (epsilon-squared) to see how much these differences actually matter in practice, not just whether they're statistically real.

Position vs. injury duration. H = 47.600, p ≈ 2.588 × 10⁻¹⁰ — so p < 0.001.

Position vs. performance. Appearances (H = 78.634, p < 0.001), minutes played (H = 4403.275, p < 0.001), goals (H = 17,496, p < 0.001), assists (H = 9494.353, p < 0.001).

These results tell me there are real overall group differences — they don't tell me which specific pairs differ from each other. And I want to be clear: statistical significance here means association or group difference, not causation.


## Tableau Dashboards & Visualizations

I built these to turn the confirmed analytical findings into something Medical Staff, Performance Staff, and coaching can actually use day to day.

**Dashboard 1** — Injury Burden & Competitive Impact. An overview of the scale and distribution of injuries and their competitive cost — injury records by season, total days missed by injury reason, and games missed by injury reason. Aimed at Medical and Performance Staff.

**Dashboard 2** — Injury Burden & Player Performance. I'd planned to visualize the relationship between injury burden and performance directly — appearances, minutes, goals, assists — but I made the call to leave those visualizations out of the final build. The Tableau-ready performance file didn't contain all the variables I'd used during the EDA and statistical work, and I'd rather ship a dashboard with a gap than one built on incomplete or mismatched data. Aimed at Performance Staff and the Head Coach.

**Dashboard 3** — Positional Injury Profile. Total days missed by playing position — defenders, midfielders, attackers, and goalkeepers compared directly. This one reflects the Kruskal–Wallis result on positional differences in days missed. Aimed at Medical Staff, Performance Staff, and the Head Coach.


## Key Findings 

Injury burden is highly uneven. The spread in days missed and games missed makes it clear that injury count on its own isn't enough to judge competitive risk — surveillance needs to account for both frequency and severity.

High burden concentrates in a real subgroup. More than 11,000 player-seasons crossed 180 days missed. That's a strong case for a targeted high-burden monitoring system rather than treating every injured player the same.

Heavier burden means lower availability. Both days missed and games missed showed a negative relationship with appearances — availability and injury burden really need to be tracked together, not as separate concerns.

Injury burden shows up in performance too. All four outcomes I tested — appearances, minutes, goals, assists — differed significantly across burden groups. Injury history is relevant context for reading a player's output, not a side note.

Injury duration depends on position. The Kruskal–Wallis result held up here — position-specific context genuinely helps with surveillance and rehab planning.

Performance is position-dependent too. All four outcomes differed significantly by position, which is exactly why players need to be judged against positional benchmarks, not one squad-wide standard.



## Stakeholder-Specific Recommendations

### Medical Staff

Build injury-burden monitoring around count, days missed, and games missed together — not injury count alone.

Give players in the High and Very High burden categories priority for medical review.

Build out position-specific injury surveillance, since duration genuinely differs by position.

Keep using calculated injury-duration checks as an ongoing data-quality safeguard.

Fold injury-burden history into rehab and return-to-competition planning.


### Performance Staff

Tie injury burden directly into availability monitoring.

Track appearances and minutes alongside burden to catch drops in competitive exposure early.

Build injury burden into workload and performance-monitoring frameworks.

Use position-specific benchmarks — performance genuinely differs enough by position to warrant it.

Watch players returning from high burden closely when reading their competitive output.

### Head Coach

Factor injury burden into squad-selection and rotation calls.

Don't read performance metrics in isolation — availability and position both matter for interpretation.

Treat injury-burden data as one input among several for workload and squad decisions, not the whole picture.

Keep contingency plans ready for positions carrying higher injury-burden risk.

Combine medical, performance, and tactical information rather than leaning on a single indicator

## AFCON Relevance & Practical Application

This wasn't built on AFCON data specifically, but the framework transfers well to a tournament environment like the Africa Cup of Nations, where squads face limited depth, a compressed schedule, travel demands, and short recovery windows.

That makes it useful for: squad availability planning before and during the tournament, flagging players with a heavy injury history, position-specific medical and performance monitoring, workload and rotation planning, return-to-competition monitoring, contingency planning for higher-risk positions, and folding medical and performance intelligence into squad decisions overall. A national team could realistically adapt this for injury surveillance and tournament preparation

## Limitations

I want to be upfront about where this falls short.

The injury and performance datasets don't share the same time span — 43 seasons of injury data against 54 seasons of performance data.

I kept missing values rather than imputing them, which protects data integrity but does shrink the observation count for some analyses.

A large share of injury records fall under "Unknown injury," which limits how precise I can get on injury-specific interpretation.

Everything here shows association and group difference, not causation — a significant Kruskal–Wallis result doesn't prove injury burden directly caused a drop in performance.

This isn't a true pre-injury-vs-post-injury longitudinal study. What I actually have covers injury burden, availability, positional differences, and performance differences across groups — not a before/after comparison for individual players.

erformance is shaped by plenty of things this dataset doesn't capture — tactical role, team quality, competition level, playing-time opportunity, transfers, coaching changes, workload exposure.

Position categories are limited to four broad groups (Goalkeeper, Defender, Midfield, Attack), which masks real sub-positional variation — a full-back and a center-back, or a winger and a striker, almost certainly carry different injury and performance profiles that this level of grouping can't see.

I chose not to include some planned Tableau visualizations rather than rebuild them on incomplete or mismatched variables — the player-season-level analysis used fields (injury-burden categories, appearances, minutes, goals, assists) that weren't available in the required form in the Tableau-ready dataset. I'd rather leave a documented gap than compromise data integrity or reproducibility, and the underlying findings are still fully documented in the EDA and Statistical Analysis sections.

Last, I didn't keep the post-hoc pairwise statistical outputs in the final report — running them produced unreliable, duplicated results, so I chose to report the robust overall Kruskal–Wallis findings instead of making claims about specific group pairs I couldn't actually back up.


## Future Improvements / Next Steps

Given more time and data, I'd want to bring in: training and match workload data, GPS and physical-performance metrics, injury recurrence, injury severity classification, player exposure data, age and career stage, competition level, tactical role, position-specific workload, a genuine pre-injury-vs-post-injury comparison, multivariable regression or longitudinal modelling, and predictive modelling for injury burden and availability.

That's the direction I'd want to take this — from descriptive and inferential analysis toward something genuinely predictive and prescriptive.

## Conclusion

What I set out to do here was turn football injury data into a real decision-support framework — one that connects injury burden, availability, performance, and player profile instead of treating them separately.

I found substantial variation in injury burden, with a real subgroup of player-seasons carrying a very high load. Injury burden was tied to lower availability, and I found statistically significant differences across burden groups for appearances, minutes played, goals, and assists. Playing position mattered too — both injury duration and performance outcomes varied significantly by position, which tells me competitive risk needs to be read through both burden and positional context together.

The practical value here is bringing medical and performance intelligence into one place. For Medical Staff, it supports surveillance and prioritization. For Performance Staff, it's a framework for folding availability and burden into performance monitoring. For the Head Coach, it's extra evidence for squad selection, rotation, and workload calls. And it transfers cleanly to a tournament setting like AFCON, where availability and squad depth carry real competitive weight.

If there's one thing I'd want this project to argue for, it's that injury analytics needs to move past just counting incidents. The more useful chain is severity → availability → performance → decision-making — approached with real statistical caution and an honest read of what observational football data can and can't tell you.


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
