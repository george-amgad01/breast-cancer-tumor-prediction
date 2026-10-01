# Breast Cancer Tumour Classification

Comparative study of **KNN, Decision Tree, Logistic Regression, and SVM** on the **Wisconsin Diagnostic Breast Cancer (WDBC)** dataset (569 samples, 30 features), focusing on **malignant-class recall** rather than accuracy alone.

### Results

| Model                   |   Accuracy |  Precision |     Recall |         F1 | Malignant Missed |
| ----------------------- | ---------: | ---------: | ---------: | ---------: | ---------------: |
| **Logistic Regression** | **0.9737** | **0.9762** | **0.9535** | **0.9647** |       **2 / 43** |
| KNN (k=9)               |     0.9649 |     0.9535 |     0.9535 |     0.9535 |           2 / 43 |
| SVM (linear)            |     0.9561 |     0.9318 |     0.9535 |     0.9425 |           2 / 43 |
| Decision Tree (entropy) |     0.9474 |     0.9744 | **0.8837** |     0.9268 |       **5 / 43** |

**Key finding:** Accuracy alone makes the models appear similar, while recall reveals that the Decision Tree misses **5 of 43 malignant cases**, compared with **2** for the other models. This highlights why **recall is critical in medical screening**, where false negatives can have greater consequences than false positives.

### Method

* 80/20 train–test split (`random_state=42`)
* `StandardScaler` for KNN, Logistic Regression, and SVM; no scaling for Decision Tree
* Metrics: **accuracy, precision, recall, F1**, with `pos_label='M'`
* Confusion matrices used to examine false negatives

### Reproduce

Dataset files (`wdbc.data`, `wdbc.names`) are not included. Download them from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/17/wisconsin+diagnostic+breast+cancer) and place them in the project directory.

```bash
pip install pandas numpy scikit-learn matplotlib jupyter
jupyter notebook tumor_prediction.ipynb
```

[LinkedIn: Why recall matters more than accuracy in medical diagnosis](https://www.linkedin.com/posts/george-amgad-95660036a_machinelearning-datascience-ai-ugcPost-7409281893801852929-NQbi)
