# SECTION 5 — Major Alignment / Similarity Scoring

**Objective:**
Calculate a student’s similarity to a given major using critical-major traits, local minimum requirements (LMRs), and dynamically weighted features. Minor traits have minimal impact, preventing irrelevant weaknesses from lowering similarity.

**Input Format**

```json
{
  "Student_Feature_Vector": {
    "Cognitive_Ability": x,
    "Conscientiousness": x,
    "Analytical_Thinking": x,
    "Creativity_Openness": x,
    "Social_Communication": x,
    "Interest_Alignment": x,
    "Stress_Tolerance": x,
    "Practical_Skills": x,
    "Theoretical_Orientation": x,
    "Motivation": x,
    "RIASEC_type": "<string>"
  },
  "Major_Minimums": {
    "Local_Feature_Vector": { ... },
    "Local_Feature_Weights": { ... },
    "Critical_Traits": ["Creativity_Openness", "Artistic", "Social_Communication"]
  }
}
```

**Step 1 — Compute Feature Match Ratios**
For each feature (i):

[
\text{MatchRatio}_i = \min\Big(1.0, \frac{\text{StudentFeature}_i}{\text{LMR}_i}\Big)
]

* StudentFeature_i = student’s value for feature i
* LMR_i = local minimum requirement from Section 4

This ensures a score of 1.0 is only achieved if the student meets or exceeds the LMR.

**Step 2 — Apply Hybrid Non-Linear Scaling**

* Critical and Moderate Features: keep linear scaling to reward excellence fully.
* Minor Features: apply square root scaling to dampen the contribution of non-critical traits.

[
\text{ScaledMatchRatio}_i =
\begin{cases}
\text{MatchRatio}_i & \text{if } i \in \text{Critical or Moderate} \
\sqrt{\text{MatchRatio}_i} & \text{if } i \in \text{Minor}
\end{cases}
]

This prevents irrelevant strengths from inflating similarity and ensures major-critical traits dominate.

**Step 3 — Weight by Feature Importance**
Multiply each scaled match ratio by the Local Feature Weight from Section 4:

[
\text{WeightedMatch}_i = \text{ScaledMatchRatio}_i \times \text{Weight}_i
]

* High weights for critical traits (0.20–0.30)
* Low weights for minor traits (0.05–0.10)

**Step 4 — Aggregate Weighted Score**
Sum all weighted matches to compute a similarity percentage:

[
\text{Similarity} = 100 \times \sum_{i=1}^{10} \text{WeightedMatch}_i
]

* Max score = 100
* Dominated by performance on critical traits
* Minor traits influence score minimally

**Step 5 — Optional Enhancements**

* Slack Factor: multiply minor features by 0.8 to further reduce noise.
* Custom Caps: for routine-heavy features, prevent unrealistic high contributions.
* RIASEC Check: optionally add small bonus if student RIASEC type matches major’s dominant type.

**Step 6 — Output Format**

```json
{
  "Similarity_Percentage": 0-100,
  "Critical_Traits_Match": {
    "Creativity_Openness": 0-1,
    "Artistic": 0-1,
    "Social_Communication": 0-1
  },
  "Minor_Traits_Match": {
    "Cognitive_Ability": 0-1,
    "Conscientiousness": 0-1,
    ...
  },
  "Justification": "Critical traits dominate the similarity. Minor traits contribute minimally. Non-linear scaling applied to minor traits to prevent score inflation."
}
```
