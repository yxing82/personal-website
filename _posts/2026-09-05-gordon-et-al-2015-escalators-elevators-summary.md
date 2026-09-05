---
title: "Summary: Gordon et al. (2015) - Urban Escalators and Interregional Elevators"
date: 2026-09-05
categories: [Literature Notes, Population Geography]
tags: [escalator effect, elevator effect, occupational mobility, migration, agglomeration, city-region, labour market, England and Wales]
---

## Full Reference

Gordon, I., Champion, T. and Coombes, M. (2015) 'Urban escalators and interregional elevators: the difference that location, mobility, and sectoral specialisation make to occupational progression', *Environment and Planning A*, 47(3), pp. 588–606. https://doi.org/10.1068/a130125p

```bibtex
@article{gordon2015urban,
  title   = {Urban escalators and interregional elevators: the difference that location, mobility, and sectoral specialisation make to occupational progression},
  author  = {Gordon, Ian and Champion, Tony and Coombes, Mike},
  journal = {Environment and Planning A},
  volume  = {47},
  number  = {3},
  pages   = {588--606},
  year    = {2015},
  doi     = {10.1068/a130125p}
}
```

## Questions

### What is the article about?

This paper examines how **where people live** and **whether they move between city-regions** independently affect occupational advancement in England and Wales, using ONS Longitudinal Study data linking the 1991 and 2001 Censuses. It distinguishes two spatial effects on job-status (JS) progression,
- **Escalator effect**: the continuing effect of residing in a dynamic city-region, operating through opportunities for accumulating human and social capital.
- **Elevator effect**: a one-off occupational effect associated with moving between city-regions. Its direction depends on differences between the origin and destination labour markets, where moving from a slacker to a tighter labour market can produce an upward elevator effect.

The paper also examines **sector of employment**, which proves substantially more important for occupational progression than either spatial effect.

### What kind of contribution is the paper trying to make?

- **Conceptually**: it makes a sharp distinction between continuing, residence-based **escalator effects** and one-off, migration-based **elevator effects**, which earlier population-geography work had not clearly separated.

- **Empirically**: it updates Fielding's escalator evidence to 1991-2001, examines occupational progression across the full job-status distribution, extends the analysis across English and Welsh city-regions, and tests whether escalators are specific to London and South-East England or a more general urban phenomenon.

### What gaps does it identify?

1. Population geographers had not clearly distinguished **occupational gains produced by relocation** from **continuing gains associated with residence** in an advantageous labour market.

2. Spatial economists had made a similar distinction between one-off productivity effects and cumulative learning effects, but generally treated migration as a means of identifying spatial effects, not as a central geographical process.

3. Fielding's original escalator model left 2 important ambiguities:
    - **Is the escalator fundamentally a South East regional or cultural phenomenon, or an urban or economic phenomenon associated with agglomeration?**
    - **How important is geographic mobility itself, compared with simply residing in an advantageous city-region?**

4. The role of sector of employment and the types of jobs available locally had received relatively little attention.

### What are the main research arguments?

Three hypotheses are tested:

1. Occupational advancement is affected by both **location** and **relocation**, but the escalator and elevator operate through different mechanisms and geographies.

2. Elevator effects should primarily reflect differences in **labour-market tightness** between origin and destination, whereas escalator effects should reflect **agglomeration**, advanced occupational structures, and concentrations of dynamic and knowledge-intensice employment.

3. The benefits of both escalator and elevator effects should be unevenly distributed, particularly favouring **younger people** and individuals with personal attribtues conducive to occupational advancement.

### How are they explored?

The paper uses a three-stage regression strategy.

- **Stage 1**: estimate area-specific **escalator**, **elevator**, and sectoral effects from individual-level regression of JS change.

- **Stage 2**: regress the estimated city-region effects on characteristics such as unemployment, agglomeration, occupational structure and industrial mix to identify the process associated with each effect.

- **Stage 3**: examine interactions with observable characteristics such as age and qualifications, and use quantile regression to investigate whether the strength of spatial effects varies with unobserved personal attributes associated with occupational progression.

Operatioanlising escalator and elevator effects differently to separate continuing exposure to a place from the one-off effect associated with changing location:

| Effect | Semi-dummy |
|---|---|
| **Escalator** | 1 if resident in the CR at both censuses; 0.5 if resident at one census; 0 if absent at both |
| **Elevator** | −1 for moving out of the CR; +1 for moving into it; 0 otherwise |

### How are data used to test them?

- Source: ONS Longitudinal Study for England and Wales, linking individual records from the 1991 and 2001 Censuses.

- Sample: ~145,000 working-age individuals who were in employment and out of education in 1991 and of working age at both censuses.

- Outcome: change in a job-status based on the logged earnings associated with SOC90 three-digit occupations.

- Geography: 38 CURD city-regions, supplemented by 20 consolodated city-regions.

> Limitations include
>
> - job-status does not capture managerial or supervisory responsibility within occupations.
> - Qualitative personal characteristics such as ambition, motivation and connectedness are not directly observed. Quantile regression tests whether contextual effects vary systematically with unobserved characteristics associated with stronger or weaker occupational progression, but it doesn't directly measure ambition.
> - The sample design focuses on occupational progression among people remaining within the observable working-age labour force.
{: .prompt-tip }

### What are the main findings?

#### Escalator effect

- Escalator effects are associated primarily with urban agglomeration, not being unique to London or South East England.

- Comparable locational advantages can occur in second- and third-order city-regions, including places such as Manchester and Leeds.

- Escalator strength is associated with the concentration of high-level occupations, dynamic knowledge-intensive sectors and advanced job opportunities.

- The effect operates across the working-age range, but is much stronger for younger workers. The estimated effect for those under 25 is around 3-4 times that for worker over 40.

- Quantile regression suggest that escalator benefits are also stronger among individuals with favourable unobserved characteristics associated with occupational advancement. Effects increase through the distribution until roughly the 65th percentile and then flatten.

#### Elevator effect

- Elevator effects are primarily associated with differences in labour-market tightness.

- Occupational gains occur when migrants move from areas where labour demand is relatively weak to areas with tighter labour markets, where their existing human capital can be used more productively.

- Unlike escalators, elevator effects show a stronger regional pattern, not an agglomeration pattern.

- Significant positive elevator gains are concentrated particularly narrowly among people aged 20-24.

- Skill stocks, industrial mix and agglomeration do not significantly explain the elevator effect once labour-market tightness is considered.

#### Sectoral effect

- Sector of employment is the strongest influence examined.

- The standard deviation of sectoral effects is around 8%, compared with roughtly 2% for escalator and elevator effects.

- Finance and IT show particularly strong occupational gains, whereas retail, land transport, hotels and catering show weaker or negative progression.

- Knowledge-intensive and expanding sectors appear to provide stronger opportunities for on-the-job learning and human-capital accumulation.

#### Escalator vs. Elevator

- Elevator: relocation --> chaning utilisation of existing human capital --> labour-market tightness;

- Escalator: residence over time --> accumulation of human or social capital --> agglomeration and opportunity structure.

Across the 38 city-regions, escalator and elevator coefficients are largely uncorrelated, despite some individually significant positive cases occurring in the Greater South East. Their broader spatial patterns and explanatory mechanisms are different.

## What is the contribution?

1. Distinguishing "being somehwere" as escalator effects from "moving somewhere" as elevator effects. This prevents the occupational advantage experienced by migrants to successful regions from automatically being interpreted as evidence of an escalator effect.

2. Interpreting the escalator as an urban-economic effect associated with agglomeration and opportunity structure. London may habe a particularly strong concentration of relevant opportunities, but it does not monopolise the escalator process.

3. What matters is not simply the concentration of highly educated or talented workers. Occupational advancement depends strongly on the avaliability of jobs that permit learning, capability development and access to productive networks.

4. Being in a favourable city-region matters, but what kind of work someone is doing within that city-region may matter substantially more.

5. Spatial effects are heterogeneous. Neither escalators nor elevators affect everybody equally.

## Discuss!

### 1. Conceptual distinction between escalator and elevator

Precisely, 
- Elevator = effect of the act and direction of moving
- escalator = continuing effect of exposure to a particular urban labour-market environment

The ket contrast is not "migrant vs. non-migrant", but "relocation vs. residence". A migrant can experience both effects, an immediate elevator effect when moving and a continuing escalator effect while subsequently residing in the destination. An established resident can experience the escalator without ever experiencing an elevator.

### 2. Elevator as utilisation, Escalator as accumulation

- Elevator ---> utilisation effect: existing capabilities obtain a better occupational return after moving into a tighter labour market.

- Escalator ---> accumulation effect: capabilities and networks develop progressively through exposure to particular jobs and urban environments.

### 3. The welfare question

The paper raises an important question:

    Do escalator regions actually create additional human capital and productive capacity, or do they primarily redistribute occupational opportunities towards people able to access particular places?

The authors lean towards the former interpretation, arguing that agglomeration provide genuine learning and capability-building opportunities. But distinguishing national human-capital creation from spatial redistribution of opportunity remains important for evaluating the wider welfare implications of escalator regions.

### 4. Sector effects may complicate the meaning of regions

Sectoral effects are substantially larger than the estimated geographical effects. Knowledge-intensive and advanced activities are spatially concentrated.

So, **Does place independently generate an escalator, or does place matter partly because particular kinds of jobs are concentrated there?**

### 5. Implication for "stepping off"

The distinction between escalators and elevators also changes how I think about return migration and Fielding's idea of "stepping off" the escalator. 

Someone moving into an escalator region may experience "elevator into the region --> time on the escalator --> another spatial move later". The later move is not necessarily just a passive "exit" after accumulated escalator gains. It may itself generate another elevator effect, depending on the labour-market relationship between origin and destination.

This makes me feel again that career could potentially involve **sequences of elevator and escalator effects**, not one simple movement onto and then off a single escalator. This is not directly tested in this paper, but we can definitely reconsider return migration and career mobility.

## What am I still confused about?

1. The few individually significant positive elevator and escalator coefficients occur in leading Greater South East city-regions, yet the two sets of coefficients are largely uncorrelated overall. How should this combination of local overlap and differentn national spatial structures be interpreted?

2. Because the analysis focuses on people observable within the working-age labour market, how might selection affect estimates of escalator and elevator processse? Could particularly unsuccessful trajectories disappear from the occupational-progression analysis?

3. The authors interpret stronger spatial coefficients higher in the JS-change distribution as evidence consistent with favourable unobserved attributes such as "dynamic human capital". How strongly can these quantiles actually be interpreted in terms of ambition or motivation, not other measured characterisitcs?

4. How much of the escalator effect comes from agglomeration itself, and how much comes from the fact that advanced, knowledge-intensive jobs are concentrated in large city-regions?

## Based on the above, why was I encouraged to read this?

This paper provides the clearest formal definition of the escalator and elevator distinction. It also directly connects to Fielding's foundational work, establishing what is confirmed, what is revised, and what remains open. The finding that the escalator is an agglomeration pehnomenon, not a London-South East cultural one is particularly important for comparative work outside that region.