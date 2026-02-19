# Paper Reading Questions

Answer these for each paper from "Articles for Beau.pdf". Not every question applies to every paper — skip what's irrelevant. Keep notes brief, a few sentences per question is fine.

## Core Questions (answer for every paper)

1. **What problem does this paper solve?** One sentence.
2. **What method do they use?** (GAN, Bayesian net, statistical, rule-based, learned model, survey/framework?)
3. **How is this relevant to my thesis?** Does it support my approach, is it an alternative I should discuss, or is it just background context?

## Interaction & Data Questions (for RS/simulation papers)

4. **How do they define an "interaction"?** (Just item+rating? Full tuple with action type, timestamp, context? Something else?)
5. **Do they generate sequential sessions or independent events?** (One-shot table of ratings vs ordered user sessions?)
6. **What data do they use?** (Which dataset, how many events, what action types?)
7. **Do they handle multiple action types** (view, cart, buy) **or just one** (e.g., ratings only)?

## Generation Method Questions (for papers that generate data)

8. **How do they handle discrete vs continuous outputs?** (Softmax over tokens? Continuous values? Gumbel-softmax trick? Something else?)
9. **How do they handle variable-length sequences?** (Fixed size? Padding? Stop token?)
10. **What conditioning do they use?** (Random noise only? User features? Temporal context? Previous interactions?)
11. **Do they mention training stability issues?** (Mode collapse, convergence problems, tricks needed?)

## Evaluation Questions (for papers that evaluate generated data)

12. **How do they evaluate the quality of generated data?** (Distributional metrics? Downstream task performance? Human inspection?)
13. **Do they test downstream utility?** (Train a model on synthetic data, evaluate on real data?)
14. **What baseline do they compare against?** (Real data? Other generation methods?)

## Positioning Questions (for surveys and frameworks)

15. **What taxonomy/categories do they propose?** (How do they organize the field?)
16. **What gaps or open problems do they identify?** (Anything that aligns with what we're doing?)
17. **Do they mention transformers/autoregressive models?** (If not, that's noteworthy — it's our gap.)

---

## Paper Priority Guide

Read in roughly this order. Tier 1 papers shape your research direction. Tier 2 fills in the alternatives discussion. Tier 3 is background you cite but don't deep-dive.

### Tier 1 — Read carefully, these frame your work
- [25] Stavinova (2022) — Survey on synthetic data simulators for RS
- [24] McInerney — Accordion trainable simulator
- [27] UserSim — GAN-based user simulation
- [3] Bobadilla (2023) — GAN for synthetic RS datasets
- [18] Jakomin (2018) — Generating data streams for RS
- [13] DataGenCARS (2017) — Synthetic data generator for context-aware RS
- [6] Chaney (2021) — RS simulation challenges

### Tier 2 — Read for breadth, cite in review
- [4] SIREN (2019) — Simulation framework for RS
- [22] T-RECS (2021) — Simulation tool for RS
- [14] SimuRec workshop (2021)
- [5] Chaudhuri (2021) — Modeling user behaviour
- [7] Chen (2021) — Adversarial reward learning for behavior
- [1] Abufadda (2021) — Survey synthetic data for ML
- [19] Jordon (2022) — Synthetic data what/why/how
- [21] Lu (2024) — ML for synthetic data generation review
- [16] Figueira (2022) — Survey synthetic data + evaluation + GANs
- [26] Xu (2018) — Tabular data with GANs

### Tier 3 — Skim, cite if relevant
- [11] Creswell (2018) — GAN overview
- [15] Emam (2020) — Practical synthetic data generation (book)
- [2] Achuthan (2022) — Synthetic biological data
- [8] Choi (2018) — Patient records with GANs
- [9] Chokwitthaya (2020) — GMM synthetic data
- [12] De Benedetti (2020) — Healthcare data with Bayesian nets
- [17] Hernandez (2022) — Tabular health records
- [20] Kaur (2021) — Bayesian nets for health data
- [23] Martins (2024) — Synthetic data via Bayesian nets
