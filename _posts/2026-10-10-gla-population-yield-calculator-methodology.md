---
title: "Summary: Greater London Authority — GLA Population Yield Calculator Methodology"
date: 2026-10-10
categories: [Methodology, Model Documentation]
tags: [Population-yield, Housing-development, Small-area population, gla, London]
---

## Full Reference

GLA Intelligence (2019) GLA Population Yield Calculator: Methodology. London: Greater London Authority. Originally published September 2014, updated June 2019. Available at: https://data.london.gov.uk/dataset/gla-population-yield-calculator-2k8nd (Accessed: 10 October 2026).

```bibtex
@techreport{gla2019yield,
  author      = {{GLA Intelligence}},
  title       = {GLA Population Yield Calculator: Methodology},
  institution = {Greater London Authority},
  address     = {London},
  year        = {2019},
  month       = jun,
  note        = {First published September 2014, updated June 2019.
                 Estimates to be cited as GLA Experimental Statistics},
  url         = {https://data.london.gov.uk/dataset/gla-population-yield-calculator-2k8nd}
}
```

## Questions 

### What is the article about?

It documents the GLA's Population Yield Calculator, an Excel tool that estimates how many people (and roughly what ages) will live in a new housing development once it is complete. The user enters the number of homes by bedrooms (1–4+) and tenure (market or social), chooses a geography (London Plan sub-region, PTAL band or a set of boroughs), and gets an estimated child and adult population.

The estimates come from 112 output areas (OAs) in London that were mostly covered by large developments completed between 2002 and 2011. Their 2011 Census populations are used as the "typical" occupancy of new-build homes.

### What kind of contribution is the paper trying to make?

Applied and methodological. It describes an empirical method for producing local, practical estimates, mainly to inform infrastructure planning and Section 106 / CIL negotiations.

### What gap(s) does it identify/tackle?

Boroughs were asking the GLA for better child-yield estimates. The two approaches in use were judged not reliable enough to apply across London:

- **Census commissioned tables** of housing characteristics, available only at local-authority level, either for everyone or for people who moved in the last 12 months. These describe the existing stock or recent movers, not new-build specifically.
- **Surveys of new housing**, which are costly, local and not comparable across London.

The gap is a **geographically specific, London-wide** estimate based on people actually living in new-build homes. No academic literature is reviewed.

### What is/are the main research questions(s)/argument(s)?

Implicitly: *given a development's mix of bedrooms and tenures and its location, how many children and adults should we expect to live there?*

Key assumptions:

- Past patterns will continue (the 2011 occupancy of 2002–11 new-build applies to future schemes).
- Population growth in a newly created OA is caused by the development in it.
- If a development covers 60%+ of an OA, the OA's population represents the development's residents.

It explicitly answers a gross question (who lives in the new homes), but it does not say how the development changes population in the wider area, and tells users to account for that themselves.

### How are they explored/presented?

Five steps:

1. **Find sites.** Filter the London Development Database (LDD) to schemes completed April 2002 – March 2011 with 50+ units.
2. **Match sites to OAs.** OAs are split when their population grows past the size limit, so new 2011 OAs mark places of concentrated growth. LDD sites are matched to new OAs, then only OAs at least 60% covered by a development are kept.
3. **Compute yields.** For each OA and each of the eight bedroom * tenure pairs, divide residents by households (e.g. 15 children in 27 one-bed market homes gives 0.481 children per home). Children are split into ages 0–9 and 10–18 using fixed proportions from the 112 OAs.
4. **Aggregate.** Pool OAs by sub-region, PTAL band (0–2, 3–4, 5–6) or borough, weighting by number of homes, to get more stable average rates.
5. **Build the tool.** Multiply the average rates by the homes the user enters.

The selection funnel:

| Stage | Count |
| --- | --- |
| LDD schemes completed Apr 2002 – Mar 2011 | 42,500 |
| ... with 50+ units | 1,018 sites |
| ... coinciding with a new 2011 OA | 267 sites (664 OAs) |
| ... OA at least 60% covered by the site | **112 OAs** |

### How are data used to test them?

**Data:**

- **LDD**: borough-submitted planning permissions and completion dates, covering everything from conversions to large schemes and estate renewal.
- **2011 Census**:
  - LC4103EW: bedrooms × tenure × dependent children (0–9, 10–18).
  - LC4405EW: households by tenure, size and bedrooms (the denominator).
  - CT0279: bedrooms × tenure for all residents, commissioned by the GLA. Adults are all residents minus children.
- **Tenure** has only two groups. "Market" combines owner-occupied, shared ownership and private rented; intermediate housing is put in market because the census places shared ownership with owner-occupation. "Social" covers council and housing association homes.

There is no formal validation, such as testing predicted yields against developments outside the sample.

**Limitations and possible biases:**

- **Age detail.** ONS refused 5-year age bands as disclosive, so outputs stop at 0–9, 10–18 and 19+. No school-age groups, no adult age structure.
- **Small, uneven samples.** 112 OAs, unevenly spread. For example, the North sub-region has 1 site for 1-bed social and 1 unit for 4-bed market. PTAL 5–6 in outer London has only 4 sites, so users are told to use PTAL 3–4 instead.
- **Selection.** Only large schemes (50+ units) that triggered an OA split are included. Schemes replacing a similar population (e.g. estate regeneration) or spread across OAs are likely missed, so the sample leans towards big schemes on previously empty or low-population land.
- **Mixed populations.** With a 60% coverage threshold, up to 40% of an OA may be older housing whose residents are counted as new-build residents.
- **Occupied homes only.** Rates are residents per *household*, so empty or second homes are excluded. Applied to all planned units, the tool may overstate yield where vacancy is high.
- **Dated.** One 2011 cross-section of 2002–11 schemes, assumed to hold in the future.
- **PTAL as context.** Users objected that PTAL varies across a site and is often disputed in negotiations. The GLA kept it (in condensed bands) as context rather than a definitive input.

### What are the main findings?

- Yields are expressed per home, by bedroom × tenure, and vary by sub-region and PTAL.
- The share of children aged 0–9 falls with home size and is lower in social than market housing:

| | 1 bed | 2 bed | 3 bed | 4 bed |
| --- | --- | --- | --- | --- |
| Market | 92% | 86% | 64% | 60% |
| Social | 78% | 78% | 53% | 41% |

- Sample sizes are thin for large homes and social 1-beds in several groupings.
- **Consultation (April 2014):** boroughs were broadly positive. They wanted school-age groups (not possible with census data), questioned PTAL (kept), and asked for bespoke aggregation (raw data and a borough selection tool were added).

### What is the contribution?

- The first London-wide, location-specific yield estimates based on residents of recent new-build, rather than borough averages or one-off surveys.
- A transparent, reusable method.
- **Using OA splits to locate new-build populations** in the census, a neat identification trick that relies on how OA boundaries are drawn.
- Practical value: widely used for infrastructure and S106/CIL negotiations.

## Discuss!

- **Gross vs Net** The tool estimates who lives in a development, not how much it adds to an area or to London. The document says it is not a projection tool and doesn't show wider impacts. *Could it be extended to do so, and how?* My current comparison of the same land in 2011 and 2021 is one route: 24,565 new homes but only +11,564 households in Lambeth and Wandsworth.
- **A 2021 refresh is feasible with my approach:**
  - EPC certificates count every new home, of any size or tenure, not only 50+ unit schemes.
  - The new-home share (homes built ÷ households) can be compared with their 60% site-coverage rule.
  - 2021 OA splits give a direct comparison with their identification method.
  - Two censuses allow before/after comparison, not only a single snapshot.
- **Tenure** Treating shared ownership and private renting as "market" hides real differences. In my results shared ownership rose to 9.3% of households in new-build areas, which argues for separate tenure groups.
- **Transport** PTAL enters only as a grouping. For TfL, outcomes such as car ownership, age and migration of residents, and finer accessibility measures, could make the tool much more useful.
<!-- - **Where people come from** Estimating origins (intra-London, other UK, abroad) would bring the tool closer to measuring additionality. -->
- **Age detail.** Check whether 2021 Census tables or custom datasets allow finer or school-age groups at OA level within disclosure rules.
- **Lockdown.** A 2021-based refresh would inherit census-day conditions (students and sharers away, fewer arrivals).

## What am I still confused about?

- The overview says developments built 2001–2011; site selection uses April 2002 – March 2011.
- Children are *dependent* children, and adults are everyone else aged 19+. Where do non-dependent 16–18-year-olds go?
- How many of the 267 sites end up in the 112 OAs, and were any OAs covered by more than one site?

## Based on the above, why was I encouraged to read this?

It is the GLA's existing answer to the first part of my research question: who lives in new housing, and how many. 

<!-- Ben Corr described it as out of date and not a GLA priority to rebuild, so there is a clear gap my PhD could fill. Adam suggested it as the starting point for the upcoming GLA/TfL meeting. -->

<!-- Its method (LDD sites matched to newly split OAs) is a close relative of my EPC + output-area approach. Its stated limits (gross not net, 2011 only, coarse ages and tenures, PTAL as a crude transport measure) map directly onto possible extensions: a 2021 refresh, additionality, origins of residents, and transport-relevant outcomes for TfL. -->
