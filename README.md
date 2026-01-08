# Student Performance Analysis

Repository for an exploratory data analysis (EDA) project that investigates factors associated with student academic performance (GPA). The analysis is implemented as a Jupyter/Colab notebook.

## Contents

- `student_performance_eda.ipynb` — Main EDA notebook (viewable and runnable in Colab).
- `Student_performance_data _.csv` — Raw dataset used by the notebook.
- `README.md` — This file.

## Project overview

This project explores how student characteristics and behaviors relate to academic performance. The notebook performs data loading, validation, univariate and bivariate analyses, visualization, and correlation checks to answer questions such as:

- How does weekly study time affect GPA?
- Are there differences in performance across gender or ethnicity?
- Which features show the strongest relationship with GPA?

## Data

Dataset (CSV) used in the notebook:
- Raw CSV: https://raw.githubusercontent.com/Sydney205/student_performance_analysis/main/Student_performance_data%20_.csv

Key columns:
- StudentID, Age, Gender, Ethnicity, ParentalEducation
- StudyTimeWeekly, Absences, Tutoring, ParentalSupport
- Extracurricular, Sports, Music, Volunteering
- GPA, GradeClass

Dataset size and basic stats (from the notebook)
- Rows: 2,392
- StudyTimeWeekly: mean ≈ 9.77 hours/week (std ≈ 5.65; range ≈ 0.001–19.98)
- Absences: mean ≈ 14.54 (std ≈ 8.47)
- GPA: mean ≈ 1.91 (std ≈ 0.92), median ≈ 1.89, range 0.0–4.0
- Binary participation indicators (approximate means): Extracurricular ≈ 0.38, Sports ≈ 0.30, Music ≈ 0.20, Volunteering ≈ 0.16
- Tutoring prevalence is low (mean ≈ 0.30; encoded as 0/1)

## Notebook

Open and run the EDA notebook:
- View in GitHub: `student_performance_eda.ipynb`
- Run in Colab: https://colab.research.google.com/github/Sydney205/student_performance_analysis/blob/main/student_performance_eda.ipynb

Notebook stages:
1. Imports and setup (pandas, numpy, matplotlib, seaborn)
2. Data loading and initial inspection (shape, dtypes, describe)
3. Missing value checks and basic cleaning
4. Univariate analysis (distributions, histograms)
5. Bivariate analysis (boxplots, scatterplots)
6. Correlation analysis (heatmap, numeric correlations)
7. Findings, conclusions and suggested next steps

## Findings from the analysis

The notebook's exploratory analyses produced the following primary findings and observations. These are descriptive/ exploratory — follow-up statistical tests and modeling are recommended to confirm effects.

- Study time and GPA
  - There is a positive association between StudyTimeWeekly and GPA in bivariate views and scatterplots: students who report more study hours generally have higher GPAs.
  - The relationship is visible but not perfectly tight (considerable spread), indicating other factors also affect GPA.

- Absences and GPA
  - Higher numbers of absences tend to be associated with lower GPA in bivariate plots and grouped summaries. This is consistent across grade levels.

- Parental education & parental support
  - Students with higher ParentalEducation and higher ParentalSupport tend to have somewhat higher GPAs on average in the grouped analyses. These relationships appear moderate and merit further modeling (control for confounders).

- Tutoring
  - Tutoring is present for a minority of students (≈30%). The simple comparisons in the notebook show limited or mixed effect in raw averages; this may reflect selection bias (students seeking tutoring are not a random sample).

- Extracurriculars (sports, music, volunteering)
  - Binary participation variables show mixed associations:
    - Sports and music participation show small differences in average GPA in the notebook's grouped boxplots.
    - Volunteering is less common and shows limited signal in simple comparisons.
  - Participation may relate to time allocation and other unobserved variables — further analysis should control for StudyTimeWeekly and other covariates.

- Distributional notes
  - GPA distribution is skewed with many values clustered in the lower-middle range; median (~1.89) is close to mean (~1.91).
  - StudyTimeWeekly shows wide variability (0–~20 hours/week).

- Correlations and relative importance
  - The correlation heatmap indicates StudyTimeWeekly and Absences among the features with clear bivariate links to GPA. ParentalEducation and ParentalSupport show weaker-to-moderate relationships.
  - No single predictor fully explains GPA variance based on exploratory checks — multivariate modeling is recommended.

- Limitations and data quality considerations
  - Observational dataset: relationships are correlational and not causal.
  - Some features are encoded numerically (e.g., Gender, Ethnicity, GradeClass) — check encoding and mapping before modeling or public release.
  - Potential measurement error or outliers (extremely low GPAs in some rows) should be examined.
  - The dataset appears complete (no missing values reported in the notebook), but check data provenance and cleaning steps if you plan publication.

## Example visuals included in the notebook

- Histogram / KDE of GPA
- Scatterplot of StudyTimeWeekly vs. GPA with regression line
- Boxplots of GPA by Gender, Ethnicity, GradeClass
- Heatmap of numeric correlations
- Bar charts of participation rates (sports, music, volunteering)

(See the notebook for the actual figures and code that produced them.)

## How to run locally

1. Clone the repository:
   git clone https://github.com/Sydney205/student_performance_analysis.git
2. (Optional) Create and activate a virtual environment:
   python -m venv .venv
   source .venv/bin/activate  # macOS / Linux
   .venv\Scripts\activate     # Windows
3. Install dependencies:
   pip install -r requirements.txt
   or:
   pip install pandas numpy matplotlib seaborn jupyter
4. Start Jupyter and open the notebook:
   jupyter notebook student_performance_eda.ipynb

Or open the notebook in Colab using the link above and run it there (no local setup required).

## Suggested next steps

- Fit multivariate models:
  - Linear regression (with regularization), random forest, or gradient boosting to estimate incremental contributions of features to GPA.
  - If converting GPA to categories (e.g., pass/fail or tiers), try classification models.
- Evaluate model validity with cross-validation and test splits; report R², RMSE, or classification metrics as appropriate.
- Perform statistical tests (t-tests, ANOVA, or regression inference) to assess the significance of observed differences.
- Feature engineering:
  - Bin study time into categories, create interaction terms (e.g., StudyTimeWeekly × ParentalSupport).
  - Aggregate extracurricular participation into a single "engagement" index.
- Address potential biases and fairness:
  - Compare model performance and residuals across gender and ethnicity subgroups.
- Data cleaning & robustness:
  - Investigate and handle outliers, verify encoding of categorical variables, and, if necessary, impute or trim extreme values.
- Create a concise summary report or dashboard with the most relevant plots and final model results.

## Contributing

If you find issues or have suggestions, feel free to open an issue or submit a pull request. Contributions that improve reproducibility, add tests, or extend the analysis (modeling, fairness checks, dashboard) are welcome.

## License & Attribution

Please see the repository license (if included) for reuse terms. If no license is present, assume the default “All rights reserved” for the repository owner.

## Contact

Author / maintainer: Sydney205 (GitHub)  
For questions related to this analysis, open an issue in the repository.
