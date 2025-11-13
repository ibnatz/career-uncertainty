# A Data-Driven Exploration of Career-Identity Uncertainty: Insights from the OSMI Tech Mental Health Dataset


## 📌 Project Overview
This project introduces a novel analysis angle on mental health in tech: instead of predicting mental health conditions, we predict career identity uncertainty, such as whether tech professionals question their career path due to mental health struggles.

### 🎯 Key Finding
Age is the #1 predictor (40% feature importance) - career stage matters more than workplace policies!

### 📊 Model Performance
- **Accuracy: 61.4% (baseline Random Forest)**
- **F1-Score: 0.69 for identifying career-uncertain individuals**
- **Classes: Balanced (58% uncertain, 42% certain) - no SMOTE needed**


## 🗂️ Dataset
- **Source:** Open Sourcing Mental Illness (OSMI) Mental Health in Tech Survey
- **Years:** 2017-2021 (combined)
- **Citation:** Memon, F.R. (2023). DOI: 10.17632/mmnzx4w8cg.1
- **Size:** 1,242 tech professionals, 11 features

### Features:
- **Demographics:** age, gender, country
- **Workplace:** tech_company, benefits, workplace_resources, medical_coverage
- **Mental Health:** mental_health (condition status), mh_employer_discussion, mh_coworker_discussion, mh_share (0-10 scale)


## 💡 Novel Contribution


### What Makes This Different?
Most analyses of this dataset focus on:
- Predicting depression/anxiety diagnoses
- Comparing company sizes or countries

### But this project asks: "Does mental health make people question their career trajectory?"

### How We Define Career Uncertainty:
```python
career_uncertainty = 1 if mh_share >= 7 else 0
```
**Rationale:** If someone's mental health significantly impacts their work (mh_share ≥ 7 out of 10), they likely experience career-related doubts and identity struggles.


## 🚀 Quick Start
### Installation
```bash
# Clone the repository
git clone https://github.com/ibnatz/career-uncertainty.git
cd mental-health-career-uncertainty

# Install dependencies
pip install pandas numpy seaborn matplotlib scikit-learn imbalanced-learn
```

### Running the Notebook

1. Download the dataset from Mendeley Data
2. Place mental_health_in_tech_survey.csv in the project directory
3. Open and run mental_health_analysis.ipynb in Jupyter/Colab

```bash
jupyter notebook mental_health_analysis.ipynb
```


## 📈 Results

### Model Performance
**Metric, Class 0 (Certain), Class 1 (Uncertain)**
- Precision, 0.51, 0.68
- Recall, 0.49, 0.69
- F1-Score, 0.50, 0.69

**Overall Accuracy: 61.4%**

### Feature Importance Rankings
**Rank, Feature, Importance**
- 1️⃣                  **Age,**          **40.4%**
- 2️⃣            Mental Health Status,      11.9%
- 3️⃣                 Country,              9.8%
- 4️⃣             Workplace Resources,     8.6%
- 5️⃣                 Benefits,             6.4%
- 6️⃣                 Gender,              6.3%
- 7️⃣            Tech Company Status,       5.3%
- 8️⃣          MH Coworker Discussion,      4.8%
- 9️⃣          MH Employer Discussion,      4.5%
- 🔟             Medical Coverage,         2.1%


## 🔍 Key Insights

### 1. Age Dominates Prediction (40%)
Career uncertainty manifests differently across life stages:
- Early career (20s): "Am I in the right field?" - imposter syndrome, skill uncertainty
- Mid-career (40s): "Is this all there is?" - burnout, career plateau questions

### 2. Workplace Support Matters, But Less Than Expected (9%)
Mental health resources help, but don't override life stage factors.

### 3. Geographic Differences Are Significant (10%)
Cultural attitudes toward mental health and career mobility vary by country.

### 4. Openness Has Low Impact (4-5%)
Whether people discuss mental health with employers/coworkers barely affects career uncertainty - it's more about internal psychological state.


## 🛠️ Technical Details

### Methods
- **Preprocessing:** LabelEncoding for categorical variables, gender standardization
- **Model:** Random Forest Classifier (baseline, no hyperparameter tuning)
- **Split:** 80-20 train-test (993 train, 249 test)
- **Class Balance:** 58-42% → **SMOTE NOT used** (balanced enough)

### Why Random Forest?
- Handles mixed feature types (numeric + categorical)
- Provides interpretable feature importance
- Robust to overfitting with default parameters
- Good baseline for tabular data


## 🎓 Use Cases

### For Students
- Example of novel angle on existing dataset
- Demonstrates feature engineering (creating derived labels)
- Shows when NOT to use SMOTE (balanced classes)

### For Researchers
- New operationalization of career-related mental health outcomes
- Age as moderator of MH-career relationship
- Baseline for future longitudinal studies

### For Tech Companies
- Data-driven evidence for age-stratified mental health programs
- Career counseling > generic wellness programs
- Retention risk prediction framework


## 📚 References
- Memon, F.R. (2023). Survey dataset on mental health in tech professionals from OSMI surveys (2017-2021). Mendeley Data, V1. https://doi.org/10.17632/mmnzx4w8cg.1
- Open Sourcing Mental Illness. (2017-2021). Mental Health in Tech Survey. https://osmhhelp.org/research
- Breiman, L. (2001). Random Forests. Machine Learning, 45(1), 5-32.
- Pedregosa, F., et al. (2011). Scikit-learn: Machine learning in Python. Journal of Machine Learning Research, 12, 2825-2830.


## 👤 Author
**Ibnat Zareen** [ibnatz](https://github.com/ibnatz)
