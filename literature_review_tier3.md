# Tier 3 Literature Review

This file covers Tier 3 papers from `paper_reading_questions.md` in the required order. Each paper uses the full Q1-Q17 template; non-applicable items are marked `N/A`. When full text was inaccessible, answers are based on available abstract/metadata and explicitly marked.

## 1) Generative Adversarial Networks: An Overview (Creswell et al., 2018)

### Availability
Local file contains abstract only (`Generative_Adversarial_Networks:_An_Overview.md`), and arXiv full text (`1710.07035`) was reviewed for high-level details.

### Q1. What problem does this paper solve?
It explains GAN fundamentals and variants, and clarifies why GANs are useful for representation learning without extensive labels.

### Q2. What method do they use?
Survey/review paper covering GAN architectures, training objectives, applications, and known failure modes.

### Q3. How is this relevant to my thesis?
It gives core conceptual background for GAN-based synthetic data generation and clarifies common pitfalls that matter when comparing methods.

### Q4. How do they define an "interaction"?
`N/A` - this is not an RS interaction paper.

### Q5. Do they generate sequential sessions or independent events?
`N/A` - not focused on session simulation; mostly image-generation contexts.

### Q6. What data do they use?
No single benchmark dataset is central; the paper is a broad methods overview with examples across GAN literature.

### Q7. Do they handle multiple action types or just one?
`N/A` - not modeled as action-stream data.

### Q8. How do they handle discrete vs continuous outputs?
They discuss that GANs are naturally easier for continuous outputs (e.g., images) and highlight that discrete generation is harder and often needs specialized tricks.

### Q9. How do they handle variable-length sequences?
Not a core contribution; variable-length sequence generation is discussed only as related work context.

### Q10. What conditioning do they use?
They review conditional settings (class/text/location conditioning) in conditional GAN variants.

### Q11. Do they mention training stability issues?
Yes. Major issues include mode collapse, unstable optimization, and convergence/equilibrium problems; they also discuss mitigation directions (e.g., Wasserstein formulations, unrolling).

### Q12. How do they evaluate the quality of generated data?
They explicitly note evaluation remains difficult and metric-dependent, without a single universally accepted quality metric.

### Q13. Do they test downstream utility?
At survey level, yes: they discuss downstream tasks such as semi-supervised learning, representation learning, editing, and translation.

### Q14. What baseline do they compare against?
`N/A` single baseline - this is a survey synthesizing many papers rather than one controlled benchmark experiment.

### Q15. What taxonomy/categories do they propose?
They organize the field by architecture and use-case families (e.g., fully connected GANs, convolutional GANs, conditional GANs, adversarial autoencoder-style hybrids, and image-to-image translation lines).

### Q16. What gaps or open problems do they identify?
Key open problems: mode collapse, instability around saddle points/equilibria, and weak consensus on evaluation.

### Q17. Do they mention transformers/autoregressive models?
They mention autoregressive models as comparators; transformers are not part of the discussion (pre-transformer-era GAN review framing).

## 2) Practical Synthetic Data Generation: Balancing Privacy and the Broad Availability of Data (El Emam et al., 2020)

### Availability
No local full book text was available. Notes are based on publisher metadata/description and table-of-contents level material.

### Q1. What problem does this paper solve?
It addresses how to generate useful synthetic data from sensitive real data while controlling privacy risk and preserving analytical value.

### Q2. What method do they use?
Practical framework/book treatment: process guidance plus statistical and ML/deep-learning synthesis methods, utility testing, and privacy-risk assessment.

### Q3. How is this relevant to my thesis?
It is strong practical context for implementation choices, validation strategy, and privacy framing around synthetic-data pipelines.

### Q4. How do they define an "interaction"?
`N/A` - not an RS interaction simulator paper.

### Q5. Do they generate sequential sessions or independent events?
Mostly tabular/process guidance; sequence synthesis is discussed conceptually in methodology chapters.

### Q6. What data do they use?
Cross-domain case-study framing (e.g., healthcare/finance/transport/manufacturing) rather than one canonical experimental dataset.

### Q7. Do they handle multiple action types or just one?
`N/A` in RS-action sense.

### Q8. How do they handle discrete vs continuous outputs?
At framework level: distribution fitting, copula/statistical approaches, and ML/deep methods for mixed data types.

### Q9. How do they handle variable-length sequences?
Discussed as a practical synthesis topic, but not as a single reproducible benchmark experiment in available material.

### Q10. What conditioning do they use?
Conditioning is driven by source-data structure, feature dependencies, and explicit synthesis rules/constraints.

### Q11. Do they mention training stability issues?
Not centered on GAN instability; emphasis is more on process robustness, overfitting avoidance, utility, and privacy tradeoffs.

### Q12. How do they evaluate the quality of generated data?
They describe utility frameworks such as replication-of-analysis, univariate/bivariate/multivariate comparisons, and distinguishability checks.

### Q13. Do they test downstream utility?
Yes conceptually: synthetic data should preserve analytical conclusions and model-development usefulness.

### Q14. What baseline do they compare against?
`N/A` single baseline - this is a practical reference book rather than one controlled method paper.

### Q15. What taxonomy/categories do they propose?
A practical taxonomy appears in chapter themes: generation methods, utility metrics, disclosure risk, and deployment/governance operations.

### Q16. What gaps or open problems do they identify?
Trust, governance, ownership, certification, and operationalization challenges are highlighted as major barriers to broad adoption.

### Q17. Do they mention transformers/autoregressive models?
Deep-learning methods are covered broadly in available metadata; transformers are not prominent in the accessible material.

## 3) Leveraging Deep Learning Algorithms for Synthetic Data Generation to Design and Analyze Biological Networks (Achuthan et al., 2022)

### Availability
Only abstract/metadata was accessible (Springer page; no full-text access). Answers below are limited by abstract-level evidence.

### Q1. What problem does this paper solve?
It reviews how deep-learning generative methods can produce synthetic biomedical/healthcare data, especially unstructured modalities.

### Q2. What method do they use?
Review article with case-study discussion across deep generative model families (RNN, VAE, GAN).

### Q3. How is this relevant to my thesis?
It broadens context beyond recommender simulation and supports the synthetic-data methodology discussion from adjacent healthcare/biomedical domains.

### Q4. How do they define an "interaction"?
`N/A` - not an RS interaction paper.

### Q5. Do they generate sequential sessions or independent events?
Not explicitly reported in accessible abstract-level material.

### Q6. What data do they use?
Case-study examples include synthetic clinical notes, synthetic DNA sequences, and enriched experimental cancer-culture data.

### Q7. Do they handle multiple action types or just one?
`N/A` in RS-action terms.

### Q8. How do they handle discrete vs continuous outputs?
Abstract indicates model-family coverage (RNN/VAE/GAN) across text/image/biological settings, but no detailed output-encoding mechanics are accessible.

### Q9. How do they handle variable-length sequences?
Not detailed in accessible text; likely model-specific (e.g., sequence models for text/DNA), but details are not available without full paper access.

### Q10. What conditioning do they use?
Not explicitly specified in available abstract.

### Q11. Do they mention training stability issues?
No explicit stability analysis is visible in accessible abstract-level text.

### Q12. How do they evaluate the quality of generated data?
Presented via case-study framing in abstract, but specific quantitative evaluation protocols are not accessible.

### Q13. Do they test downstream utility?
Yes at high level: synthetic data is positioned as supporting better modeling/analysis in biomedical workflows.

### Q14. What baseline do they compare against?
Not reported in the accessible abstract/metadata.

### Q15. What taxonomy/categories do they propose?
They organize discussion by deep-learning architecture families and biomedical use-case modalities.

### Q16. What gaps or open problems do they identify?
From accessible text: need for robust methods and broader adoption/validation in healthcare and biomedical synthetic-data workflows.

### Q17. Do they mention transformers/autoregressive models?
Transformers are not mentioned in accessible abstract-level material.

## 4) Generating Multi-label Discrete Patient Records using Generative Adversarial Networks (Choi et al., 2018)

### Availability
Full text available via arXiv (`1703.06490`) and reviewed.

### Q1. What problem does this paper solve?
It proposes a way to generate realistic high-dimensional discrete EHR records for sharing/analysis under privacy constraints.

### Q2. What method do they use?
`medGAN`: GAN + autoencoder for multi-label discrete health records, with minibatch averaging and training refinements.

### Q3. How is this relevant to my thesis?
It is a foundational GAN-based synthetic-data method with clear utility/privacy evaluation, useful as a baseline and methodological reference.

### Q4. How do they define an "interaction"?
As patient-record feature vectors (diagnosis/medication/procedure code presence/count), not RS action tuples.

### Q5. Do they generate sequential sessions or independent events?
Independent aggregated records: they collapse longitudinal records into fixed-size vectors, so no explicit session sequence generation.

### Q6. What data do they use?
Three EHR sources: Sutter PAMF (~258K patients), MIMIC-III (~46K ICU patients), and a Sutter heart-failure cohort (~30K patients), transformed into high-dimensional code vectors.

### Q7. Do they handle multiple action types or just one?
They handle multiple clinical code groups (diagnoses/medications/procedures), but this is still tabular-record synthesis rather than multi-action RS logs.

### Q8. How do they handle discrete vs continuous outputs?
They target discrete binary/count outputs via autoencoder latent generation and decoder mapping, with different losses/activations for binary vs count settings.

### Q9. How do they handle variable-length sequences?
They avoid explicit variable-length sequence modeling by aggregating to fixed-length patient vectors.

### Q10. What conditioning do they use?
Generation is primarily noise-driven through learned latent structure; no explicit user/context conditioning beyond what is encoded in training distributions.

### Q11. Do they mention training stability issues?
Yes. They address mode collapse and instability with minibatch averaging, plus batch normalization and shortcut connections.

### Q12. How do they evaluate the quality of generated data?
Dimension-wise distribution checks, dimension-wise predictive performance, qualitative clinician review, and privacy-risk analyses (presence/attribute disclosure).

### Q13. Do they test downstream utility?
Yes: classifiers trained on synthetic data are compared against real-data-trained classifiers on held-out real test data.

### Q14. What baseline do they compare against?
Model/baseline comparisons include random-noise perturbation, independent sampling, stacked RBM/DBM, VAE, and medGAN ablations.

### Q15. What taxonomy/categories do they propose?
`N/A` formal taxonomy.

### Q16. What gaps or open problems do they identify?
They highlight limitations in longitudinal-sequence generation, need for stronger privacy guarantees, and remaining training/evaluation challenges.

### Q17. Do they mention transformers/autoregressive models?
They discuss prior discrete-generation approaches (e.g., SeqGAN-style RL methods) but do not include transformer methods.

## 5) Applying the Gaussian Mixture Model to Generate Large Synthetic Data from a Small Data Set (Chokwitthaya et al., 2020)

### Availability
Full conference paper text was accessible via NSF-PAR accepted manuscript mirror and reviewed.

### Q1. What problem does this paper solve?
It addresses small sample sizes in immersive virtual-environment (IVE) experiments by generating larger IID synthetic datasets.

### Q2. What method do they use?
Gaussian Mixture Model (GMM) trained with expectation-maximization to learn IVE data and sample IID synthetic points.

### Q3. How is this relevant to my thesis?
It provides a non-GAN statistical alternative for data augmentation/simulation when behavioral data is scarce.

### Q4. How do they define an "interaction"?
Participant light-switch behavior in a simulated office: users rate likelihood of turning lights on under defined scenarios.

### Q5. Do they generate sequential sessions or independent events?
Independent IID samples; no sequential trajectory/session model.

### Q6. What data do they use?
IVE light-switch experiment with 30 participants and 48 scenarios (2 switch locations x 4 tasks x 6 illuminance levels), with Likert-style switching probabilities.

### Q7. Do they handle multiple action types or just one?
Mostly one action type (switch-on behavior probability) under varying context factors.

### Q8. How do they handle discrete vs continuous outputs?
Scenario/context variables are encoded and modeled through Gaussian-mixture components; generated outputs are IID samples from fitted mixture distributions.

### Q9. How do they handle variable-length sequences?
`N/A` - no sequence modeling.

### Q10. What conditioning do they use?
Conditioned implicitly on experimental context variables (task, switch location, illuminance) through the fitted mixture model.

### Q11. Do they mention training stability issues?
They note overfitting risk in GMM and suggest future noise-based regularization and participant-diversity handling.

### Q12. How do they evaluate the quality of generated data?
Two-tailed t-tests compare means of real IVE data vs generated IID samples across task groups; reported differences are not statistically significant.

### Q13. Do they test downstream utility?
Yes conceptually: generated larger datasets are positioned to support downstream ML/performance analyses requiring more data.

### Q14. What baseline do they compare against?
Primary comparison is real IVE data vs GMM-generated synthetic samples (no broad multi-generator benchmark suite).

### Q15. What taxonomy/categories do they propose?
`N/A` formal taxonomy.

### Q16. What gaps or open problems do they identify?
Overfitting, participant-diversity effects, and IVE presence-quality measurement are listed as future-work issues.

### Q17. Do they mention transformers/autoregressive models?
No.

## 6) Practical Lessons from Generating Synthetic Healthcare Data with Bayesian Networks (De Benedetti et al., 2020)

### Availability
Only abstract/metadata was accessible (Springer chapter page; no full-text chapter access). Answers below are limited by abstract-level evidence.

### Q1. What problem does this paper solve?
It examines how to generate synthetic primary-care data that preserves realistic structure while reducing patient re-identification risk.

### Q2. What method do they use?
Practical Bayesian-network-based synthetic-data approach focused on real-world healthcare complexity and privacy constraints.

### Q3. How is this relevant to my thesis?
It is a directly relevant non-GAN alternative emphasizing trust/transparency and privacy in synthetic healthcare data.

### Q4. How do they define an "interaction"?
`N/A` in RS terms; framed as relationships in primary-care records.

### Q5. Do they generate sequential sessions or independent events?
Abstract states they consider modeling time, but exact temporal mechanics are not accessible without full text.

### Q6. What data do they use?
Primary-care healthcare data context; specific dataset sizes/schemas are not available in accessible abstract material.

### Q7. Do they handle multiple action types or just one?
`N/A` in RS-action framing.

### Q8. How do they handle discrete vs continuous outputs?
Not detailed in accessible abstract.

### Q9. How do they handle variable-length sequences?
Not detailed in accessible text.

### Q10. What conditioning do they use?
Conditioning appears to rely on modeling realistic joint relationships and temporal structure in healthcare data (abstract-level statement).

### Q11. Do they mention training stability issues?
No explicit training-stability discussion appears in accessible abstract.

### Q12. How do they evaluate the quality of generated data?
At abstract level: realism/trust in distributions/relationships plus reduced patient matching/identification risk.

### Q13. Do they test downstream utility?
Yes at high level: synthetic data is positioned as a substitute for restricted real primary-care data.

### Q14. What baseline do they compare against?
Not reported in accessible abstract metadata.

### Q15. What taxonomy/categories do they propose?
`N/A` formal taxonomy.

### Q16. What gaps or open problems do they identify?
Handling real-world complexity, temporal modeling, and minimizing synthetic-to-real patient matching risk are central challenges.

### Q17. Do they mention transformers/autoregressive models?
No mention in accessible abstract-level material.

## 7) Synthetic Data Generation for Tabular Health Records: A Systematic Review (Hernandez et al., 2022)

### Availability
Only abstract/metadata was reliably accessible in this environment; full text was not openly retrievable here. Answers are based on abstract-level evidence.

### Q1. What problem does this paper solve?
It synthesizes recent work on synthetic tabular healthcare data generation and evaluates method/evaluation trends.

### Q2. What method do they use?
Systematic review of 2016-2021 literature, analyzing 34 publications with focus on GAN-based methods.

### Q3. How is this relevant to my thesis?
It helps position method choices and evaluation gaps in healthcare tabular synthesis, useful for alternatives/background discussion.

### Q4. How do they define an "interaction"?
`N/A` - focus is tabular health-record synthesis literature, not RS interaction simulation.

### Q5. Do they generate sequential sessions or independent events?
Review focus is synthetic tabular records, which are typically row-based rather than session-sequence simulation.

### Q6. What data do they use?
They review 34 studies across healthcare tabular-record contexts (paper-level analysis, not one dataset experiment).

### Q7. Do they handle multiple action types or just one?
`N/A` in RS-action sense.

### Q8. How do they handle discrete vs continuous outputs?
At review level they compare multiple generation approaches (with special attention to GANs), but no single output-handling mechanism applies globally.

### Q9. How do they handle variable-length sequences?
Not a central focus in the accessible abstract; emphasis is tabular rather than sequence generation.

### Q10. What conditioning do they use?
Not standardized; varies across reviewed methods and datasets.

### Q11. Do they mention training stability issues?
Yes indirectly: they conclude GAN generalizability remains limited and further method development is needed.

### Q12. How do they evaluate the quality of generated data?
By reviewing reported literature metrics and benchmarking practices; they stress inconsistency across studies.

### Q13. Do they test downstream utility?
Review-level answer: yes, many included works evaluate utility, but methods and criteria are heterogeneous.

### Q14. What baseline do they compare against?
No universal baseline across the reviewed papers; comparison practices vary widely.

### Q15. What taxonomy/categories do they propose?
They report a classification of synthetic tabular-health approaches and analyze GAN-based methods in detail.

### Q16. What gaps or open problems do they identify?
Major gap: no universal method/metric for robust benchmarking; need better GAN generalizability on healthcare tabular data.

### Q17. Do they mention transformers/autoregressive models?
Not highlighted in accessible abstract-level evidence.

## 8) Application of Bayesian Networks to Generate Synthetic Health Data (Kaur et al., 2021)

### Availability
Full open-access text was available via PMC and reviewed.

### Q1. What problem does this paper solve?
It proposes an automated Bayesian-network method for generating realistic synthetic health data and compares it against medBGAN.

### Q2. What method do they use?
Learn a Bayesian-network structure/parameters from real data, then sample synthetic records from the learned probabilistic graph.

### Q3. How is this relevant to my thesis?
It is a strong non-GAN baseline family with explicit structure, interpretability, and privacy analysis.

### Q4. How do they define an "interaction"?
As record-level health-variable relationships (diagnoses/clinical variables), not RS interaction events.

### Q5. Do they generate sequential sessions or independent events?
Independent row-wise synthetic record generation; temporal encounter hierarchy is not explicitly modeled.

### Q6. What data do they use?
UCI heart disease (303 records, 14 variables), UCI diabetes (47 features over 1999-2008 encounters), and MIMIC-III diagnoses data (binary/count versions with high dimensionality).

### Q7. Do they handle multiple action types or just one?
`N/A` in RS-action terms.

### Q8. How do they handle discrete vs continuous outputs?
They support categorical and numerical health variables via Bayesian-network modeling, with preprocessing/discretization considerations for some continuous variables.

### Q9. How do they handle variable-length sequences?
They treat records as tabular rows and note limitations for repeated-encounter/temporal structure; dynamic Bayesian networks are suggested as future work.

### Q10. What conditioning do they use?
Conditioning follows Bayesian-network parent-child dependencies; variables are sampled in topological order conditioned on parent values.

### Q11. Do they mention training stability issues?
No GAN-style collapse issues; focus is on model fit, preprocessing sensitivity, and computational efficiency.

### Q12. How do they evaluate the quality of generated data?
They use statistical similarity tests (e.g., Kolmogorov-Smirnov), association-rule preservation, correlation-matrix comparisons, ML prediction parity, discriminator tests, and disclosure-risk analyses.

### Q13. Do they test downstream utility?
Yes: predictive modeling and association-rule analyses on synthetic vs real data are compared.

### Q14. What baseline do they compare against?
Primary baseline is medBGAN (and disclosure comparisons include medGAN references).

### Q15. What taxonomy/categories do they propose?
`N/A` formal taxonomy paper.

### Q16. What gaps or open problems do they identify?
Key limitations include handling temporal/hierarchical encounter data, continuous-variable preprocessing constraints, and scaling to very large/high-dimensional datasets.

### Q17. Do they mention transformers/autoregressive models?
No transformer focus.

## 9) Generation and Analysis of Synthetic Data via Bayesian Networks: A Robust Approach for Uncertainty Quantification via Bayesian Paradigm (Martins et al., 2024)

### Availability
Full text available via arXiv (`2402.17915`) and reviewed.

### Q1. What problem does this paper solve?
It addresses how to generate synthetic data with robust uncertainty quantification so analyses on synthetic data better reflect uncertainty in original-data inference.

### Q2. What method do they use?
A full Bayesian Bayesian-network approach: MCMC over network structures plus posterior predictive simulation of synthetic-data statistics with penalizing priors.

### Q3. How is this relevant to my thesis?
It is a modern Bayesian-network alternative emphasizing uncertainty-aware synthetic-data analysis, useful as contrast to GAN-style generators.

### Q4. How do they define an "interaction"?
`N/A` - they model tabular binary-variable relationships, not RS interaction events.

### Q5. Do they generate sequential sessions or independent events?
Independent tabular synthetic rows (static Bayesian-network setting).

### Q6. What data do they use?
Simulated binary-data scenarios (different variable counts/sample sizes) plus real PNAD 2023 household data (5 selected variables, 5,651 households).

### Q7. Do they handle multiple action types or just one?
`N/A` in RS-action sense.

### Q8. How do they handle discrete vs continuous outputs?
Current method is developed/tested for binary data; extensions to richer variable types are future work.

### Q9. How do they handle variable-length sequences?
`N/A` - not a sequence model.

### Q10. What conditioning do they use?
Sampling is conditioned by Bayesian-network parent sets and posterior uncertainty over graph/parameters.

### Q11. Do they mention training stability issues?
Not GAN-style. They discuss MCMC efficiency/chain settings and computational cost as practical concerns.

### Q12. How do they evaluate the quality of generated data?
They compare synthetic-vs-original analytical outputs using overlap of confidence intervals, MLE/p-value-based statistics, and uncertainty-interval behavior across methods.

### Q13. Do they test downstream utility?
Yes: core goal is preserving practical inferential analyses when only synthetic data are shared.

### Q14. What baseline do they compare against?
Two alternatives: (S2) top-posterior network + MLE with 5 synthetic sets combined, and (S3) synthpop/IPF generation.

### Q15. What taxonomy/categories do they propose?
`N/A` formal field taxonomy; method-level decomposition is provided (network posterior estimation, synthetic generation, predictive-statistics outputs).

### Q16. What gaps or open problems do they identify?
Future directions include multinomial/continuous/mixed data support, missing-data scenarios, and broader scalability.

### Q17. Do they mention transformers/autoregressive models?
No; this is a Bayesian-network/statistical paradigm paper.
