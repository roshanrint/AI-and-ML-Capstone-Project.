1. Overview

| Field         | Details                                                                                                                                                     |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Name**      | Adaptive Rule-Based Sequential Black-Box Optimiser                                                                                                          |
| **Type**      | Heuristic sequential optimisation strategy using magnitude-aware perturbation and dimension-sensitive refinement                                            |
| **Version**   | v10 (Week 10 / Module 21 – Final Iteration)                                                        |
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
