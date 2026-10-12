---
title: "Summary: GeoDS — London gentrifying - Residential mobiblity since the turn of the century"
date: 2026-10-12
categories: [Literature Notes, Population Geography]
tags: [gentrification, displacement, neighbourhood change, urban inequality, residential mobility, population redistribution, London]
---

## Full Reference

Longley, P., van Dijk, J., Kimura, S., & Khurshid, R. (2026, January 16). London gentrifying: Residential mobility since the turn of the century. Geographic Data Service (GeoDS).

```bibtex
@online{longley2026london,
  author       = {Longley, Paul and van Dijk, Justin and Kimura, Shunya and Khurshid, Reem},
  title        = {London gentrifying: Residential mobility since the turn of the century},
  year         = {2026},
  date         = {2026-01-16},
  organization = {Geographic Data Service (GeoDS)},
  url          = {https://geods.ac.uk/2026/01/16/london-gentrifying-residential-mobility-since-the-turn-of-the-century/},
  urldate      = {2026-10-07},
  note         = {Data story; first in a series produced with Trust for London}
}
```

## Questions 

### What is the article about?

How residential mobility has reshaped England's major cities, and London's gentrified neighbourhoods in particular, between 2001 and 2025.
- city scale: 8 major English cities (Birminghan, Bristol, Leeds, Leicester, Liverpool, Manchester, Sheffield, London). Each city's share of UK residential turnover, the distances people move into and out of them, and whether moving in/out improves or worsens the neighbourhood people live in.
- neighbourhood scale: the 53 London MSOAs that the Trust for London classed as "gentrified". Tracking their inflows, inflow distances, and the deprivation of the places incomers came from.

Question: How geographic mobility relates to social mobility, framed through the idea of London and gentrifying areas within it as an "escalator". (This question is still unresolved to me, after reading Champion's (2012) paper "Testing the Return Migration Element of the Escalator Region Model" - have summarised reading thoughts of this paper and posted)

> This is the reverse analytical order: 
>
> Gentrified areas are identified first (by income change), and population movement is then described within them.
{: .prompt-info }

### What kind of contribution is the paper trying to make?

Empirical and descriptive. This isn't a peer-reviewed paper - it showcases what the GeoDS Linked Consumer Registers (LCRs) can reveal, ffering long-run, annual, small-area trends. Also no formal hypothesis testing or modelling.

### What gap(s) does it identify/tackle?

- Data gap: census-based mobility analysis gives decennial snapshots; LCRs allow annual tracking over 25 years at neighbourhood level, including move distances and origin-destination deprivation.
- Conception test: gentrification as "wealthier incomers raise demand and prices and displace incumbents, so heightened churn is read as a signal of gentrification". This tests what churn actually looks like in gentrified areas.

### What is/are the main research questions(s)/argument(s)?

1. How much for major cities contribute to UK residential turnover (into / out of / within), and is London different?
2. How far do people move into and out of these cities, and how has this changed?
3. Is spatial mobility accompanied by social mobility (measured as change in neighbourhood deprivation betweem origin and destination)?
4. Within London's 53 gentrified neighbourhoods: how do inflows, inflow distances and incomers' origin deprivation compare wiht the London average, and do they vary between neighbourhoods and over time?

**Gentrification is not a single, uniform or linear process.** Neighbourhoods follow different trajectories and gentrified areas amplify London's escalator effects.

### How are they explored/presented?

Visual, descriptive comparison across time and space.
- Smoothed time-series line charts of city shares of UK moves (into / out of / within), 2001-2025.
- Median move distances into and out of each city -- gentrified London plotted vs. London overall and the other cities.
- Mean change in IMD percentile between origin and destination for moves into and out of each city (Residential Mobility and Deprivation measure).
- Heatmaps across the 53 gentrified MSOAs for inflows relative to the London neighbourhood average, median inflow distance, incomers' origin deprivation relative to the London mean.
- Small-multiple case studies of selected neighbourhoods.

### How are data used to test them?

- Mobility data: GeoDS Linked Consumer Registers, linked consumer and electoral-roll-type records that let individuals' address changes be traced year by year (2001-2025) and aggregated to any geography.
- Median distance between origin and destination of UK residential moves.
- harmonised IMD, compared between origin and destination neighbourhoods within each temporal period.
- Trust for London's 53 MSOAs - lowest income quintile in 2012 but above-average growth in mean income by 2020 (ONS small-area income estimates, 2011/12 and 2019/20).
- ONS "major" built-up areas with usual resident population over 400,000.

### What are the main findings?

**City Scale**
- Moves into and out of major cities are a growing share of UK turnover, while the share of within-city moves has fallen - except London, whose within-city share stays broadly steady and exceeds its combined in- and outflows.
- People move into cities from increasingly long distances, and cities draw from farther away than they send people. 
    - London leads: median inflow distance ~114km in 2025;
    - Bristol is a surprising second;
    - Manchester lower than its size suggests.
- Movers into cities typically go to more deprived neighbourhoods than they left. Movers out typically gain. These gaps have shrunk over time. London is middle-ranking on this measure.

**Gentrified London (53 MSOAs)**
- Their combined share of London's in- and outflows has risen since the early 2000s, with a post-2008 lull.
- Inflows above the London neighbourhood average changed (3 areas in 2001 and 25 in 2025).
    - suggested drivers are procimity to business districts and transport, transient populations (e.g. students), regeneration changing housing stock.
- Trajectories have sharp post-2014 rises (Algate, Bromley-by-Bow West), slow strafy rises still below average (Grahame Park, Peckham Park Road), tracking the average (Leytonstone South West).
- Median inflow distance into gentrified London exceeds London overall, ~12.5 km on average for in-movers, ~10.1 km for out-movers.
    - London's own average ~102 km in, ~82 km out.
- Inflow distance patterns are non-linear. Some areas shift to longer-distance inflows at different times, others contract then stabilise.
- O-D deprivation gaps are larger for gentrified areas than for London overall, though they have attenuated over time.
- Classic sequence in some areas - early incomers ("pioneers") come from more deprived places and gain; later incomers come from less deprived places and take a relative "hit".

### What is the contribution?

- Showed the value of LCRs, something censuses cannot provide.
- Adds "move distance" and "O-D deprivation" as lenses on gentrification, beyond coutns of inflows and outflows.
- Empirically showed that "gentrified" areas are heterogeneous, with different **timings, intensities and incomer profiles**, supporting the view of gentrification as multiple pathways not a single process.
- Links residential mobility to social mobility via the escalator concept (but I have quite a bit confusion here ...)

## Discuss!

- They define gentrified areas first and then descirbe mobility; in my dissertation, I started from population change. Maybe the two approaches can validaye each other.
- The 114 km median inflow distance and the extra distance for gentrified areas, is a dimension my dissertation did not test. The claim that longer-distance incomers are causing local housing-market change needs further testing in future work.
- Only about half the gentrified areas have above-average inflows in 2025. My dissertation could examine both halves as potentially different mechanisms. This article only discusses about inflows.
- The idea that residents accumulate gains and then cash them in by moving on is a sequential, agent-level process. ABM could be a good tool to explore it.
- The article blends escalator effects, gentrification and displacement. I'd prefer them separated.
    - **regeneration: often a deliberate policy intervention;**
    - **gentrification: a process of class or social change, priginally defined by Ruth Glass in terms of displacement of working-class residents;**
    - **displacement: a specific outcome for incumbents.**

## What am I still confused about?

- The authors say neighbourhood change in London is an outcome of moves motivated by improving one's circumstances. How can this be inferred from descriptive aggregate data? Neighbourhood change could equally trigger the moves.
- What exactly is the "escalator effect" here? It seems to mean faster wealth accumulation for owner occupiers or landlords in improving neighbourhoods, and more loosely, improving personal economic and social circumstances. But this is measured through area IMD differences, not wealth, tenure or individual outcomes.
- Neighbourhoods themselved change over 25 years, as gentrified areas get less deprived. How does harmonised IMD handle this, andn is the comparison against the destination's deprivation at the time of the mover or a fixed edition?
- **How could one tell whether a neighbourhood is improving and attracting some people from wealthier areas without pushing original residents out vs. genuinely displacing people and becoming unaffordabl?** Outflow destinations and the deprivation of where leavers go should be analysed.
- For a gentrified area, **are both early and later arrivals all "gentrifiers"?** The aricle mentioned that arrivlas at different times have different living experiences.


## Based on the above, why was I encouraged to read this?

Move distance can be treated as an indicator of a neighbourhood's changing housing market and attractiveness.

For future directions, they could be,
- testing distance-based hypotheses;
- separating improvement from displacement using outflows;
- modelling the sequential escalator process.