# Tier 1 Literature Review

This file covers Tier 1 papers from `paper_reading_questions.md` in the required reading order. Each paper uses the full Q1-Q17 template; non-applicable items are marked `N/A`.

## 1) Synthetic Data-Based Simulators for Recommender Systems: A Survey (Stavinova et al., 2022)

### Availability
Full PDF available locally (`Synthetic Data-Based Simulators for Recommender Systems_ A Survey.pdf`).

### Q1. What problem does this paper solve?
It systematizes a fragmented simulator literature by proposing a consistent way to compare and reason about RS simulators. (Abstract; Section 2)

### Q2. What method do they use?
Survey + framework paper: a structured review with a new classification based on simulator functionality, reproducibility, and industrial effectiveness. (Abstract; Section 2.2)

### Q3. How is this relevant to my thesis?
It is a direct framing paper for interaction simulation design choices, simulator quality control, and simulation-to-reality gaps.

### Q4. How do they define an "interaction"?
At survey level, interactions are user-item responses in RS loops (recommendations -> user responses -> updated training data), sometimes including visits, slates, and delayed effects. (Section 2.3; Section 4.4.4)

### Q5. Do they generate sequential sessions or independent events?
They report that sequential feedback loops are the dominant modeled real-world effect across simulators, though simulator implementations vary. (Section 4.4.4)

### Q6. What data do they use?
They synthesize evidence across many simulators and datasets (open and private), including large interaction/session logs; the paper itself is not a single-dataset experiment. (Section 3; Appendix tables discussion)

### Q7. Do they handle multiple action types or just one?
Across surveyed simulators, both exist: some model only narrow feedback signals, others include richer signals (e.g., visits, clicks/positive outcomes, context/slate effects).

### Q8. How do they handle discrete vs continuous outputs?
No single mechanism: surveyed methods include statistical generators, GAN-like generators, response models, and parametric functions, each with its own output treatment. (Section 4 variants)

### Q9. How do they handle variable-length sequences?
Varies by simulator; the survey notes methods that model sequential dynamics and recurring visits, including variable-sized trajectory generation in some systems. (Section 4.4.4)

### Q10. What conditioning do they use?
Conditioning commonly includes user/item profiles, historical interactions, scenario parameters, context/slates, and assumptions about biases/drift. (Section 2.3; Section 4)

### Q11. Do they mention training stability issues?
Yes at a system level: they emphasize simulator complexity/tuning difficulty and lack of systematic quality-control methodology; they do not center on one GAN-specific stability story. (Section 4.4.4; Conclusions open problems)

### Q12. How do they evaluate the quality of generated data?
By simulation quality components and consistency checks: real-vs-sim behavior/metric alignment, bias analysis, and task-level RS outcomes. (Sections 2.3 C4; 4.4)

### Q13. Do they test downstream utility?
Yes, as a survey theme: simulators are used for RS training/testing, offline what-if analysis, and policy evaluation before online deployment.

### Q14. What baseline do they compare against?
The survey highlights heterogeneous baselines and explicitly points out missing standardized head-to-head comparisons under matched settings. (Conclusions open problems)

### Q15. What taxonomy/categories do they propose?
Core taxonomy: C1 synthetic data generation, C2 scenario modeling, C3 RS training/testing, C4 simulation quality control, C5 experiment summarization; plus comparison axes: functionality, approbation, industry effectiveness. (Section 2.2-2.3)

### Q16. What gaps or open problems do they identify?
Key gaps: inconsistent real-vs-synthetic RS comparison outcomes, weak universal simulator-quality methodology, scarce controlled cross-simulator benchmarks, and reproducibility deficits. (Conclusions)

### Q17. Do they mention transformers/autoregressive models?
Transformers are not a central axis in this survey; the emphasis is broader simulator architecture/components and existing mostly pre-transformer simulator patterns.

## 2) Accordion: A Trainable Simulator for Long-Term Interactive Systems (McInerney et al., 2021)

### Availability
Full PDF available locally (`Accordion: A Trainable Simulator for Long-Term Interactive Systems.pdf`).

### Q1. What problem does this paper solve?
It addresses offline evaluation limitations by simulating long-term interactive dynamics, including how recommendation quality changes future user visits and dataset size. (Abstract; Introduction)

### Q2. What method do they use?
A trainable continuous-time simulator based on inhomogeneous Poisson processes with marked events for item and response generation. (Section 3)

### Q3. How is this relevant to my thesis?
Highly relevant: it is a strong alternative to plain sequence models for interaction simulation because it explicitly models arrival/visit dynamics and feedback loops.

### Q4. How do they define an "interaction"?
An event is essentially `(time, user, item, outcome)`; events are grouped into visits, and outcomes include positive interactions/streams under recommendation exposure. (Section 3.1)

### Q5. Do they generate sequential sessions or independent events?
Sequential, continuous-time trajectories with history-dependent intensity and state updates; explicitly long-term and non-i.i.d. (Section 3; Figure/algorithm discussion)

### Q6. What data do they use?
Public ContentWise impressions data (127,904,252 impressions; 15,983 users; 2,211 items; 98 days) and a private randomized A/B dataset subset (11,525 users; 1,723 items; 28 days). (Section 4.1 datasets)

### Q7. Do they handle multiple action types or just one?
They model multiple event aspects (visits, impressions, item interaction outcomes), not just a single static rating.

### Q8. How do they handle discrete vs continuous outputs?
Time is continuous via Poisson intensity; item and reward marks are sampled from softmax-based discrete distributions. (Section 3.1)

### Q9. How do they handle variable-length sequences?
By construction: number of visits/events is random (Poisson/thinning), and interactions per visit can vary. (Algorithm 1; simulation section)

### Q10. What conditioning do they use?
Intensity is conditioned on global time effects, user state/history features, and Hawkes-style influence from prior positive interactions; marking models also condition on history. (Section 3.1)

### Q11. Do they mention training stability issues?
They discuss approximation tradeoffs and artifacts (e.g., underdispersion from Poisson assumptions), and propose scalable objectives to make training feasible. (Sections 3.2, 4)

### Q12. How do they evaluate the quality of generated data?
Through intensity-fit checks, held-out policy/hyperparameter prediction tasks, and A/B-test outcome prediction quality on real experimental data. (Section 4)

### Q13. Do they test downstream utility?
Yes: simulator-guided exploration tuning and offline prediction of policy changes before online testing. (Sections 4.2-4.3)

### Q14. What baseline do they compare against?
They compare against non-adaptive/invariant-visit simulation variants and a strong debiasing baseline (Norm-IPS), plus objective approximations. (Section 4)

### Q15. What taxonomy/categories do they propose?
`N/A` - this is a method paper, not a taxonomy/survey paper.

### Q16. What gaps or open problems do they identify?
Main limitations include restrictive Poisson assumptions (underdispersion), model-induced bias, and need for richer visit/intensity structure.

### Q17. Do they mention transformers/autoregressive models?
They briefly reference autoregressive click-behavior modeling contextually, but their own simulator is Poisson-process based, not transformer-based. (Section 3.1)

## 3) UserSim: User Simulation via Supervised Generative Adversarial Network (Zhao et al., 2021)

### Availability
Full PDF available locally (`UserSim: User Simulation via Supervised Generative\nAdversarial Network.pdf`).

### Q1. What problem does this paper solve?
It aims to pre-train/evaluate RL recommenders offline by simulating user behavior when online A/B training is costly and risky. (Abstract; Introduction)

### Q2. What method do they use?
A supervised GAN user simulator: GRU-based generator + discriminator with unsupervised real/fake and supervised feedback-class prediction objectives. (Section 2)

### Q3. How is this relevant to my thesis?
Directly relevant to your interaction-simulator question because it targets sequential RS user behavior under limited per-user logs.

### Q4. How do they define an "interaction"?
As MDP tuples `(state, action, reward)` where state is a sequence of browsed items+feedback, action is recommended item(s), reward is feedback type. (Section 2.1)

### Q5. Do they generate sequential sessions or independent events?
Sequential sessions: they extract ordered tuples from each user session and model transitions from state to next action/feedback.

### Q6. What data do they use?
Public JD.com dataset with 283,228 user sessions, 1,355,255 items, 97,713,660 interactions, average session length 345; click=positive, skip=negative. (Table 1; Section 3.1)

### Q7. Do they handle multiple action types or just one?
In experiments they use binary feedback types (positive/negative), while noting extension to more behavior classes is possible.

### Q8. How do they handle discrete vs continuous outputs?
Items/feedback are embedded into continuous vectors; generator outputs item-embedding-like actions; discriminator predicts discrete real/fake x feedback classes via softmax logits.

### Q9. How do they handle variable-length sequences?
They use a fixed history window (`N=20`) as state, so variable-length sessions are converted into fixed-length state-action-reward slices. (Section 3.1)

### Q10. What conditioning do they use?
Generator/discriminator condition on user history (items + feedback), with adversarial and supervised losses shaping generated actions and behavior prediction.

### Q11. Do they mention training stability issues?
They use pretraining and alternating updates for GAN training, but do not foreground classic mode-collapse analysis as a major result.

### Q12. How do they evaluate the quality of generated data?
Using behavior-prediction metrics (F1, AUC), generator sequence-similarity metrics (ROUGE), ablations, and sensitivity analysis. (Section 3)

### Q13. Do they test downstream utility?
Yes: they train DQN recommenders on simulator-generated interactions and compare convergence/reward behavior against offline-log and baseline-simulator setups. (Section 3.3)

### Q14. What baseline do they compare against?
LR, UserSim-d, RecSim, RecoGym, Virtual-Taobao, GAN-PW, IRecGAN; plus generator-side comparisons to FM, W&D, Autorec, GRU4Rec, RRN, IRGAN, SSRM. (Section 3)

### Q15. What taxonomy/categories do they propose?
`N/A` - method paper, no field taxonomy.

### Q16. What gaps or open problems do they identify?
Remaining limitations include simplified behavior labels, dependence on offline logs, and fixed-window state design for long-horizon realism.

### Q17. Do they mention transformers/autoregressive models?
No transformer method is proposed; sequence modeling is GRU/RNN-centric.

## 4) Creating synthetic datasets for collaborative filtering recommender systems using GANs (Bobadilla et al., 2023)

### Availability
Full PDF available locally (`Creating synthetic datasets for collaborative filtering recommender systems.pdf`).

### Q1. What problem does this paper solve?
It generates parameterized synthetic collaborative-filtering datasets where users/items/sample count/variability can be controlled. (Abstract; Introduction)

### Q2. What method do they use?
GANRS: DeepMF embedding extraction + GAN generation in dense space + clustering-based conversion back to sparse discrete CF tuples. (Section 3)

### Q3. How is this relevant to my thesis?
It is relevant as a synthetic data generation baseline/alternative, especially for controlled benchmark construction, though it is less focused on dynamic interaction simulation.

### Q4. How do they define an "interaction"?
A CF tuple `<user, item, rating>` (explicit rating), with no mandatory temporal or session context in the core formulation.

### Q5. Do they generate sequential sessions or independent events?
Independent tabular rating events; not session-sequence generation.

### Q6. What data do they use?
Movielens 100K (943 users, 1,682 items, 99,831 ratings), Netflix* (23,012 users, 1,750 items, 535,421 ratings), MyAnimeList (19,179 users, 2,692 items, 548,967 ratings). (Table 2)

### Q7. Do they handle multiple action types or just one?
Primarily one signal: ratings.

### Q8. How do they handle discrete vs continuous outputs?
GAN works in continuous dense embedding space; generated ratings are continuous then clipped/rounded to discrete rating scales; generated dense user/item vectors are discretized via K-means cluster assignment. (Section 3)

### Q9. How do they handle variable-length sequences?
`N/A` - not a sequential/session model.

### Q10. What conditioning do they use?
Random Gaussian noise plus learned user/item embedding structure from source data; user-specified parameters control output users/items/samples and variability (`std`).

### Q11. Do they mention training stability issues?
They discuss GAN instability/mode-collapse in related work context, but their paper focuses more on architecture design and empirical behavior than deep stability diagnostics.

### Q12. How do they evaluate the quality of generated data?
Distributional alignment checks (user/item/rating behavior), duplicate analysis, and downstream RS quality trends (MAE, accuracy, precision, recall, F1) against source-data trends. (Section 4)

### Q13. Do they test downstream utility?
Yes: recommendation/prediction behavior on synthetic datasets is tested with DeepMF and compared to source dataset trends.

### Q14. What baseline do they compare against?
Primary reference is the original real datasets and expected metric/distribution trends; prior tools (e.g., SynEvaRec/CTGAN-related) are discussed but not used as a single standardized direct benchmark in the core experiments.

### Q15. What taxonomy/categories do they propose?
`N/A` - method paper, no taxonomy proposal.

### Q16. What gaps or open problems do they identify?
They highlight that parameterized synthetic CF dataset generation was underdeveloped, and show tradeoffs (e.g., duplicate handling, precision-recall behavior) that still need careful tuning.

### Q17. Do they mention transformers/autoregressive models?
No transformer-centric method; discussion is GAN/CF embedding focused with some RNN/LSTM references in related work.

## 5) Generating inter-dependent data streams for recommender systems (Jakomin et al., 2018)

### Availability
Only an abstract/introduction/snippet `.md` source is available locally (`Generating inter-dependent data streams for recommender systems.md`). Full text appears access-restricted.

### Q1. What problem does this paper solve?
It tackles scarce and insufficiently diverse RS datasets by generating multiple inter-dependent temporal data streams for evaluation.

### Q2. What method do they use?
GIDS: a synthetic stream generator that builds clustered relational structures with timestamps and configurable concept drift.

### Q3. How is this relevant to my thesis?
Very relevant: it targets synthetic interaction streams (not just static ratings) for incremental/time-aware recommender evaluation.

### Q4. How do they define an "interaction"?
Limited evidence: interactions are represented as timestamped relational tuples, with baseline random quadruplets `{user, item, rating, timestamp}` explicitly mentioned.

### Q5. Do they generate sequential sessions or independent events?
Sequential streams (time-changing data) are a core design goal, though exact session mechanics are not fully visible in the available snippet.

### Q6. What data do they use?
Limited evidence: they generate multiple synthetic datasets/streams and compare against real datasets using static/dynamic recommenders and data fusion algorithms; specific dataset names/sizes are not visible.

### Q7. Do they handle multiple action types or just one?
Limited evidence suggests a primary rating-style interaction signal rather than rich multi-action event taxonomies.

### Q8. How do they handle discrete vs continuous outputs?
Limited evidence: ratings appear discrete and time is timestamp-based; exact output parameterization details are not available.

### Q9. How do they handle variable-length sequences?
Likely stream-length variability exists, but this is not explicitly documented in the accessible text.

### Q10. What conditioning do they use?
They condition generation on inter-entity cluster structure, cross-dataset dependencies, distributional targets, time dynamics, and drift parameters.

### Q11. Do they mention training stability issues?
No explicit model-training stability discussion is visible in the available abstract/snippet text.

### Q12. How do they evaluate the quality of generated data?
They report statistical similarity to real data and recommender/data-fusion performance comparability.

### Q13. Do they test downstream utility?
Yes, via recommender and data-fusion algorithm evaluation on generated streams.

### Q14. What baseline do they compare against?
A random synthetic generator baseline is explicitly mentioned in the available snippet.

### Q15. What taxonomy/categories do they propose?
`N/A` - no taxonomy proposal is visible from available text.

### Q16. What gaps or open problems do they identify?
Main motivation/gap is lack of publicly available, diverse, interconnected temporal RS data for robust incremental evaluation.

### Q17. Do they mention transformers/autoregressive models?
No such mention is visible in the available abstract/snippet text.

## 6) DataGenCARS: A generator of synthetic data for the evaluation of context-aware recommendation systems (del Carmen et al., 2017)

### Availability
Only an abstract/introduction/snippet `.md` source is available locally (`DataGenCARS: A generator of synthetic data for the evaluation of context-aware recommendation systems.md`). Full text appears access-restricted.

### Q1. What problem does this paper solve?
It addresses the lack of suitable context-rich datasets for evaluating context-aware recommender systems (CARS).

### Q2. What method do they use?
A Java-based configurable synthetic dataset generator supporting user/item/context schema definition, realistic rating generation, and real+synthetic mixing.

### Q3. How is this relevant to my thesis?
Directly relevant for interaction-definition design because it formalizes context as part of the generated recommendation data.

### Q4. How do they define an "interaction"?
Limited evidence: user-item ratings/events are generated jointly with contextual attributes (context dimensions tied to recommendations).

### Q5. Do they generate sequential sessions or independent events?
Limited evidence indicates primarily configurable dataset generation (tabular/contextual), not clearly session-sequence simulation.

### Q6. What data do they use?
Limited evidence: the tool can build datasets from scratch, mimic existing datasets, and run experiments with fully synthetic and realism-oriented settings; specific event counts are not visible.

### Q7. Do they handle multiple action types or just one?
Limited evidence points to primarily rating-oriented signals with context attributes, not a broad multi-action event stream.

### Q8. How do they handle discrete vs continuous outputs?
Insufficient detail in available text; it describes realistic ratings/attributes generation but not exact numeric-output mechanisms.

### Q9. How do they handle variable-length sequences?
`N/A` or unclear from available text; sequence/session mechanics are not described in the abstract snippet.

### Q10. What conditioning do they use?
Generation is conditioned on user schemas/profiles, item types/attributes, and context types via configurable input files.

### Q11. Do they mention training stability issues?
No explicit training-stability discussion is visible in accessible text.

### Q12. How do they evaluate the quality of generated data?
They report experimental evidence for usefulness in evaluating recommendation algorithms, including completely synthetic and realistic-mimic scenarios.

### Q13. Do they test downstream utility?
Yes, in the sense that generated datasets are used to evaluate recommendation algorithms.

### Q14. What baseline do they compare against?
Limited evidence: comparisons include use of existing datasets and generated variants; specific baseline method details are not visible.

### Q15. What taxonomy/categories do they propose?
`N/A` - no taxonomy is provided in available text.

### Q16. What gaps or open problems do they identify?
They emphasize the continuing dataset scarcity/incompleteness problem for CARS and the need for flexible scenario generation.

### Q17. Do they mention transformers/autoregressive models?
No such mention is visible in available text.

## 7) Recommendation System Simulations: A Discussion of Two Key Challenges (Chaney, 2021)

### Availability
Full PDF available locally (`Recommendation System Simulations_ A Discussion of Two Key Challenges.pdf`).

### Q1. What problem does this paper solve?
It clarifies two foundational simulation design problems: user choice modeling and modeling non-recommendation exposure channels.

### Q2. What method do they use?
Position/discussion paper: conceptual review of existing assumptions plus proposed alternatives grounded in consumer-choice literature.

### Q3. How is this relevant to my thesis?
It is highly relevant for defining interaction assumptions in your simulator so claims remain realistic and interpretable.

### Q4. How do they define an "interaction"?
As repeated user choice/engagement decisions over items, where utility-driven selection can occur from recommended and alternative sources. (Sections 2-3)

### Q5. Do they generate sequential sessions or independent events?
Conceptually sequential/repeated choice instances over time, but this paper itself does not implement a concrete simulator.

### Q6. What data do they use?
No new empirical dataset is introduced; it synthesizes assumptions from prior work and cites observational evidence (e.g., alternative-access effects).

### Q7. Do they handle multiple action types or just one?
At conceptual level, they focus on choice/selection behavior and source selection rather than detailed multi-action event ontologies.

### Q8. How do they handle discrete vs continuous outputs?
`N/A` - no generative model implementation with explicit output layer design.

### Q9. How do they handle variable-length sequences?
`N/A` - no concrete simulator implementation is provided.

### Q10. What conditioning do they use?
Conceptual conditioning variables include item attributes, user utility weights, randomness, aspiration thresholds, search/decision costs, and source-selection mechanisms.

### Q11. Do they mention training stability issues?
`N/A` - not a trainable model paper.

### Q12. How do they evaluate the quality of generated data?
No direct generated-data evaluation; emphasis is on assumption quality, realism, and replicability of simulation design choices.

### Q13. Do they test downstream utility?
`N/A` - no downstream empirical training/evaluation experiments are run in this position paper.

### Q14. What baseline do they compare against?
`N/A` - no experimental benchmark table; they discuss alternative assumptions conceptually.

### Q15. What taxonomy/categories do they propose?
They organize the field around two key challenge categories and review families of consumer-choice models (e.g., multinomial logit/probit, satisficing, consideration-set frameworks).

### Q16. What gaps or open problems do they identify?
Need for explicit/standardized user-choice assumptions, realistic non-recommendation exposure modeling, realistic policy comparisons, and scale standards for convincing simulations.

### Q17. Do they mention transformers/autoregressive models?
No transformer/autoregressive modeling focus; the paper is primarily economic/behavioral modeling guidance.

