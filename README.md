# Heart Failure Survival Analysis, Winter 2026

Survival analysis of heart failure patients to identify key factors that distinguish survival from death. Students will learn visualization, statistical analysis, and machine learning techniques to predict patient outcomes.

**Key Finding**: Two features are sufficient to distinguish survival from death using different classifiers.

**[View Project Website](https://michigandatascienceteam.github.io/W26-MDST-Project_Heart-Failure-Survival-Analysis/)**

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
Hypothesis testing (T-test, Mann-Whitney U), correlation analysis, multiple testing correction (FDR), feature variance analysis, and Variance Inflation Factor (VIF) for detecting multicollinearity.

<ins>**Week 3: Unsupervised Learning**</ins> {<small>`Week3.ipynb`</small>}
<br>
Data normalization (Z-score), dimensionality reduction with PCA, K-Means clustering, hierarchical (agglomerative) clustering, confusion matrices, silhouette scores, and the elbow method.

<ins>**Tutorials**</ins> {<small>`tutorials/`</small>}
<br>
Beginner-friendly guides for [Git](tutorials/git_tutorial.md) and [Python virtual environments](tutorials/venv_tutorial.md).

## Schedule

| **Week** | **Topic** | **Links** |
| --- | --- | --- |
| 1 | Data Exploration | [Notebook](Week1.ipynb), [Seaborn Docs](https://seaborn.pydata.org/), [Pandas Docs](https://pandas.pydata.org/docs/) |
| 2 | Statistical Analysis | [Notebook](Week2.ipynb), [Slides](slides/week2_slides.pdf), [Scipy Stats](https://docs.scipy.org/doc/scipy/reference/stats.html), [Statsmodels VIF](https://www.statsmodels.org/stable/generated/statsmodels.stats.outliers_influence.variance_inflation_factor.html) |
| 3 | Unsupervised Learning | [Notebook](Week3.ipynb), [Slides](slides/week3_slides.pdf), [PCA Guide](https://scikit-learn.org/stable/modules/decomposition.html#pca), [Clustering](https://scikit-learn.org/stable/modules/clustering.html) |

## Research Background

This project is based on the paper by Chicco & Jurman (2020):

> **Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone**
> *BMC Medical Informatics and Decision Making, 20, 16*

**Key Findings from the Paper:**
- Applied several ML classifiers (Random Forest, Gradient Boosting, SVM, etc.) to predict survival
- Discovered that **serum creatinine** and **ejection fraction** alone achieve strong predictive performance
- Random Forest achieved the best results with Matthews Correlation Coefficient (MCC) of 0.418
- Feature ranking analysis revealed time, serum creatinine, and ejection fraction as top predictors
- Demonstrated that complex models with all 13 features do not significantly outperform simpler 2-feature models

**Clinical Relevance:**
- Serum creatinine indicates kidney function, often impaired in heart failure patients
- Ejection fraction measures heart pumping efficiency, a direct indicator of cardiac health
- These two biomarkers are routinely measured and can guide clinical decision-making

[Read the full paper](https://bmcmedinformdecismak.biomedcentral.com/articles/10.1186/s12911-020-1023-5)

## Resources

- [Project Website](https://michigandatascienceteam.github.io/W26-MDST-Project_Heart-Failure-Survival-Analysis/)
- [UCI Dataset](https://archive.ics.uci.edu/ml/datasets/Heart+failure+clinical+records)
- [Scikit-learn](https://scikit-learn.org/stable/)
- [Git Tutorial](tutorials/git_tutorial.md)
- [Virtual Environment Tutorial](tutorials/venv_tutorial.md)

## Getting Started

```bash
git clone https://github.com/MichiganDataScienceTeam/W26-MDST-Project_Heart-Failure-Survival-Analysis.git
cd W26-MDST-Project_Heart-Failure-Survival-Analysis
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

New to Git or virtual environments? See the [Git Tutorial](tutorials/git_tutorial.md) and [Virtual Environment Tutorial](tutorials/venv_tutorial.md) for detailed walkthroughs.

## Acknowledgements

<big>**Leads**</big>
<br>
Sina Bonakdar
<br>
Terry Zhang

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
