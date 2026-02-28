1. Motivation

This dataset was created as part of a ten-week Black-Box Optimisation (BBO) capstone project in which I sequentially queried eight unknown benchmark functions of varying dimensionality. The purpose of generating and documenting this dataset was not simply to improve function outputs over time, but to create a transparent and traceable record of how optimisation decisions were made under uncertainty.
Because black-box optimisation problems do not reveal internal structure, all decision-making must be based solely on observed input–output behaviour. For that reason, documenting the full query history is essential. Without this record, it would be impossible to evaluate whether performance improvements resulted from systematic reasoning, random chance, or implicit bias in sampling.

This dataset supports:
Analysis of exploration versus exploitation behaviour over time
Reflection on heuristic-based optimisation strategies
Evaluation of decision consistency across multiple functions
Reproducibility of optimisation reasoning
In short, the dataset is not merely a record of results; it is a record of the decision-making process itself.



2. Composition
   
The dataset consists of 80 total query–evaluation pairs collected over 10 weeks. Each week, I submitted one input vector for each of the eight functions, and the system returned a corresponding scalar output value.

Each entry in the dataset includes:
Week number
Function identifier (1–8)
Input vector (with dimensionality depending on function)
Output value returned by the evaluation system

The dimensionality of the functions ranges from 2D to 8D. This variation significantly influences optimisation difficulty, as higher-dimensional spaces expand exponentially in volume. With only 10 queries per function, coverage of the 8D input space is extremely sparse. Therefore, the dataset reflects a constrained sampling regime, which places strong emphasis on strategic decision-making rather than exhaustive search.

One notable characteristic of the dataset is the wide range of output magnitudes. Some functions (e.g., Function 1) consistently returned extremely small values close to numerical zero, suggesting either a sharp basin or underflow-like behaviour. In contrast, Function 5 exhibited dramatic growth in output values in later weeks, increasing from double-digit values to over 3000. This variation indicates that the underlying functions likely differ significantly in curvature, smoothness, and scaling behaviour.

There are no missing values in the dataset. However, there is an inherent structural limitation: each function is evaluated only once per week. This means the dataset does not include parallel comparisons or repeated trials, and therefore does not support statistical variance estimation.


| Function | Dimensionality | Observed Behaviour                            |
| -------- | -------------- | --------------------------------------------- |
| 1        | 2D             | Extremely small magnitudes (≈10⁻²²⁹ to 10⁻²⁸) |
| 2        | 2D             | Mild positive/negative fluctuation            |
| 3        | 3D             | Stable negative region                        |
| 4        | 4D             | Strong negative basin                         |
| 5        | 4D             | Rapid positive escalation                     |
| 6        | 5D             | Moderate negative plateau                     |
| 7        | 6D             | Small positive fluctuations                   |
| 8        | 8D             | Gradual upward trend                          |




3. Collection Process
   
The dataset was collected sequentially across ten weeks. Each week’s submission was informed by all prior observed outputs, meaning the collection process was adaptive rather than independent.

Weeks 1–2: Structured Exploration
In the first two weeks, I prioritised broad exploration of the input space. Because no performance signals were yet available, the goal was to avoid clustering and instead distribute values across different regions. This approach aimed to establish baseline behaviour patterns for each function.
At this stage, decision-making was cautious and evenly distributed rather than targeted. The primary objective was to gather signal, not maximise performance.

Weeks 3–5: Local Sensitivity Testing
After observing output variability, I began introducing small perturbations around previously promising inputs. The rationale behind this shift was the assumption that the functions exhibit some degree of local smoothness, meaning nearby inputs would produce related outputs.
This stage marked the beginning of exploitation behaviour. However, exploration was not abandoned entirely. For functions showing strongly negative or unstable outputs, I introduced broader shifts to avoid becoming trapped in potentially unproductive regions.

Weeks 6–7: Dimensional Prioritisation
By mid-project, patterns began to emerge suggesting that certain dimensions might influence outputs more strongly than others. Rather than adjusting all dimensions uniformly, I began selectively modifying specific coordinates while holding others relatively stable.
This reflected a transition from uniform perturbation to sensitivity-based refinement. Although this was heuristic rather than statistically validated, it represented an attempt to introduce structure into the search process.

Weeks 8–9: Controlled Diversity and Prompt Structuring
In later weeks, I focused on maintaining diversity while ensuring syntactic and dimensional correctness. I consciously controlled how much variation to introduce, balancing stability against the need to escape plateaus.
At this stage, I became more attentive to emergent behaviours, such as sudden output jumps or stagnation. When significant changes occurred, I interpreted them as signals of underlying curvature or threshold effects.

Week 10: Explicit Rule Formalisation
In the final week, I consolidated my strategy into an explicit rule-based framework. Instead of relying on intuition alone, I classified each function’s previous output into categories (near-zero, strongly positive, strongly negative) and adjusted step sizes accordingly.

This formalisation improved transparency. Rather than implicitly adjusting perturbation magnitude, I made the scaling logic explicit. This shift enhances reproducibility, as another person could follow the same magnitude-based rules.



4. Preprocessing and Transformations

No preprocessing was applied to the dataset. All output values are recorded exactly as returned by the evaluation system. No smoothing, scaling, normalisation, or filtering was performed.
This decision was intentional. Applying transformations would risk obscuring the raw behaviour of the functions and potentially biasing interpretation. Preserving original values ensures the dataset remains faithful to the optimisation environment.

5. Intended and Inappropriate Uses

Intended Uses
This dataset is intended for:
Studying adaptive optimisation behaviour
Analysing sequential decision-making
Evaluating exploration–exploitation dynamics
Teaching transparency in ML experimentation
Because it records the full trajectory of optimisation, it can be used to analyse how reasoning evolves under constraints.


Inappropriate Uses
This dataset should not be used to:
Claim discovery of global optima
Benchmark against large-scale optimisation algorithms
Perform statistical hypothesis testing
Generalise findings beyond this specific evaluation setup
The small sample size per function and absence of repeated trials limit inferential strength.


6. Distribution and Maintenance

The dataset is stored in my public GitHub repository for the BBO capstone project. It is distributed for academic purposes and transparency. No personal or sensitive data is included.
Maintenance responsibility lies with the repository owner. Since the project is complete, the dataset is static and will not be expanded further.
