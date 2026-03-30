# AI-and-ML-Capstone-Project.
This is a repository for my capstone project being developed as part of the Professional Certificate program in Machine Learning and Artificial Intelligence at Imperial College London.



# Project Overview
The BBO Capstone Project focuses on optimizing complex, high-dimensional functions whose inner workings are hidden. The main objective is to choose input queries that explore the function effectively and pinpoint high-performing areas while using as few evaluations as possible. This mirrors real-world situations in machine learning and engineering, where testing functions can be expensive, slow, or risky.

Taking part in this project builds key abilities in iterative modeling, handling uncertainty, and making decisions with incomplete information. These skills are highly valuable for careers in data science, optimization, and AI research, where planning experiments and improving performance with limited resources is often crucial.

Inputs and Outputs
Inputs:

Vary by function, ranging from 2D to 8D input vectors.

Input values are continuous and constrained within [0,1].

Queries are formatted to six decimal places.

Example input formats:

Function 1 (2D): [0.847231, 0.153924]

Function 8 (8D): [0.850111, 0.200222, 0.750333, 0.900444, 0.150555, 0.650666, 0.300777, 0.800888]

Outputs:

Scalar performance values indicating the function response at the queried input.

Values can vary widely, from near zero to very large magnitudes, reflecting diverse function behavior.

Example outputs:

Function 1: 1.41e-177

Function 5: 2.71


# Challenge Objectives
Goal: Maximize the output of each unknown function with a limited number of queries.

Constraints:

Function structures are unknown (nonlinear, possibly high-dimensional).

Each function can only be queried a limited number of times.

Queries must be carefully selected to balance exploration (covering unobserved regions) and exploitation (refining promising regions).

The project emphasizes learning the function landscape iteratively, making informed decisions based on limited prior data.


# Technical Approach
Week 1 – Foundational Exploration
Selected query points to evenly cover the input space and avoid clustering.

Focused on high-dimensional coverage (Functions 6–8) to build a diverse dataset.

Strategy prioritized exploration over immediate exploitation due to minimal prior knowledge.

Week 2 – Guided Exploration Based on Early Signals
Began incorporating output information from initial queries.

Explored distant areas to reduce model uncertainty and detect regions with high potential.

Considered qualitative feature effects, e.g., swapping high and low input values to assess their impact on function outputs.

Recognized limitations for linear/logistic models due to nonlinearity, variance differences, and small sample sizes.

Week 3 – Targeted, Model-Guided Queries
Shifted toward balancing exploitation with exploration.

For high-performing functions (e.g., Functions 5, 7, 8), refined queries locally around promising points.

For low-performing functions (e.g., Functions 1, 4), explored new regions to gather informative data.

Potential use of SVMs:

Soft-margin SVMs to separate high- vs low-performance regions.

Kernel methods (e.g., RBF) for capturing nonlinear relationships.

Highlighted risk of overfitting in high-dimensional functions and importance of feature selection or regularization in surrogate models.

Overall Strategy:
Continuously refine the process for selecting queries based on observed results, thoughtfully balancing exploration and exploitation. This method enhances efficiency, clarity, and flexibility, capturing the typical challenges found in real-world black-box optimization.

# Summary:
The BBO Capstone Project offers hands-on experience in strategic experimentation, iterative learning, and optimizing unknown systems with limited information. Over three rounds, the strategy progressed from evenly covering the space to exploring based on observed outputs, and finally to focused, model-driven optimization, showcasing real-world applications of machine learning and decision-making under uncertainty.


This project explores black-box function optimisation across thirteen iterative rounds. Each week involved selecting input queries, observing outputs, and refining strategies based on accumulated data. Early iterations emphasised exploration of the input space, while later stages shifted toward exploitation, clustering, and local refinement around high-performing regions. Techniques inspired by scaling laws, principal component analysis, and reinforcement learning guided decision-making. The final approach balances exploration and exploitation, using feedback signals to improve subsequent queries. The analysis highlights emergent behaviour, convergence patterns, and sensitivity to input variations. Overall, the project demonstrates an adaptive, data-driven optimisation process applied to unknown functions effectively implemented.


# Conclusion

Across Weeks 1–13, this capstone project demonstrates a complete and progressive approach to black-box optimisation, evolving from uninformed exploration to structured, feedback-driven exploitation. In the early weeks, the absence of prior knowledge necessitated broad, largely random sampling to build an initial understanding of how each function responded to changes in input variables. As observations accumulated, patterns began to emerge, enabling more informed query selection and a gradual shift toward targeted search in promising regions of the input space.

From Weeks 4–6 onward, optimisation became increasingly guided by empirical trends, with iterative adjustments informed by previous outputs. This phase marked the transition from exploration-heavy strategies to a more balanced exploration–exploitation framework. Scaling effects and diminishing returns became apparent, highlighting that certain regions of the input space yielded consistently stronger outputs while others showed limited sensitivity. These insights allowed for more efficient allocation of queries, focusing computational effort where it was most likely to produce meaningful gains.

In Weeks 7–9, the strategy incorporated considerations of scaling laws and emergent behaviour. Small perturbations around high-performing inputs were used to probe local stability and uncover potential non-linearities. At the same time, awareness of unexpected output spikes reinforced the importance of maintaining some level of exploration to avoid missing regions of hidden performance. This stage reflects a more mature optimisation mindset, where both risk and opportunity are explicitly considered when designing queries.

Weeks 10–11 introduced a stronger emphasis on interpretability and structure. Functions were analysed in terms of output magnitude, directional trends, and clustering behaviour in the input space. This allowed for classification of regions into high-value basins, near-zero stable zones, and underperforming areas. The optimisation process became more systematic, with input adjustments informed by clearly defined heuristics rather than ad hoc decisions. Concepts analogous to dimensionality reduction and clustering helped prioritise variables and regions that had the greatest impact on outputs.

By Week 12, the strategy had converged further toward exploiting known promising regions while maintaining controlled local exploration. Insights inspired by principal component analysis helped identify key drivers of variation, suggesting that not all input dimensions contributed equally to output changes. This led to a more efficient search strategy, where effort was concentrated on influential variables while less impactful dimensions were held relatively stable. The result was a more focused and data-efficient optimisation process.

In the final week, the project framed the optimisation problem through the lens of reinforcement learning. Each function output was treated as a reward signal, guiding iterative updates to the query strategy. Positive outputs reinforced nearby regions, encouraging further exploitation, while negative outputs discouraged revisiting unproductive areas. This feedback loop mirrors policy improvement in reinforcement learning, where decisions are continuously refined based on accumulated experience. The balance between exploration and exploitation became an explicit policy choice rather than an implicit behaviour.

Overall, the progression across all thirteen weeks illustrates a coherent evolution from random search to principled, feedback-driven optimisation. The methodology integrates concepts from scaling laws, clustering, dimensionality reduction, and reinforcement learning to construct a robust and adaptive querying strategy. Key limitations, including potential local optima and sampling bias toward previously explored regions, were acknowledged and mitigated through controlled perturbations and occasional exploration. The final outcome is a structured and interpretable optimisation approach that effectively balances efficiency, robustness, and adaptability when working with unknown black-box functions.



