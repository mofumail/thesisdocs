Highlights

    •
    A novel synthetic data stream generator (GIDS) was developed.
    •
    Use for evaluation of incremental recommender systems and data fusion algorithms.
    •
    Resembles real datasets in terms of data properties and recommender performance.
    •
    Tunable parameters allow for systematic generation of streams for various problems.

Abstract
Recommender systems are essential tools in modern e-commerce, streaming services, search engines, social networks and many other areas including the scientific community. However, lack of publicly available data hinders the development and evaluation of recommender algorithms. To address this problem, we propose a Generator of Inter-dependent Data Streams (GIDS), capable of generating multiple temporal and inter-dependent synthetic datasets of relational data. The generator is able to simulate a collection of time-changing data streams, helping to effectively evaluate a variety of recommender systems, data fusion algorithms and incremental algorithms. The evaluation using recommender and data fusion algorithms showed that our generator can successfully mimic real datasets in terms of statistical data properties, and achieved performance of recommender systems.
Introduction
Evaluating and comparing recommender algorithms is inherently difficult [1], since algorithm performance depends on the properties of the datasets used for learning and evaluation. The datasets may contain a varying number of users and items, rating sparsity, different rating scales and other unique data properties. To properly test these algorithms, we therefore need many different and specialized datasets. However, the amount and diversity of publicly available data for recommender systems remains limited [2]. This problem gets worse when we try to collect multiple related datasets from the same domain with meaningful connections between the datasets (such as movies and actors, holiday destinations and weather, etc.), or when we search for temporal dependencies and patterns in the datasets.
Synthetic data generators (SDG) can help us alleviate this problem by generating test-specific datasets for development and evaluation of numerous algorithms. Synthetic data can serve as an algorithm benchmark or can be used to test the algorithm’s robustness on specific edge cases. If the generated data were not produced by a static distribution or a process, i.e., data distribution is affected by time, we can represent such dataset as a data stream. In such cases, synthetic data streams could help to evaluate existing and develop incremental streaming algorithms.
In this paper, we present a novel synthetic Generator of Inter-dependent Data Streams – GIDS. The generator can artificially generate a collection of multiple inter-connected relational datasets in a matrix form, alongside with time dependency component in a form of relation timestamps that can afterwards be used for simulation of data streams. GIDS can also simulate various concept drifts in data and its set of tunable parameters allows systematic generation of specific datasets for testing distinct algorithm properties.
GIDS works by simulating multiple sets of clusters (groups of objects) of different object types and connections (relations) between those clusters. In this way, GIDS mimics real-life problems where one can observe such structure; such as in collaborative filtering, where users receive recommendations for items that users with similar taste and preferences (e.g., users within the same cluster) liked in the past. Collections of such generated datasets allow effective evaluation of recommender systems and data fusion algorithms. We evaluate our approach by generating multiple datasets (and data streams) and compare them to real datasets by using static and dynamic recommender systems and data fusion algorithms.
This paper is organized as follows. In Section 2 we overview the related work on synthetic data generators, focusing mainly on those used for generating datasets for recommender systems. We present our synthetic data generator in Section 3 and evaluate it in Section 4. In Section 5 we conclude the paper with directions for future work.
Access through your organization

Check access to the full text by signing in through your organization.
Section snippets
Related work
Machine learning problems often face a lack of sufficient data. This can arise due to the natural rarity of the data itself, difficult or expensive experiments, privacy concerns, uneven distribution of samples, etc. Several synthetic data generators have already been proposed for various problems in data mining and machine learning, such as: generating transaction data [3], filling databases [4], clustering [5], bioinformatics [6] and other general purpose data generators [7], [8].
For
Generating multiple inter-dependent data streams
When designing the data stream generator GIDS, our main goal was to mimic relevant properties that are present in real datasets:

    ○ realistic relations between groups of different entities (e.g., a realistic pattern of user ratings),
    ○ hidden correlations between multiple datasets (a common dimension in a set of multiple relations, e.g., when same users rate different entities: movies, songs, restaurants, etc.),
    ○ real data distribution (distributions of rating values and number of ratings per row

Evaluation
Our main goal was to create a synthetic data generator that is able to create multiple inter-dependent datasets that resemble real-life problems in order to design a realistic benchmark for algorithm development and testing. To evaluate our approach, we designed a special set of experiments that test our objectives (listed in Section 3). For a performance baseline we include a basic synthetic data generator (denoted with Random) that randomly generates quadruplets {user, item, rating, timestamp
Conclusion
Scarcity and lack in diversity of public available datasets for recommender systems make development and evaluation of such algorithms a difficult and challenging task. In this paper, we have presented a methodology for generating multiple inter-dependent data streams for evaluating (incremental or time-aware) recommender systems.
The proposed GIDS algorithm works by creating object clusters that are inter-connected and creates a clear structure in the data, mimicking properties of real data.
