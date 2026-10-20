# Intrusion Detection System using Machine Learning

Classifies network connections as normal or one of four attack types using the KDD Cup 1999 dataset.

## Classes
| Class | Meaning |
|---|---|
| normal | Legitimate traffic |
| dos | Denial of service |
| probe | Scanning and reconnaissance |
| r2l | Unauthorised remote access |
| u2r | Privilege escalation |

## Approach
- Data: KDD Cup 1999, 10% subset (~494k connections, 41 features)
- Preprocessing: label encoding, removal of highly correlated features (30 features kept), stratified 67/33 split, MinMax scaling
- Models compared: Naive Bayes, Decision Tree, Random Forest, Linear SVC, Logistic Regression, Histogram Gradient Boosting
- Evaluation: accuracy, macro F1, per-class reports, confusion matrices, ROC and precision-recall curves, feature importance
- Best model: **Random Forest, 99.97% test accuracy** (330,994 train / 163,027 test)

## Files
| File | Purpose |
|---|---|
| `intrusion_detection_system.ipynb` | Full pipeline |
| `ids_model.joblib`, `ids_scaler.joblib` | Saved model and scaler |
| `ids_metadata.json` | Feature names, class names, accuracy |
| `kddcup.data_10_percent_corrected` | Dataset |

## Run it
```bash
pip install pandas numpy matplotlib seaborn scikit-learn kagglehub joblib
jupyter notebook intrusion_detection_system.ipynb
```
If the dataset is missing, the notebook can fall back to synthetic data, so results will differ.

## Limitations
KDD Cup 1999 is an old benchmark and is heavily imbalanced (u2r has under 100 samples), so overall accuracy overstates real-world performance. Check per-class recall.

## Credits
Based on [add article link], with the fixes listed in the notebook summary.
