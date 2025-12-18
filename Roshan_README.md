# AI-and-ML-Capstone-Project.
This is a repository for my capstone project being developed as part of the Professional Certificate program in Machine Learning and Artificial Intelligence at Imperial College London.



Project Overview
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


Challenge Objectives
Goal: Maximize the output of each unknown function with a limited number of queries.

Constraints:

Function structures are unknown (nonlinear, possibly high-dimensional).

Each function can only be queried a limited number of times.

Queries must be carefully selected to balance exploration (covering unobserved regions) and exploitation (refining promising regions).

The project emphasizes learning the function landscape iteratively, making informed decisions based on limited prior data.


Technical Approach
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

Summary:
The BBO Capstone Project offers hands-on experience in strategic experimentation, iterative learning, and optimizing unknown systems with limited information. Over three rounds, the strategy progressed from evenly covering the space to exploring based on observed outputs, and finally to focused, model-driven optimization, showcasing real-world applications of machine learning and decision-making under uncertainty.
