# **SECTION 1 — Psychometric Traits**

**Objective:**
Given a CSV-like input containing one student’s Likert-scale responses (headers in the first row, answers in the second row), generate a JSON object representing averaged psychometric trait scores.

### **Required Output Format**

```json
{
  "Openness": <avg>,
  "Conscientiousness": <avg>,
  "Extraversion": <avg>,
  "Agreeableness": <avg>,
  "Neuroticism": <avg>,
  "LogicalMathematical": <avg>,
  "Investigative": <avg>,
  "Artistic": <avg>,
  "Musical": <avg>,
  "BodilyKinesthetic": <avg>,
  "SpatialVisual": <avg>,
  "Interpersonal": <avg>,
  "Social": <avg>,
  "Realistic": <avg>,
  "Enterprising": <avg>,
  "Conventional": <avg>,
  "Intrapersonal": <avg>,
  "RIASEC_field": <computed>
}
```

### **Instructions**

1. Compute each trait as the **average** of all corresponding questions.
2. Use the following mappings:

   * **Big Five:** Openness, Conscientiousness, Extraversion, Agreeableness, Neuroticism
   * **RIASEC:** Realistic, Investigative, Artistic, Social, Enterprising, Conventional
   * **Multiple Intelligences:** Intrapersonal, Musical, Logical-Mathematical, Bodily-Kinesthetic, Spatial-Visual, Interpersonal
3. Keep Likert values as-is (1–5).
4. Return **numeric values only**, rounded to one decimal if needed.
5. Ignore demographic or free-text columns.
6. **RIASEC_field** = the dominant RIASEC type computed from the six RIASEC averages (optionally weighted by Big Five if required).
7. Input format:

   * First row → question identifiers
   * Second row → student responses
   * Input headers (CSV first row):Openness_1,Openness_2,Openness_3,Openness_4,Openness_5,
Conscientiousness_1,Conscientiousness_2,Conscientiousness_3,Conscientiousness_4,Conscientiousness_5,
Extraversion_1,Extraversion_2,Extraversion_3,Extraversion_4,Extraversion_5,
Agreeableness_1,Agreeableness_2,Agreeableness_3,Agreeableness_4,Agreeableness_5,
Neuroticism_1,Neuroticism_2,Neuroticism_3,Neuroticism_4,Neuroticism_5,
Realistic_1,Realistic_2,Realistic_3,Realistic_4,Realistic_5,Realistic_6,
Investigative_1,Investigative_2,Investigative_3,Investigative_4,Investigative_5,Investigative_6,
Artistic_1,Artistic_2,Artistic_3,Artistic_4,Artistic_5,Artistic_6,
Social_1,Social_2,Social_3,Social_4,Social_5,Social_6,
Enterprising_1,Enterprising_2,Enterprising_3,Enterprising_4,Enterprising_5,Enterprising_6,
Conventional_1,Conventional_2,Conventional_3,Conventional_4,Conventional_5,Conventional_6,
Intrapersonal_1,Intrapersonal_2,Intrapersonal_3,Intrapersonal_4,Intrapersonal_5,Intrapersonal_6,
Musical_1,Musical_2,Musical_3,Musical_4,Musical_5,Musical_6,
LogicalMathematical_1,LogicalMathematical_2,LogicalMathematical_3,LogicalMathematical_4,LogicalMathematical_5,LogicalMathematical_6,
BodilyKinesthetic_1,BodilyKinesthetic_2,BodilyKinesthetic_3,BodilyKinesthetic_4,BodilyKinesthetic_5,BodilyKinesthetic_6,
SpatialVisual_1,SpatialVisual_2,SpatialVisual_3,SpatialVisual_4,SpatialVisual_5,SpatialVisual_6,
Interpersonal_1,Interpersonal_2,Interpersonal_3,Interpersonal_4,Interpersonal_5,Interpersonal_6,Interpersonal_7,Interpersonal_8,Interpersonal_9,Interpersonal_10
   * Input student responses (CSV second row): 4,4,5,4,4,3,3,2,4,3,3,4,3,4,4,3,3,3,2,2,2,3,3,4,4,4,4,4,4,4,3,2,4,2,3,4,4,4,5,4,4,4,4,3,4,4,5,3,2,4,4,4,4,4,4,3,3,3,4,4,4,2,3,2,4,4,3,2,3,5,4,4,4,4,3,4,3,2,4,2,4,1,2,3,2,4,1,2,1,2,2,2,4,3,2,4,4,3,3,4,4,4


8. Output must follow the exact JSON structure shown above.


**FIRST INPUT:**
Provide the CSV-like psychometric row in an array:
`[]`

---

# **SECTION 2 — Demographic Information**

**Objective:**
Given the demographic survey CSV (headers in the first row, student’s answers in the second row), produce a standardized JSON object describing demographic characteristics.

### **Required Output Format**

```json
{
  "Gender": "",
  "Age": "",
  "EducationLevel": "",
  "City": "",
  "FamilyIncomeRange": "",
  "FamilySize": "",
  "MotherEducation": "",
  "FatherEducation": "",
  "MiddleSchoolType": "",
  "HighSchoolType": "",
  "CurrentMajor": "",
  "Major_Selection_Reasons": [],
  "Satisfaction_with_Major": "",
  "Major_Fit_with_Interests": "",
  "Continue_in_Major": "",
  "Motivating_Factors_in_Class": [],
  "10yr_Priority_Goal": "",
  "Access_to_Quality_Education": "",
  "Leisure_Activities": []
}
```

### **Instructions**

1. Convert comma-separated multiple-choice responses into **JSON arrays**.
2. Keep text **exactly as provided** (Persian/English).
3. Extract only the required demographic fields listed above.
4. If a field has no answer, output an empty string `""`.
5. Trim whitespace from all text fields.
6. Do **not** translate unless needed for JSON structure.
7. Input format:
   * First row → column titles
   * Second row → student responses
8. Output must follow the exact JSON schema shown above.


**SECOND INPUT:**
Provide the CSV-like demographic row in an array:
`[]`
