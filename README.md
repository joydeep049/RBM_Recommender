# Recommendation Using Restricted Boltzmann Machine 

Restricted Boltzmann Machines are stochastic neural networks which focuses on learning the underlying probability distribution. It uses a set of Visible and Hidden nodes. It is based on energy minimisation across a set of nodes. Add Stochasticity and Hidden nodes to a Hopfield Network, and you would get a Restricted Boltzmann Machine.

The `Restricted` part of RBMs come from the fact that the Pairwise interactions are only allowed within a set of observable and unobservable states. The visible layer or the hidden layers do not have recurrent connections within them, nor are they self connected. This property makes the algorithm able to always reach convergence, also making it possible for RBMs to be trained by efficient optimisation algorithms like `contrastive divergence`.

Hopfield networks memorise the data, and hence cannot be used for recommendation purposes. 

Link to the collab notebook : [RBM_Recommender.ipynb](https://colab.research.google.com/drive/1IFz5Tce-YNW_NYZqYgmT2IH7KtjHSZSW?usp=drive_link)

## Scoring System Analysis

Approach:

1. Match Interests: Study materials that align with the student’s interests will receive a higher score.
2. Match Course: If the material subject is related to the student's course, the material will also get a higher score.
3. Quiz Performance: Higher average quiz scores could indicate that the student is more capable of handling harder study materials.
4. Past Engagement: If the student has viewed certain materials, those materials will not be recommended again.

## Synthetic Data Used

Student Table 

| student_id | name          | course                    | year | avg_quiz_score | interests                      |
|------------|---------------|---------------------------|------|-----------------|--------------------------------|
| 1          | John Doe     | Computer Science          | 3    | 78              | AI, Blockchain                 |
| 2          | Jane Smith   | Mechanical Engineering     | 2    | 65              | Environmental Science, AI      |
| 3          | Sam Lee      | Civil Engineering         | 4    | 85              | Sustainability, Data Science   |
| 4          | Alex Chen    | Computer Science          | 1    | 55              | AI, Fintech                    |
| 5          | Maria Perez  | Electrical Engineering     | 3    | 70              | Robotics, Blockchain           |
| 6          | Tom White    | Physics                   | 2    | 63              | Quantum Computing, Physics     |
| 7          | Sophia Brown  | Biology                   | 4    | 88              | Biotechnology, Data Science    |
| 8          | Liam Green   | Mathematics               | 1    | 57              | Mathematics, AI                |
| 9          | Olivia Black  | Cybersecurity             | 3    | 74              | Cybersecurity, IoT            |
| 10         | Emma Gray    | Mechanical Engineering     | 2    | 68              | Mechanical Engineering, Robotics|

Material Table 

| material_id | subject                 | difficulty_level | popularity_score | content_length |
|-------------|-------------------------|------------------|------------------|-----------------|
| 101         | AI                      | Medium           | 65.3             | 15.2            |
| 102         | Blockchain              | Hard             | 72.5             | 22.6            |
| 103         | Sustainability          | Medium           | 88.7             | 35.1            |
| 104         | Robotics                | Hard             | 91.4             | 27.8            |
| 105         | Environmental Science    | Easy             | 79.2             | 33.4            |
| 106         | Data Science            | Hard             | 86.1             | 12.3            |
| 107         | Cybersecurity           | Medium           | 73.4             | 30.5            |
| 108         | Physics                 | Hard             | 67.8             | 28.9            |
| 109         | Mathematics             | Medium           | 94.5             | 14.8            |
| 110         | Chemistry               | Hard             | 60.2             | 37.2            |
| 111         | Astronomy               | Hard             | 77.1             | 18.9            |
| 112         | Quantum Computing        | Medium           | 82.9             | 24.6            |
| 113         | Biotechnology           | Medium           | 68.4             | 10.5            |
| 114         | Machine Learning        | Medium           | 90.0             | 20.1            |
| 115         | Renewable Energy        | Hard             | 84.3             | 36.4            |
| 116         | Ethics in AI           | Hard             | 78.8             | 19.8            |
| 117         | Web Development         | Medium           | 92.7             | 12.7            |
| 118         | Embedded Systems        | Easy             | 63.5             | 31.5            |
| 119         | IoT                     | Hard             | 70.1             | 25.9            |
| 120         | Cloud Computing         | Easy             | 89.6             | 11.4            |


Engagement Table 

| student_id | material_id | rating | viewed |
|------------|-------------|--------|--------|
| 1          | 101         | 4      | Y      |
| 2          | 102         | 5      | N      |
| 3          | 103         | 3      | Y      |
| 4          | 104         | 4      | Y      |
| 5          | 105         | 5      | N      |
| 6          | 106         | 2      | Y      |
| 7          | 107         | 3      | Y      |
| 8          | 108         | 5      | N      |
| 9          | 109         | 4      | Y      |
| 10         | 110         | 4      | Y      |
| 1          | 111         | 3      | N      |
| 2          | 112         | 5      | Y      |
| 3          | 113         | 2      | Y      |
| 4          | 114         | 4      | Y      |
| 5          | 115         | 3      | N      |
| 6          | 116         | 5      | Y      |
| 7          | 117         | 2      | Y      |
| 8          | 118         | 4      | N      |
| 9          | 119         | 4      | Y      |
| 10         | 120         | 5      | Y      |
| 1          | 101         | 2      | Y      |
| 2          | 102         | 3      | N      |
| 3          | 103         | 5      | Y      |
| 4          | 104         | 4      | Y      |
| 5          | 105         | 3      | N      |
| 6          | 106         | 2      | Y      |
| 7          | 107         | 4      | Y      |
| 8          | 108         | 5      | N      |
| 9          | 109         | 3      | Y      |
| 10         | 110         | 2      | Y      |


## Motivation

I could have simply built a recommender system using collaborative or content filtering. But this small work is my way of paying a tribute to `Geoffrey Hinton` and `John Hopfield`. 

The RBM is the perfect way to do that. The limitations of the Hopfield Networks led to the development of probabilistic models like RBMs. Also, Geoffrey Hinton has a paper where he explains how to use RBMs for building a recommendation system.

## Whats Next?

I plan to write my own implementation of a RBM. So stay tuned for that!
