# **SECTION 3 — 10-Dimensional Feature Vector Conversion**

**Objective:**
Convert a student’s raw trait scores into a **10-dimensional proportional personal feature vector** representing cognitive, social, creative, practical, and motivational traits. Output values are **normalized to sum to 1**. Include the `RIASEC_type` string for reference.

### **Input Format**

```json
{
  "Openness": <0-5>,
  "Conscientiousness": <0-5>,
  "Extraversion": <0-5>,
  "Agreeableness": <0-5>,
  "Neuroticism": <0-5>,
  "LogicalMathematical": <0-5>,
  "Investigative": <0-5>,
  "Artistic": <0-5>,
  "Musical": <0-5>,
  "BodilyKinesthetic": <0-5>,
  "SpatialVisual": <0-5>,
  "Interpersonal": <0-5>,
  "Social": <0-5>,
  "Realistic": <0-5>,
  "Enterprising": <0-5>,
  "Conventional": <0-5>,
  "Intrapersonal": <0-5>,
  "RIASEC_field": <0-5>,
  "RIASEC_type": "<string value>"
}
```

### **Step 1 — Compute 10 Weighted High-Level Features**

```text
Cognitive_Ability        = 0.5*LogicalMathematical + 0.4*Investigative + 0.1*Conscientiousness
Conscientiousness        = 0.5*Conscientiousness + 0.3*Conventional + 0.2*Intrapersonal
Analytical_Thinking      = 0.5*LogicalMathematical + 0.4*Investigative + 0.1*Openness
Creativity_Openness      = 0.3*Openness + 0.3*Artistic + 0.2*Musical + 0.2*SpatialVisual
Social_Communication     = 0.25*Extraversion + 0.25*Agreeableness + 0.25*Interpersonal + 0.25*Social
Interest_Field_Alignment = RIASEC_field
Stress_Tolerance         = 0.6*(5 - Neuroticism) + 0.4*Intrapersonal
Practical_Skills         = 0.4*BodilyKinesthetic + 0.4*Realistic + 0.2*SpatialVisual
Theoretical_Orientation  = 0.4*LogicalMathematical + 0.4*Investigative + 0.2*Openness
Learning_Motivation      = 0.6*Intrapersonal + 0.4*Conscientiousness
```

### **Step 2 — Preprocess Features**

1. Apply mild compression (e.g., `sqrt(feature)` or `log1p(feature)`) to reduce inflated values.
2. Ensure all features are ≥ 0.

### **Step 3 — Convert to Proportional Values**

1. Compute total = sum of all 10 features.
2. If total = 0 → set all features to 0.
3. Else → normalize each feature:

   ```text
   normalized_feature = feature / total
   ```
4. Round each normalized feature to **3 decimal places**.

### **Step 4 — Output JSON**

```json
{
  "Cognitive_Ability": <0-1>,
  "Conscientiousness": <0-1>,
  "Analytical_Thinking": <0-1>,
  "Creativity_Openness": <0-1>,
  "Social_Communication": <0-1>,
  "Interest_Field_Alignment": <0-1>,
  "Stress_Tolerance": <0-1>,
  "Practical_Skills": <0-1>,
  "Theoretical_Orientation": <0-1>,
  "Learning_Motivation": <0-1>,
  "RIASEC_type": "<string value>"
}
```

### **Notes / Rationale**

* Weighted mapping follows **psychological, educational, and career research**.
* Mild compression prevents extreme values from dominating the vector.
* Proportional normalization ensures **balanced, interpretable, and comparable student profiles**.
* Sum = 1 allows **easy visualization** and relative comparison across dimensions.
