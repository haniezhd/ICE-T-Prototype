# SECTION 4 — Major Minimum Requirements

**Objective:**
For a given academic major in Iran, assign the minimum required competencies for students in both global/ideal and local/practical contexts, focusing primarily on critical traits for each major. Reduce the impact of irrelevant traits and adjust for routine vs specialized work.

**Input Format**

```json
{
  "Major_Name": "<string>",
  "Local_Context": {
    "Routine_Phase": "<yes/no>",
    "Specialized_Phase": "<yes/no>",
    "Socio_Economic_Conditions": "<urban/rural, average income, parental education, resource access>"
  }
}
```

**Step 1 — Identify Major-Critical Traits**
Automatically or manually determine the 3–5 most critical traits for the major (e.g., Creativity_Openness, Artistic, Social_Communication for Graphic).

Classify remaining traits as minor or auxiliary, which will have minimal influence on similarity.

**LMRs (Local Minimum Requirements):**

* Critical Traits: Moderate-high (6–8/10)
* Minor Traits: Low (3–5/10)

Caps can be applied to routine-heavy features if the job is mostly routine.

This ensures that students are scored primarily on what truly matters for success in that major.

**Step 2 — Assign Local Feature Weights**

* Critical Traits: High weight (0.20–0.30 each)
* Moderate Traits: Medium weight (0.10–0.15)
* Minor Traits: Low weight (0.05–0.10)

Ensure sum of weights = 1.

Weights reflect practical importance in local context (Iranian work routines, socio-economic conditions, and resource limitations).

This prevents irrelevant traits from inflating or diluting the similarity score.

**Step 3 — Adjust Scores for Routine vs Specialized Phases**

**Routine Phase:**

* Apply penalties to analytical, creative, or theoretical dimensions if tasks are repetitive.
* Cap values to avoid unrealistic scoring in routine-heavy areas.

**Specialized Phase:**

* Allow higher scores in critical traits, especially Creativity, Analytical_Thinking, and Theoretical_Orientation.

This provides realistic local adjustment while keeping major-critical traits dominant.

**Step 4 — Dynamic / LLM-Assisted Critical Trait Detection**
Optionally instruct the LLM to:

* Analyze the normal tasks of the major
* Detect which traits are most used
* Output these as the critical trait set

This allows automatic adaptation for different majors and avoids hardcoding.

**Step 5 — Output Format (JSON)**

```json
{
  "Major": "<Major_Name>",
  "Critical_Traits": ["Creativity_Openness", "Artistic", ...],
  "Ideal_Feature_Vector": {
    "Cognitive_Ability": x,
    "Conscientiousness": x,
    "Analytical_Thinking": x,
    "Creativity_Openness": x,
    "Social_Communication": x,
    "Interest_Alignment": x,
    "Stress_Tolerance": x,
    "Practical_Skills": x,
    "Theoretical_Orientation": x,
    "Motivation": x
  },
  "Local_Feature_Vector": {
    "Cognitive_Ability": x,
    "Conscientiousness": x,
    "Analytical_Thinking": x,
    "Creativity_Openness": x,
    "Social_Communication": x,
    "Interest_Alignment": x,
    "Stress_Tolerance": x,
    "Practical_Skills": x,
    "Theoretical_Orientation": x,
    "Motivation": x
  },
  "Local_Feature_Weights": {
    "Cognitive_Ability": w1,
    "Conscientiousness": w2,
    "Analytical_Thinking": w3,
    "Creativity_Openness": w4,
    "Social_Communication": w5,
    "Interest_Alignment": w6,
    "Stress_Tolerance": w7,
    "Practical_Skills": w8,
    "Theoretical_Orientation": w9,
    "Motivation": w10
  },
  "Justification_Notes": "Explain why certain features are capped or weighted lower due to routine-level practice or socio-economic limitations. Highlight specialized phases for critical features."
}
```

**Step 6 — Advantages**

* Focuses scoring on what truly matters (major-critical traits).
* Reduces dilution or inflation caused by irrelevant features.
* Adapts to local Iranian context (routine vs specialized, socio-economic factors).
* Dynamic critical-trait detection allows flexible deployment for multiple majors.
* Compatible with Section 5 (Similarity/Alignment) since weights and LMRs now reflect actual major importance.
