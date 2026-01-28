# Heart Failure Survival Analysis, Winter 2026

Survival analysis of heart failure patients to identify key factors that distinguish survival from death. This project provides a complete end-to-end data science pipeline from raw clinical data to predictive modeling and interpretable insights.

**Key Finding**: Two features are sufficient to distinguish survival from death using different classifiers.

## Project Overview

Heart failure is a critical condition affecting millions worldwide. Early identification of high-risk patients enables timely intervention and improved outcomes. This project implements a comprehensive analytical pipeline to:

- Process and clean clinical records data
- Perform exploratory data analysis and visualization
- Conduct rigorous statistical hypothesis testing
- Engineer meaningful features from raw clinical measurements
- Build and evaluate predictive machine learning models
- Identify the most important predictors of patient survival

## Structure

Below is a high-level overview of the main components of this project.

<ins>**Dataset**</ins> {<small>`heart_failure_clinical_records_dataset.csv`</small>}
<br>
Heart failure clinical records from 299 patients collected at the Faisalabad Institute of Cardiology. Contains 13 clinical features:

| Feature | Description | Type |
| --- | --- | --- |
| age | Age of patient (years) | Continuous |
| anaemia | Decrease of red blood cells | Binary |
| creatinine_phosphokinase | Level of CPK enzyme in blood (mcg/L) | Continuous |
| diabetes | If patient has diabetes | Binary |
| ejection_fraction | Percentage of blood leaving heart per contraction | Continuous |
| high_blood_pressure | If patient has hypertension | Binary |
| platelets | Platelets in blood (kiloplatelets/mL) | Continuous |
| serum_creatinine | Level of serum creatinine in blood (mg/dL) | Continuous |
| serum_sodium | Level of serum sodium in blood (mEq/L) | Continuous |
| sex | Gender (0=Female, 1=Male) | Binary |
| smoking | If patient smokes | Binary |
| time | Follow-up period (days) | Continuous |
| DEATH_EVENT | If patient died during follow-up | Binary (Target) |

<ins>**Week 1: Data Exploration & Visualization**</ins> {<small>`Week1.ipynb`</small>}
<br>
Introduction to the dataset and exploratory data analysis pipeline:
- Loading and inspecting clinical data structure
- Handling missing values and data quality checks
- Summary statistics and distribution analysis
- Visualization techniques: histograms, box plots, correlation heatmaps
- Initial insights into feature relationships

<ins>**Week 2: Statistical Analysis & Feature Importance**</ins> {<small>`Week2.ipynb`</small>}
<br>
Rigorous statistical testing and feature evaluation:
- Pearson correlation with target variable
- Parametric testing: Independent samples T-test
- Non-parametric testing: Mann-Whitney U test
- Multiple hypothesis correction: Benjamini-Hochberg FDR
- Feature importance using Random Forest classifier
- Variance analysis and coefficient of variation

## Pipeline Architecture

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   Raw Data      │────▶│   Preprocessing │────▶│      EDA        │
│   (CSV)         │     │   & Cleaning    │     │  Visualization  │
└─────────────────┘     └─────────────────┘     └─────────────────┘
                                                         │
                                                         ▼
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   Evaluation    │◀────│   ML Models     │◀────│   Statistical   │
│   & Insights    │     │   Training      │     │   Analysis      │
└─────────────────┘     └─────────────────┘     └─────────────────┘
```

## Schedule

| **Week** | **Topic** | **Links** |
| --- | --- | --- |
| 1 | Data Exploration | [Notebook](Week1.ipynb), [Seaborn Docs](https://seaborn.pydata.org/), [Pandas Docs](https://pandas.pydata.org/docs/) |
| 2 | Statistical Analysis | [Notebook](Week2.ipynb), [Scipy Stats](https://docs.scipy.org/doc/scipy/reference/stats.html), [Statsmodels](https://www.statsmodels.org/) |

## Key Results

From our analysis, we identified the following significant predictors of mortality (p < 0.05 after FDR correction):

1. **time** - Follow-up period (strongest predictor)
2. **ejection_fraction** - Heart pumping efficiency
3. **serum_creatinine** - Kidney function indicator
4. **age** - Patient age
5. **serum_sodium** - Electrolyte balance

## Resources

**Documentation**
- [Pandas User Guide](https://pandas.pydata.org/docs/user_guide/index.html)
- [Seaborn Tutorial](https://seaborn.pydata.org/tutorial.html)
- [Scipy Statistical Functions](https://docs.scipy.org/doc/scipy/reference/stats.html)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/)

**Dataset Source**
- [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Heart+failure+clinical+records)

**Research Paper**
- Chicco, D., Jurman, G. *Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone*. BMC Med Inform Decis Mak 20, 16 (2020)

## Getting Started

```bash
# Clone the repository
git clone https://github.com/MichiganDataScienceTeam/W26-MDST-Project_Heart-Failure-Survival-Analysis.git
cd W26-MDST-Project_Heart-Failure-Survival-Analysis

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook
```

## Requirements

- Python 3.8+
- pandas
- numpy
- matplotlib
- seaborn
- scipy
- scikit-learn
- statsmodels
- jupyter

## Acknowledgements

<big>**Leads**</big>
<br>
Sina Bonakdar
<br>
Terry Zhang

<big>**Organization**</big>
<br>
[Michigan Data Science Team](https://mdst.club/)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
