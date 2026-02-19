# Tier 2 Literature Review

This file covers Tier 2 papers from `paper_reading_questions.md` in the required order. Each paper uses the full Q1-Q17 template; non-applicable items are marked `N/A`.

## 1) SIREN: A Simulation Framework for Understanding the Effects of Recommender Systems in Online News Environments (Bountouridis et al., 2019)

### Availability
Full PDF available locally (`SIREN: A Simulation Framework for Understanding the Eﬀects\nof Recommender Systems in Online News Environments.pdf`).

### Q1. What problem does this paper solve?
It provides a simulation framework to help news content providers analyze long-term recommender effects (e.g., filter-bubble and Matthew-effect concerns) before deployment.

### Q2. What method do they use?
An empirical-data-informed simulation framework (SIREN) with explicit models for articles, users, recommendation salience, editorial priming, and user preference drift.

### Q3. How is this relevant to my thesis?
Highly relevant as an RS simulation alternative focused on interaction dynamics and societal outcomes, not just static offline metrics.

### Q4. How do they define an "interaction"?
Interaction is modeled as users choosing and reading articles from an awareness pool each news-cycle iteration, with awareness influenced by search/proximity, editorial prominence, and recommendations.

### Q5. Do they generate sequential sessions or independent events?
Sequential: simulation runs over repeated iterations (news cycles), with evolving user preferences and changing article prominence.

### Q6. What data do they use?
They build the topic space using a BBC dataset of 2,225 articles and then run case-study simulations (default settings include 200 active users, 30 iterations, and 100 new articles per iteration).

### Q7. Do they handle multiple action types or just one?
Primarily one action type (article read/selection), though recommendation exposure and editorial priming are separate mechanisms affecting that choice.

### Q8. How do they handle discrete vs continuous outputs?
Continuous variables model distances, prominence, and probabilities in topic space; discrete outcomes are article reads/selections and ranked recommendation positions.

### Q9. How do they handle variable-length sequences?
Per-user session size is variable (sampled per iteration), while the system itself is long-horizon iterative over fixed simulation timesteps.

### Q10. What conditioning do they use?
User choice is conditioned on user/article distance, prominence, awareness weighting (`λ`), recommendation salience (`δ`, rank decay `β`), and user-drift sensitivity.

### Q11. Do they mention training stability issues?
`N/A` for GAN-style training stability; this is a simulation/behavior-model paper rather than adversarial model training.

### Q12. How do they evaluate the quality of generated data?
They evaluate recommender effects via diversity trajectories over time, using EPC (long-tail novelty) and EPD (unexpectedness) metrics, including drift vs non-drift comparisons.

### Q13. Do they test downstream utility?
Yes in a practical sense: they position SIREN as a decision-support tool for choosing recommender strategies under societal-diversity objectives.

### Q14. What baseline do they compare against?
Random and MostPopular baselines, plus ItemKNN, UserKNN, and WeightedBPRMF from MyMediaLite.

### Q15. What taxonomy/categories do they propose?
`N/A` formal taxonomy; they instead specify simulation requirements for online news and a modular framework decomposition.

### Q16. What gaps or open problems do they identify?
Open issues include imperfect simulation realism, metric-to-human-perception mismatch, and need to model additional contexts/user types and richer editorial dynamics.

### Q17. Do they mention transformers/autoregressive models?
No transformer/autoregressive modeling focus; methods are probabilistic/agent-based simulation components.

## 2) T-RECS: A Simulation Tool to Study the Societal Impact of Recommender Systems (Lucherini et al., 2021)

### Availability
Full PDF available locally (`T-RECS_ A Simulation Tool to Study the Societal Impact of Recommender Systems.pdf`).

### Q1. What problem does this paper solve?
It lowers the engineering/reproducibility barrier for long-term recommender-system simulation studies by providing a unified simulation toolkit.

### Q2. What method do they use?
An open-source modular Python simulation framework (agent-based style) for users, items/content creators, algorithms, and measurement modules.

### Q3. How is this relevant to my thesis?
Directly relevant as infrastructure for experimenting with interaction simulators and feedback-loop assumptions without rebuilding simulators from scratch.

### Q4. How do they define an "interaction"?
A timestep loop: model predicts scores, serves items, users consume/provide feedback, and the system updates state from user-item feedback.

### Q5. Do they generate sequential sessions or independent events?
Sequential, multi-timestep dynamics over arbitrarily long horizons, including repeated retraining and adaptive content-generation settings.

### Q6. What data do they use?
Mostly synthetic simulation setups; demonstrated through replications including Chaney-style simulations (100 steps, 10 new items/step, 1,000 final items) and network-scale diffusion simulations (up to 1,000,000 users).

### Q7. Do they handle multiple action types or just one?
Default behavior often uses one implicit interaction per user per step, but the framework supports custom behaviors (e.g., sharing/creator adaptation) and multi-agent dynamics.

### Q8. How do they handle discrete vs continuous outputs?
Continuous latent representations (user/item attributes/scores) drive discrete interaction events (consume/share/select) and ranked recommendations.

### Q9. How do they handle variable-length sequences?
Temporal horizon and catalog growth are dynamic; new items/content creators can be introduced over time, and interaction histories accumulate.

### Q10. What conditioning do they use?
Conditioning includes user preferences, item attributes, recommendation model internals, interleaving/exposure assumptions, and content-creator response to feedback.

### Q11. Do they mention training stability issues?
Not GAN-mode-collapse style; they discuss simulation variance and emphasize confidence intervals/repeated runs for robust inference.

### Q12. How do they evaluate the quality of generated data?
By constructive replication and outcome metrics tied to target phenomena (e.g., Jaccard-based homogenization, cascade popularity/virality, creator-entropy trends).

### Q13. Do they test downstream utility?
Yes: they demonstrate that T-RECS can reproduce prior findings and support novel hypothesis testing with lower implementation overhead.

### Q14. What baseline do they compare against?
Replication baselines include random/ideal and common recommender models (e.g., popularity, content filtering, matrix factorization, social filtering) depending on scenario.

### Q15. What taxonomy/categories do they propose?
They consistently structure simulators into interacting components: users, items/content creators, recommendation model, and measurement modules.

### Q16. What gaps or open problems do they identify?
They highlight metric inconsistency across literature, reproducibility challenges, uncertainty quantification needs, and unresolved long-term societal-effect questions.

### Q17. Do they mention transformers/autoregressive models?
No transformer/autoregressive emphasis; the paper focuses on simulation infrastructure and agent interactions.

## 3) SimuRec: Workshop on Synthetic Data and Simulation Methods for Recommender Systems Research (Ekstrand et al., 2021)

### Availability
Full PDF available locally (`SimuRec: Workshop on Synthetic Data and Simulation Methods for Recommender Systems Research.pdf`).

### Q1. What problem does this paper solve?
It addresses the lack of agreed best practices for using simulation and synthetic data in recommender-systems research.

### Q2. What method do they use?
Workshop report/position summary: community discussion format producing a consensus report plus a research agenda.

### Q3. How is this relevant to my thesis?
Useful for positioning and methodology framing: it clarifies where simulation is useful, where it is weak, and what validation/reporting standards are still missing.

### Q4. How do they define an "interaction"?
`N/A` as a formal model definition; they discuss interaction/simulation methods at meta-methodological level.

### Q5. Do they generate sequential sessions or independent events?
`N/A` - no implemented simulator in this paper.

### Q6. What data do they use?
No new experimental dataset; content is based on workshop submissions/discussions and prior literature.

### Q7. Do they handle multiple action types or just one?
`N/A` - no concrete data-generation model in this paper.

### Q8. How do they handle discrete vs continuous outputs?
`N/A` - methodological workshop report, not a generative model.

### Q9. How do they handle variable-length sequences?
`N/A`.

### Q10. What conditioning do they use?
`N/A`.

### Q11. Do they mention training stability issues?
`N/A` for model-training details.

### Q12. How do they evaluate the quality of generated data?
They focus on the need for evaluation criteria and validation protocols rather than providing a new empirical metric pipeline.

### Q13. Do they test downstream utility?
`N/A` - no empirical downstream benchmark in this report.

### Q14. What baseline do they compare against?
`N/A` - no experimental comparison table.

### Q15. What taxonomy/categories do they propose?
They frame use-case categories and methodological questions (when simulation is useful/ill-suited, how to validate/report), but not a strict formal taxonomy.

### Q16. What gaps or open problems do they identify?
Major gaps: unclear best practices, limited methodological validation research, and open questions on robustness/reproducibility/evaluation of simulation-based RS studies.

### Q17. Do they mention transformers/autoregressive models?
No transformer/autoregressive emphasis.

## 4) Modeling User Behaviour in Research Paper Recommendation System (Chaudhuri et al., 2021)

### Availability
Full PDF available locally (`Modeling User Behaviour in Research Paper Recommendation System.pdf`).

### Q1. What problem does this paper solve?
It models dynamic user intention for research-paper recommendation, beyond static preference profiles.

### Q2. What method do they use?
Hybrid topic extraction (LDA + Word2Vec) plus LSTM-based sequential intention prediction using temporal/session features.

### Q3. How is this relevant to my thesis?
Directly relevant for interaction modeling design: it operationalizes user intention as a time-conditioned sequence prediction problem.

### Q4. How do they define an "interaction"?
Interactions are user clicks/liked papers from recommendation logs, represented with topic, time difference, and session number features.

### Q5. Do they generate sequential sessions or independent events?
Sequential sessions; historical topic sequences are used to predict next topic of interest.

### Q6. What data do they use?
Dataset 1: titles of 2,000 papers from Scopus for topic modeling. Dataset 2: interaction logs with 50 users and 5,213 items (2019-10-12 to 2020-05-18) for intention modeling.

### Q7. Do they handle multiple action types or just one?
Primarily one implicit positive action type (clicked/liked papers).

### Q8. How do they handle discrete vs continuous outputs?
Topic labels/predictions are discrete classes; temporal features (time differences) are numeric inputs for sequential prediction.

### Q9. How do they handle variable-length sequences?
Historical sequences are transformed into supervised windows (lookback format), effectively using fixed-size sequence inputs for LSTM training.

### Q10. What conditioning do they use?
Past topic sequence + timestamp-derived features + session context.

### Q11. Do they mention training stability issues?
No explicit adversarial-training stability discussion.

### Q12. How do they evaluate the quality of generated data?
Not synthetic-data generation; they evaluate model quality using F1 (topic extraction), and accuracy/RMSE for intention prediction.

### Q13. Do they test downstream utility?
Yes: user-study-based recommendation evaluation against search engines using Recall@10, Precision@10, MAP@10, and CTR.

### Q14. What baseline do they compare against?
LDA-only topic pipeline; sequential baselines FPM, Markov Chain Model, CNN; and recommendation baselines Google Scholar, Microsoft Academic Search, and CiteSeer.

### Q15. What taxonomy/categories do they propose?
`N/A` formal taxonomy.

### Q16. What gaps or open problems do they identify?
They note limitations around richer temporal drift modeling and missing contextual/item-item factors; future work suggests broader preference/context features.

### Q17. Do they mention transformers/autoregressive models?
No transformer/autoregressive model is proposed; sequence modeling is LSTM-based.

## 5) Generative Adversarial Reward Learning for Generalized Behavior Tendency Inference (Chen et al., 2021)

### Availability
Full PDF available locally (`Generative Adversarial Reward Learning for Generalized Behavior Tendency Inference.pdf`).

### Q1. What problem does this paper solve?
It replaces manually crafted, task-specific RL reward functions with a learned reward framework for generalized behavior-tendency inference.

### Q2. What method do they use?
Generative inverse reinforcement learning with a discriminative actor-critic design and Wasserstein GAN-based adversarial reward learning.

### Q3. How is this relevant to my thesis?
Highly relevant as an interaction-modeling alternative that learns behavior guidance from demonstrations instead of fixed heuristics.

### Q4. How do they define an "interaction"?
As MDP transitions over state-action-reward(-next-state), with expert and learned policies compared via occupancy/distribution matching.

### Q5. Do they generate sequential sessions or independent events?
Sequential trajectories over episodes/timesteps in dynamic environments.

### Q6. What data do they use?
Three scenarios: SUMO-based traffic signal control, VirtualTB online recommendation environment, and COCO-18 Search scanpath prediction.

### Q7. Do they handle multiple action types or just one?
Multiple action spaces across domains (traffic actions, recommendation decisions, gaze/scanpath actions).

### Q8. How do they handle discrete vs continuous outputs?
State/action representations are learned with neural policies; reward is learned as continuous scoring; adversarial distribution matching uses Wasserstein objectives.

### Q9. How do they handle variable-length sequences?
Trajectory-based training with replay buffers and explicit absorbing-state handling.

### Q10. What conditioning do they use?
Conditioning includes state-action pairs, expert demonstrations, environment feedback, and reward shaping terms.

### Q11. Do they mention training stability issues?
Yes. They explicitly target instability/sample-efficiency issues and use off-policy learning + Wasserstein GAN (with gradient penalty) to improve stability.

### Q12. How do they evaluate the quality of generated data?
They evaluate learned behavior quality via task performance metrics: waiting time (traffic), CTR (recommendation), and scanpath metrics (cumulative probability, mismatch, ratio).

### Q13. Do they test downstream utility?
Yes, across multiple downstream tasks and environments where learned behavior policy quality matters.

### Q14. What baseline do they compare against?
Traffic: Q-Learning, DQN, SARSA, A2C. Recommendation: IRecGAN, PGCR, GAUM, KGRL. Scanpath: Detector, Fixation heuristics, BC-CNN, BC-LSTM, IRL.

### Q15. What taxonomy/categories do they propose?
`N/A` formal taxonomy.

### Q16. What gaps or open problems do they identify?
They discuss remaining issues in giant state/action spaces, replay sampling quality, and constraints in Wasserstein training/optimization.

### Q17. Do they mention transformers/autoregressive models?
No transformer/autoregressive focus; method is inverse-RL + adversarial reward learning.

## 6) A Survey Of Synthetic Data Generation for Machine Learning (Abufadda et al., 2021)

### Availability
Only abstract-level `.md` content is available locally (`A_Survey_Of_Synthetic_Data_Generation_for_Machine_learning.md`).

### Q1. What problem does this paper solve?
It reviews synthetic data generation methods for ML settings where real data is scarce or sensitive (especially healthcare).

### Q2. What method do they use?
Survey/review of synthetic data generation (augmentation) methods and their impact on ML performance.

### Q3. How is this relevant to my thesis?
Background relevance: useful broad context on why synthetic data is needed under scarcity/privacy constraints.

### Q4. How do they define an "interaction"?
`N/A` from available abstract-only text.

### Q5. Do they generate sequential sessions or independent events?
`N/A` from available abstract-only text.

### Q6. What data do they use?
Limited evidence: review focus appears healthcare-centric; no concrete dataset breakdown is available in the local abstract.

### Q7. Do they handle multiple action types or just one?
`N/A` from available abstract-only text.

### Q8. How do they handle discrete vs continuous outputs?
`N/A` from available abstract-only text.

### Q9. How do they handle variable-length sequences?
`N/A` from available abstract-only text.

### Q10. What conditioning do they use?
`N/A` from available abstract-only text.

### Q11. Do they mention training stability issues?
`N/A` from available abstract-only text.

### Q12. How do they evaluate the quality of generated data?
Limited evidence: they discuss how generated data helps improve ML performance, but detailed metric protocols are not visible.

### Q13. Do they test downstream utility?
At review level, yes (improvement in ML algorithms is central), but local abstract lacks per-study detail.

### Q14. What baseline do they compare against?
`N/A` from available abstract-only text.

### Q15. What taxonomy/categories do they propose?
Limited evidence: they organize by available synthetic data generation/augmentation methods, mainly in healthcare.

### Q16. What gaps or open problems do they identify?
Core gap is insufficient accessible data due to scarcity and privacy/security barriers.

### Q17. Do they mention transformers/autoregressive models?
No such mention in the locally available abstract.

## 7) Synthetic Data - what, why and how? (Jordon et al., 2022)

### Availability
Full PDF available locally (`Synthetic Data - what, why and how_.pdf`).

### Q1. What problem does this paper solve?
It clarifies what synthetic data can and cannot do, especially for privacy-sensitive data sharing and ML development.

### Q2. What method do they use?
Comprehensive report/survey with conceptual frameworks for privacy, fidelity, utility, auditing, and deployment practices.

### Q3. How is this relevant to my thesis?
Strong methodological background for evaluating synthetic-data pipelines and avoiding privacy/utility misconceptions.

### Q4. How do they define an "interaction"?
`N/A` for RS interaction semantics; focus is general synthetic data methodology.

### Q5. Do they generate sequential sessions or independent events?
`N/A` as a methodological survey/report rather than a single generator.

### Q6. What data do they use?
No single benchmark dataset; they synthesize evidence and examples across domains with emphasis on private data release contexts.

### Q7. Do they handle multiple action types or just one?
`N/A`.

### Q8. How do they handle discrete vs continuous outputs?
No single output mechanism; they survey multiple generator families (e.g., GANs, VAEs, agent-based/econometric models).

### Q9. How do they handle variable-length sequences?
`N/A` for one model; sequence handling depends on selected generator class in surveyed literature.

### Q10. What conditioning do they use?
Conceptually task/use-case conditioning is central (privacy, fairness, augmentation), but not one fixed conditioning architecture.

### Q11. Do they mention training stability issues?
They flag opacity/uncertainty in over-parameterized black-box generators, but not as a single-model training study.

### Q12. How do they evaluate the quality of generated data?
They structure evaluation around utility, fidelity, and privacy, including utility-driven (e.g., TSTR-style) and fidelity-driven analyses plus privacy auditing/attacks.

### Q13. Do they test downstream utility?
Yes conceptually: extensive discussion of using synthetic data for model development and comparing synthetic-vs-real conclusions.

### Q14. What baseline do they compare against?
Framework-level baseline is real data/task performance; they discuss comparing conclusions/model rankings between synthetic and real data workflows.

### Q15. What taxonomy/categories do they propose?
They organize by use cases (privacy, fairness, augmentation), evaluation axes (utility/fidelity/privacy), and private synthetic-data generation/auditing approaches.

### Q16. What gaps or open problems do they identify?
Key gaps include non-trivial privacy guarantees, outlier handling under privacy constraints, and lack of one-size-fits-all differentially private synthetic-data methods.

### Q17. Do they mention transformers/autoregressive models?
Transformers are not a central axis in this report; focus is broader synthetic-data governance/evaluation methodology.

## 8) Machine Learning for Synthetic Data Generation: A Review (Lu et al., 2024/2025 preprint)

### Availability
Full PDF available locally (`Machine Learning for Synthetic Data Generation_ A Review.pdf`).

### Q1. What problem does this paper solve?
It surveys ML-driven synthetic data generation to address data quality, scarcity, privacy, and governance challenges across domains.

### Q2. What method do they use?
A broad systematic review spanning applications, generative model families, privacy/fairness methods, evaluation strategies, and future challenges.

### Q3. How is this relevant to my thesis?
Useful breadth paper for alternatives discussion and for framing evaluation/privacy/fairness constraints around simulator-generated data.

### Q4. How do they define an "interaction"?
`N/A` for RS-specific interaction tuples; this is cross-domain synthetic-data review.

### Q5. Do they generate sequential sessions or independent events?
Not a single generator; they cover both sequential modalities (text/time series) and non-sequential data types.

### Q6. What data do they use?
Survey-level coverage across computer vision, speech/audio, NLP, healthcare, and business scenarios.

### Q7. Do they handle multiple action types or just one?
`N/A` in the RS-action sense; reviewed tasks vary widely across modalities/applications.

### Q8. How do they handle discrete vs continuous outputs?
They review multiple paradigms: language models for token sequences, GAN/VAE/diffusion-style models for continuous and mixed data, and tabular-specific methods.

### Q9. How do they handle variable-length sequences?
Sequential/time-series and text generation methods are explicitly covered, including autoregressive language modeling approaches.

### Q10. What conditioning do they use?
Conditioning is method-dependent in surveyed works (e.g., conditional GAN variants, multimodal conditioning, task/domain constraints).

### Q11. Do they mention training stability issues?
Yes, particularly around GAN training and privacy-preserving synthesis tradeoffs in modern/foundation-model settings.

### Q12. How do they evaluate the quality of generated data?
They categorize evaluation into human assessment, statistical/distance-based checks, downstream-task performance, and application-specific evaluations.

### Q13. Do they test downstream utility?
Yes at survey level: downstream utility on real tasks is treated as a core evaluation paradigm.

### Q14. What baseline do they compare against?
No single benchmark baseline; they summarize diverse baseline conventions across reviewed domains and methods.

### Q15. What taxonomy/categories do they propose?
They organize by application domain, generative model family (LM/VAE/GAN/RL/diffusion), and cross-cutting concerns (privacy, fairness, evaluation).

### Q16. What gaps or open problems do they identify?
They emphasize missing standardized tools/metrics, outlier and corner-case coverage, inherited bias, and security/privacy risks in foundation-model-based synthesis.

### Q17. Do they mention transformers/autoregressive models?
Yes. They explicitly include language-model generation and list autoregressive modeling among core generative paradigms.

## 9) Survey on Synthetic Data Generation, Evaluation Methods and GANs (Figueira and Vaz, 2022)

### Availability
Full PDF available locally (`Survey on Synthetic Data Generation, Evaluation Methods\nand GANs.pdf`).

### Q1. What problem does this paper solve?
It unifies three strands typically treated separately: synthetic data generation methods, GAN architectures, and synthetic data evaluation methods.

### Q2. What method do they use?
Systematic survey across major databases (WoS, Scopus, IEEE, ACM), with synthesis focused on GAN evolution and tabular-data generation.

### Q3. How is this relevant to my thesis?
Useful Tier-2 breadth paper for alternative generation methods and quality-assessment strategies, especially for tabular synthetic data.

### Q4. How do they define an "interaction"?
`N/A` in RS sense; focus is synthetic data methods across domains.

### Q5. Do they generate sequential sessions or independent events?
Mostly method review for tabular and other data types; no single session simulator is proposed.

### Q6. What data do they use?
Survey-level corpus plus discussed benchmark datasets from referenced works (especially tabular-generation studies such as TGAN/CTGAN evaluations).

### Q7. Do they handle multiple action types or just one?
`N/A` as a recommender interaction question.

### Q8. How do they handle discrete vs continuous outputs?
They detail tabular GAN approaches that explicitly model mixed types (continuous + categorical), including TGAN/CTGAN preprocessing and conditional mechanisms.

### Q9. How do they handle variable-length sequences?
`N/A` for the main tabular focus; sequence handling is not the central contribution.

### Q10. What conditioning do they use?
They discuss conditional generation variants (e.g., CGAN-style conditioning and tabular adaptations).

### Q11. Do they mention training stability issues?
Yes. They review common GAN training problems (e.g., oscillation, vanishing gradients, mode collapse) and architecture advances addressing them.

### Q12. How do they evaluate the quality of generated data?
They summarize several families: descriptive/statistical checks, graphical inspection, ML efficacy, GAN-train/GAN-test, and precision/recall/authenticity-style measures.

### Q13. Do they test downstream utility?
At review level yes: ML efficacy and task performance are central evaluation perspectives.

### Q14. What baseline do they compare against?
In discussed studies, baselines include real data and competing generators/statistical synthesizers (e.g., GC, BN variants, other GAN models).

### Q15. What taxonomy/categories do they propose?
They organize by standard vs deep methods, GAN architecture timeline/flavors, tabular GAN subfamilies, and evaluation-method groupings.

### Q16. What gaps or open problems do they identify?
They stress that GAN progress is heavily image-centric, while tabular synthesis and robust task-appropriate evaluation remain underdeveloped.

### Q17. Do they mention transformers/autoregressive models?
Transformer/autoregressive models are not a central theme; the survey is primarily GAN-centric.

## 10) Synthesizing Tabular Data / TGAN (Xu and Veeramachaneni, 2018)

### Availability
Full PDF available locally (`Synthesizing Tabular Data.pdf`).

### Q1. What problem does this paper solve?
It generates realistic synthetic tabular data with mixed continuous/discrete columns while preserving useful statistical structure for ML tasks.

### Q2. What method do they use?
TGAN: LSTM-with-attention generator plus MLP discriminator, with dedicated preprocessing for tabular variable types.

### Q3. How is this relevant to my thesis?
Important Tier-2 alternative for synthetic data generation baselines, especially where controlled tabular synthesis is needed.

### Q4. How do they define an "interaction"?
No recommender interaction semantics; each table row is a sample from a learned joint tabular distribution.

### Q5. Do they generate sequential sessions or independent events?
Independent tabular rows, generated column-by-column in an autoregressive-like row construction process.

### Q6. What data do they use?
Three UCI tabular datasets: Census-Income, KDD99, and Covertype.

### Q7. Do they handle multiple action types or just one?
`N/A` - this is tabular row synthesis, not action-stream simulation.

### Q8. How do they handle discrete vs continuous outputs?
Continuous variables use mode-specific normalization via Gaussian mixtures (value + cluster representation); discrete variables are one-hot/softmax generated.

### Q9. How do they handle variable-length sequences?
`N/A` - fixed table schema; no variable-length session modeling.

### Q10. What conditioning do they use?
Generation is conditioned on random latent noise plus previously generated columns via LSTM state and attention context.

### Q11. Do they mention training stability issues?
Yes. They note challenges in tabular GAN training and add KL-divergence/noise terms to improve effective learning/stability for discrete and clustered outputs.

### Q12. How do they evaluate the quality of generated data?
Using machine-learning efficacy (train on synthetic, test on real), correlation preservation (NMI matrices), and nearest-neighbor distance analysis.

### Q13. Do they test downstream utility?
Yes: models trained on synthetic data are evaluated on real test data; they also check model-ranking preservation.

### Q14. What baseline do they compare against?
Gaussian Copula (GC), Bayesian-network variants (e.g., BN-Co/BN-Id), and real-data references.

### Q15. What taxonomy/categories do they propose?
`N/A` formal taxonomy.

### Q16. What gaps or open problems do they identify?
They note limitations to single-table mixed-type data and point to future work on sequential data and multi-table synthesis.

### Q17. Do they mention transformers/autoregressive models?
No transformer methods; generation is recurrent/autoregressive-like through LSTM column sequencing.

