# ICE-T Prototype Results

**Note:** The prototype was tested on several students who were dissatisfied with their current majors. Below are the alignment results computed using the prompts from Sections 1–5. Each JSON represents one student, showing critical and minor trait matches, similarity percentage, and justification.

---

## Subject 1

```json
{
  "Similarity_Percentage": 17.2,
  "Critical_Traits_Match": {
    "Stress_Tolerance": 0.105,
    "Social_Communication": 0.144,
    "Practical_Skills": 0.134
  },
  "Minor_Traits_Match": {
    "Creativity_Openness": 0.597,
    "Interest_Alignment": 0.616,
    "Cognitive_Ability": 0.167,
    "Conscientiousness": 0.165,
    "Analytical_Thinking": 0.204,
    "Theoretical_Orientation": 0.206,
    "Motivation": 0.160
  },
  "Justification": "The student’s strongest traits are in creativity and interest alignment, but critical traits for this major — stress tolerance, social communication, and practical skills — are weak relative to local minimum requirements. Minor traits were dampened to avoid inflating similarity. The resulting low similarity reflects a significant mismatch with the major’s critical competencies."
}
```

---

## Subject 2

```json
{
  "Similarity_Percentage": 20.8,
  "Critical_Traits_Match": {
    "Cognitive_Ability": 0.144,
    "Conscientiousness": 0.153,
    "Analytical_Thinking": 0.147,
    "Theoretical_Orientation": 0.170,
    "Learning_Motivation": 0.139
  },
  "Minor_Traits_Match": {
    "Creativity_Openness": 0.204,
    "Practical_Skills": 0.196,
    "Stress_Tolerance": 0.208,
    "Social_Communication": 0.487,
    "Interest_Alignment": 0.463
  },
  "Justification": "The student shows moderate alignment in cognitive and analytical traits, but critical competencies required by the major remain underdeveloped. Minor traits contribute slightly more due to scaling adjustments, but their local weights are low. Overall, the student’s profile does not meet the majority of the major’s critical requirements, resulting in a low similarity score."
}
```

---

## Subject 3

```json
{
  "Similarity_Percentage": 15.04,
  "Critical_Traits_Match": {
    "Social_Communication": 0.121,
    "Practical_Skills": 0.115,
    "Stress_Tolerance": 0.105
  },
  "Minor_Traits_Match": {
    "Cognitive_Ability": 0.158,
    "Conscientiousness": 0.163,
    "Analytical_Thinking": 0.157,
    "Creativity_Openness": 0.505,
    "Interest_Alignment": 0.000,
    "Theoretical_Orientation": 0.160,
    "Motivation": 0.159
  },
  "Justification": "The student exhibits strengths in creativity and conscientiousness, but fails to meet the major’s highest-weighted critical traits: social communication, practical skills, and stress tolerance. Minor traits were scaled to avoid overestimating contribution. The final similarity indicates a substantial gap between the student’s abilities and the major’s key requirements."
}
```
