# ICE-T: Intelligent Career and Education Tool (Prototype)

ICE-T (Intelligent Career and Education Tool) is an AI-driven framework for personalized academic and career guidance. It uses student demographics, psychometrics, motivation, and practical constraints to evaluate alignment with academic majors.

**Key Features:**

* Converts raw student responses into 10-dimensional feature vectors.
* Generates ideal and locally adjusted major requirement vectors.
* Calculates weighted, critical-trait–dominant similarity scores.
* Produces JSON outputs with feature vectors, similarity scores, and match classifications.

**Note:** This prototype does not use learned weights, so similarity percentages are illustrative and not statistically validated. However, the explanations, critical-trait reasoning, and justifications for alignment remain meaningful and useful for guidance purposes.

**Repository Structure:**

```
/prompts
    ├─ CSV_to_JSON_prompt.md
    ├─ personal_feature_vectorization_prompt.md
    ├─ major_minimum_requirements_prompt.md
    ├─ match_scoring_prompt.md

/datasets
    └─ sample_student_data.csv

/results
    └─ final_alignment_results.md

README.md
```

**Usage:** Process prompts section by section for best accuracy: CSV → JSON → feature vector → major requirements → alignment scoring.

ICE-T is fully LLM-driven and requires no code execution, enabling rapid exploration of student-major fit and personalized guidance.
