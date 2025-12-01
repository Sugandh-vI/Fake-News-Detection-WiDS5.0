
---

### `WEEK4.md`
```markdown
# Week 4 — Baseline Models

**Goal:** Train baseline classifiers and compare.

**Cells**

1. Train 3 models
```python
from sklearn.linear_model import LogisticRegression
from sklearn.naive_bayes import MultinomialNB
from sklearn.svm import LinearSVC

lr = LogisticRegression(max_iter=2000); lr.fit(X_train_tfidf, y_train)
nb = MultinomialNB(); nb.fit(X_train_tfidf, y_train)
svm = LinearSVC(); svm.fit(X_train_tfidf, y_train)


from sklearn.metrics import accuracy_score
for name, model in [('LR',lr),('NB',nb),('SVM',svm)]:
    pred = model.predict(X_test_tfidf)
    print(name, accuracy_score(y_test, pred))
