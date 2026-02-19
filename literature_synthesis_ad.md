# A-D Early Hypotheses and Literature-Based Answers

This document synthesizes the completed Tier 1-3 review notes into early hypotheses for the four assignment questions from `assignment.pdf`. It is literature-grounded but still provisional, and should be treated as a thesis-direction draft rather than final claims.

## A) How can interactions be best defined?

### Early Hypothesis
The most useful interaction definition for this thesis is an event-level typed tuple with explicit time, exposure context, and outcome fields, grouped into sessions and linked across sessions by user history.

### Literature-Based Answer
Across Tier 1 and Tier 2 RS simulation papers, "interaction" is broader than `<user,item,rating>`. Papers that better capture realistic system dynamics model interactions as time-indexed events with state and context, not static preference points.

Practical synthesis from the reviewed literature suggests a two-level structure:

1. Event level (atomic interaction):
   - `user_id`
   - `session_id`
   - `event_time` (or time delta)
   - `item_id`
   - `action_type` (view/click/cart/buy/etc.)
   - `exposure_context` (position, candidate set/slate, recommendation source)
   - optional outcome fields (dwell, conversion flag, reward proxy)
2. Sequence level:
   - ordered events within session
   - user state carried across sessions (history-dependent behavior)

This aligns with interaction definitions seen in long-term simulators and behavior simulators, where recommendation exposure and temporal order change future behavior.

### Recommended Thesis Position
Define interactions in the thesis as a typed temporal event tuple, not rating-only tuples. Make this definition an explicit contribution in the literature/design chapter, because it directly answers research question A and justifies why a sequence generator is needed.

### Risks / Uncertainties
- Some reviewed Tier 3 papers are healthcare/tabular and do not use RS interaction semantics directly.
- A richer schema increases modeling complexity and data sparsity for rare action types.
- If the upstream arrival simulator interface is narrow, some context fields may need to be optional.

### Evidence Trace
- Tier 1: Stavinova et al. (survey) emphasizes feedback-loop interactions and simulator quality dimensions.
- Tier 1: McInerney et al. (Accordion) models events as `(time,user,item,outcome)` with visit dynamics.
- Tier 1: Zhao et al. (UserSim) models sequential user behavior conditioned on prior interactions.
- Tier 1: DataGenCARS and Jakomin papers reinforce context-aware and stream-based interaction framing.
- Tier 2: SIREN and T-RECS model iterative, stateful user-item interaction processes over time.
- Tier 2: SimuRec highlights methodological need to formalize what interaction processes are being simulated.

## B) How can interactions be modelled to mimic real-life scenarios?

### Early Hypothesis
A hybrid strategy best mimics real-life behavior: autoregressive sequence modeling for within-session dynamics, plus explicit temporal/exposure mechanisms for long-term feedback effects.

### Literature-Based Answer
The reviewed papers show no single model class dominates all realism dimensions:

- Markov/statistical stream generators are simple and controllable but often miss longer dependencies.
- GAN-based simulators can capture high-dimensional patterns but can be unstable and harder to validate.
- Process/agent simulators capture feedback loops and societal effects but need stronger assumptions and calibration.
- Bayesian network methods improve interpretability/privacy in tabular domains but are less natural for rich sessional RS event streams.

For this thesis context (interaction generator component, arrival simulator already separate), the literature most strongly supports sequence-conditioned modeling for interaction trajectories, with realism constraints beyond pure next-step likelihood.

### Recommended Thesis Position
Use a sequence-first generator as the primary model for component (2), and include explicit conditioning on:
- prior interaction history,
- action-type dependencies,
- recommendation/exposure context,
- temporal features (at minimum event ordering; ideally time deltas).

Treat long-term dynamics as either:
- a second-stage extension (visit intensity / inter-session process), or
- an external simulator coupling (arrival component + interaction component loop).

### Risks / Uncertainties
- Highly expressive models may optimize short-horizon metrics while drifting from real distributional behavior.
- If training data lacks rich exposure/context fields, conditioning quality is capped.
- Literature indicates instability/comparison issues for adversarial approaches and non-standardized evaluation.

### Evidence Trace
- Tier 1: Accordion demonstrates benefit of explicit visit/time process modeling for long-term effects.
- Tier 1: UserSim and related GAN-user simulation work shows sequence generation viability and adversarial tradeoffs.
- Tier 1: Chaney highlights simulation pitfalls and realism-vs-evaluation challenges.
- Tier 2: SIREN/T-RECS show value of dynamic, iterative, feedback-aware simulation.
- Tier 2: GARL (Chen) supports behavior-tendency modeling under sequential and reward-like signals.
- Tier 3: GAN/Bayesian survey papers reinforce that model choice must match data type, goals, and evaluation constraints.

## C) Which simulation techniques can be implemented for the data generator?

### Early Hypothesis
A practical implementation portfolio should include one simple baseline, one legacy-comparable sequential baseline, and one primary modern generator, all evaluated under the same realism and utility protocol.

### Literature-Based Answer
From the reviewed literature, implementable technique families are:

1. Statistical/process baselines:
   - first-order transition/Markov or rule-driven stream generators
   - useful for interpretability and sanity baselines
2. Neural sequential generators:
   - RNN/GRU/LSTM or transformer-style autoregressive models
   - suitable for event-sequence generation with history conditioning
3. Adversarial simulation/generation:
   - GAN-based user simulators
   - useful comparison class but higher stability/evaluation burden
4. Framework/agent simulation wrappers:
   - SIREN/T-RECS-like looped simulators for policy-level effects
5. Bayesian/tabular generators:
   - useful especially for structured tabular subproblems and privacy-focused synthesis

### Recommended Thesis Position
Implement (or preserve) a focused three-technique stack for the core thesis comparison:

1. Simple baseline: Markov/transition generator (transparent reference).
2. Sequential baseline: RNN-style generator (to address assignment's "is RNN right choice?" concern).
3. Primary model: autoregressive transformer-like interaction generator (or currently selected sequence-first model).

Then add lightweight realism constraints (valid action chains, timestamp consistency, optional rejection/repair rules) to improve plausibility without changing core model family.

### Risks / Uncertainties
- Adding too many technique families can dilute thesis focus and execution time.
- GAN/Bayesian methods may be cited as alternatives but not fully implemented if scope is constrained.
- Comparability requires strict split/control of preprocessing and decoding rules.

### Evidence Trace
- Tier 1: UserSim, Bobadilla, and medGAN-derived ideas show adversarial options and tradeoffs.
- Tier 1: Jakomin/DataGenCARS provide statistical and configurable generator alternatives.
- Tier 1/2: Chaney, SIREN, T-RECS emphasize simulation-loop techniques and caution on assumptions.
- Tier 2/3: Survey papers (Stavinova, Lu, Figueira, Hernandez, Creswell) support multi-family positioning and method-selection by objective.

## D) Which choices need to be made to successfully demonstrate a data simulator?

### Early Hypothesis
A successful demonstrator requires two proof lines at once: (i) synthetic data realism relative to real data and (ii) downstream recommender utility when trained/tested under controlled settings.

### Literature-Based Answer
The literature repeatedly shows that demonstrating only one axis (e.g., next-item accuracy or visual plausibility) is insufficient. A convincing simulator demo must define:

1. Scope and interface choices:
   - what component (2) receives from arrival simulator
   - what event schema it outputs
2. Baseline choices:
   - at least one simple and one legacy-relevant comparator
3. Fidelity evaluation choices:
   - distributional match (action mix, session length, inter-event timing, item popularity/long-tail)
   - sequence realism (behavior chains, impossible transitions, ordering consistency)
4. Utility evaluation choices:
   - train downstream RS on synthetic, evaluate on held-out real
   - compare against real-trained and baseline-generated references
5. Reproducibility choices:
   - fixed splits/seeds
   - deterministic preprocessing and explicit decoding rules
   - transparent failure cases and ablations

### Recommended Thesis Position
Define the demonstrator as an end-to-end pipeline:

`arrival process -> interaction generator -> synthetic logs -> downstream RS training/evaluation`

Success criteria should include both:
- fidelity thresholds (or relative superiority vs baselines), and
- downstream utility parity gap reporting.

Present results by model family, not only by single headline metric. Include at least one ablation showing which conditioning signals materially improve realism.

### Risks / Uncertainties
- Good fidelity does not guarantee high downstream utility, and vice versa.
- Some metrics can be gamed by memorization-like behavior; privacy and uniqueness checks should be included where feasible.
- If arrival component contracts are still evolving, demonstrator integration should use a clearly documented stub/adapter.

### Evidence Trace
- Tier 1: Chaney explicitly frames key simulation design/evaluation challenges.
- Tier 1: Accordion and UserSim demonstrate value of task-level and policy-level evaluation beyond raw generation.
- Tier 2: T-RECS/SIREN demonstrate the importance of long-run effect metrics and repeated-run uncertainty handling.
- Tier 2/3: Synthetic data survey/systematic review papers emphasize lack of universal metrics and need for multi-metric evaluation.
- Tier 3: Kaur/Martins/Bayesian works reinforce utility-plus-disclosure and uncertainty-aware evaluation as strong practice.

## Provisional Conclusion Across A-D

Early literature-based direction: treat interactions as temporal typed events, model them with history-conditioned sequence generators plus explicit constraints, compare against transparent baselines, and demonstrate success with both realism and downstream RS utility in a reproducible pipeline.
