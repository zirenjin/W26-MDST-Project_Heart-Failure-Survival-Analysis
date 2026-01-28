# Heart Failure Survival Analysis, Winter 2026

Survival analysis of heart failure patients to identify key factors that distinguish survival from death. Students will learn visualization, statistical analysis, and machine learning techniques to predict patient outcomes.

**Key Finding**: Two features are sufficient to distinguish survival from death using different classifiers.

## Structure

Below is a high-level overview of the main components of this project.

<ins>**Dataset**</ins> {<small>`heart_failure_clinical_records_dataset.csv`</small>}
<br>
Heart failure clinical records from 299 patients with 13 features including age, ejection fraction, serum creatinine, and follow-up time. Binary outcome: survival or death.

<ins>**Week 1: Data Exploration**</ins> {<small>`Week1.ipynb`</small>}
<br>
Introduction to the dataset, exploratory data analysis, and visualization techniques using Pandas, Seaborn, and Matplotlib.

<ins>**Week 2: Statistical Analysis**</ins> {<small>`Week2.ipynb`</small>}
<br>
Hypothesis testing (T-test, Mann-Whitney U), correlation analysis, multiple testing correction (FDR), and feature importance using Random Forest.

## Schedule

| **Week** | **Topic** | **Links** |
| --- | --- | --- |
| 1 | Data Exploration | [Notebook](Week1.ipynb), [Seaborn Docs](https://seaborn.pydata.org/), [Pandas Docs](https://pandas.pydata.org/docs/) |
| 2 | Statistical Analysis | [Notebook](Week2.ipynb), [Scipy Stats](https://docs.scipy.org/doc/scipy/reference/stats.html), [Statsmodels](https://www.statsmodels.org/) |

## Resources

- [UCI Dataset](https://archive.ics.uci.edu/ml/datasets/Heart+failure+clinical+records)
- [Scikit-learn](https://scikit-learn.org/stable/)
- Chicco, D., Jurman, G. *Machine learning can predict survival of patients with heart failure*. BMC Med Inform Decis Mak 20, 16 (2020)

## Getting Started

```bash
git clone https://github.com/MichiganDataScienceTeam/W26-MDST-Project_Heart-Failure-Survival-Analysis.git
cd W26-MDST-Project_Heart-Failure-Survival-Analysis
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

## Acknowledgements

<big>**Leads**</big>
<br>
Sina Bonakdar
<br>
Terry Zhang

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
