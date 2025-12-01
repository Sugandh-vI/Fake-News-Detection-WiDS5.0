
---

### `WEEK5.md`
```markdown
# Week 5 — Model Tuning & Error Analysis

**Goal:** Tune the best model and inspect mistakes.

**Cells**

1. Hyperparameter tuning (example for LinearSVC)
```python
from sklearn.model_selection import GridSearchCV
params = {'C':[0.01,0.1,1,10]}
grid = GridSearchCV(LinearSVC(), params, cv=3, scoring='f1', n_jobs=-1)
grid.fit(X_train_tfidf, y_train)
best = grid.best_estimator_
print(grid.best_params_)

from sklearn.metrics import classification_report, confusion_matrix
pred = best.predict(X_test_tfidf)
print(classification_report(y_test, pred))
import seaborn as sns, matplotlib.pyplot as plt
cm = confusion_matrix(y_test, pred)
sns.heatmap(cm, annot=True, fmt='d'); plt.show()

wrong_idx = [i for i,(p,t) in enumerate(zip(pred, y_test.tolist())) if p != t]
for idx in wrong_idx[:10]:
    print('---')
    print('Actual:', y_test.tolist()[idx])
    print('Pred :', pred[idx])
    print('Text :', X_test.tolist()[idx][:300])

