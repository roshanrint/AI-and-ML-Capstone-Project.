1. Overview

| Field         | Details                                                                                                                                                     |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Name**      | Adaptive Rule-Based Sequential Black-Box Optimiser                                                                                                          |
| **Type**      | Heuristic sequential optimisation strategy using magnitude-aware perturbation and dimension-sensitive refinement                                            |                                                 |
| **Framework** | Deterministic rule-based search with structured perturbation logic (no external surrogate training framework)                                               


2. Intended Use

This optimisation approach is suitable for small-budget black-box problems where:
The number of evaluations is strictly limited
Function gradients are unavailable
Sequential reasoning is allowed

It is particularly appropriate in educational settings where understanding decision evolution is more important than achieving absolute optimality.

However, this approach should not be used in:
High-dimensional optimisation requiring robust global guarantees
Noisy environments where single evaluations are unreliable
Large-scale industrial optimisation requiring statistical validation
Its heuristic nature limits reliability in highly complex landscapes.


3. Strategy Evolution

The strategy developed in stages.
Initially, exploration dominated. Without prior knowledge, sampling needed to be broad enough to detect basic behaviour patterns.
As outputs accumulated, I shifted toward local refinement. Small perturbations were introduced under the assumption that nearby points might improve performance.
Midway through the project, I began noticing that not all dimensions appeared equally influential. This led to selective adjustment of certain coordinates. Although this was based on observation rather than formal sensitivity analysis, it represented a move toward structured reasoning.
In the final stage, I formalised step sizes based on output magnitude. For large positive outputs, I applied smaller refinements to avoid overshooting potential peaks. For strongly negative outputs, I applied broader shifts to escape poor regions. Near-zero outputs were treated diagnostically, with micro-adjustments used to test curvature.
This evolution reflects a progression from intuitive exploration to transparent rule-based adaptation.


4. Performance Summary

Performance varied across functions.
Function 5 demonstrated the most dramatic improvement, with outputs increasing significantly in later rounds. This suggests that the strategy successfully entered a high-reward region and refined around it.
Function 8 showed gradual, steady improvement, indicating a smoother landscape.
Higher-dimensional functions showed slower progress, likely due to sparse sampling relative to search-space volume.
Performance was measured solely using raw output magnitude, as no alternative evaluation metrics were provided.


5. Assumptions and Limitations

The strategy assumes:
Local smoothness in function behaviour
Deterministic outputs
Meaningful correlation between nearby points

If these assumptions do not hold, the approach may fail. For example, in highly multimodal landscapes with narrow peaks, limited sampling could miss optimal regions entirely.

Additionally, because the approach does not model uncertainty or maintain probabilistic beliefs, it cannot quantify confidence in its decisions.


6. Ethical and Transparency Considerations

By documenting both dataset structure and decision logic, this project promotes transparency and reproducibility. Clearly stating assumptions and limitations prevents overclaiming performance and ensures responsible reporting.
Transparency also allows others to critique, replicate, or improve the strategy. In real-world applications, such openness supports trust and iterative refinement.


# Reflection

This project explores black-box function optimisation across thirteen iterative rounds. Each week involved selecting input queries, observing outputs, and refining strategies based on accumulated data. Early iterations emphasised exploration of the input space, while later stages shifted toward exploitation, clustering, and local refinement around high-performing regions. Techniques inspired by scaling laws, principal component analysis, and reinforcement learning guided decision-making. The final approach balances exploration and exploitation, using feedback signals to improve subsequent queries. The analysis highlights emergent behaviour, convergence patterns, and sensitivity to input variations. Overall, the project demonstrates an adaptive, data-driven optimisation process applied to unknown functions effectively implemented.


# Conclusion

Across Weeks 1–13, this capstone project demonstrates a complete and progressive approach to black-box optimisation, evolving from uninformed exploration to structured, feedback-driven exploitation. In the early weeks, the absence of prior knowledge necessitated broad, largely random sampling to build an initial understanding of how each function responded to changes in input variables. As observations accumulated, patterns began to emerge, enabling more informed query selection and a gradual shift toward targeted search in promising regions of the input space.

From Weeks 4–6 onward, optimisation became increasingly guided by empirical trends, with iterative adjustments informed by previous outputs. This phase marked the transition from exploration-heavy strategies to a more balanced exploration–exploitation framework. Scaling effects and diminishing returns became apparent, highlighting that certain regions of the input space yielded consistently stronger outputs while others showed limited sensitivity. These insights allowed for more efficient allocation of queries, focusing computational effort where it was most likely to produce meaningful gains.

In Weeks 7–9, the strategy incorporated considerations of scaling laws and emergent behaviour. Small perturbations around high-performing inputs were used to probe local stability and uncover potential non-linearities. At the same time, awareness of unexpected output spikes reinforced the importance of maintaining some level of exploration to avoid missing regions of hidden performance. This stage reflects a more mature optimisation mindset, where both risk and opportunity are explicitly considered when designing queries.

Weeks 10–11 introduced a stronger emphasis on interpretability and structure. Functions were analysed in terms of output magnitude, directional trends, and clustering behaviour in the input space. This allowed for classification of regions into high-value basins, near-zero stable zones, and underperforming areas. The optimisation process became more systematic, with input adjustments informed by clearly defined heuristics rather than ad hoc decisions. Concepts analogous to dimensionality reduction and clustering helped prioritise variables and regions that had the greatest impact on outputs.

By Week 12, the strategy had converged further toward exploiting known promising regions while maintaining controlled local exploration. Insights inspired by principal component analysis helped identify key drivers of variation, suggesting that not all input dimensions contributed equally to output changes. This led to a more efficient search strategy, where effort was concentrated on influential variables while less impactful dimensions were held relatively stable. The result was a more focused and data-efficient optimisation process.

In the final week, the project framed the optimisation problem through the lens of reinforcement learning. Each function output was treated as a reward signal, guiding iterative updates to the query strategy. Positive outputs reinforced nearby regions, encouraging further exploitation, while negative outputs discouraged revisiting unproductive areas. This feedback loop mirrors policy improvement in reinforcement learning, where decisions are continuously refined based on accumulated experience. The balance between exploration and exploitation became an explicit policy choice rather than an implicit behaviour.

Overall, the progression across all thirteen weeks illustrates a coherent evolution from random search to principled, feedback-driven optimisation. The methodology integrates concepts from scaling laws, clustering, dimensionality reduction, and reinforcement learning to construct a robust and adaptive querying strategy. Key limitations, including potential local optima and sampling bias toward previously explored regions, were acknowledged and mitigated through controlled perturbations and occasional exploration. The final outcome is a structured and interpretable optimisation approach that effectively balances efficiency, robustness, and adaptability when working with unknown black-box functions.
