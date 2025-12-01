
---

### `WEEK3.md`
```markdown
# Week 3 — Feature Extraction (TF-IDF)

**Goal:** Convert text to numeric features.

**Cells**

1. Train-test split
```python
from sklearn.model_selection import train_test_split
X = df['clean_text']; y = df['label']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42, stratify=y)

from sklearn.feature_extraction.text import TfidfVectorizer
tfidf = TfidfVectorizer(max_features=5000)
X_train_tfidf = tfidf.fit_transform(X_train)
X_test_tfidf = tfidf.transform(X_test)
print(X_train_tfidf.shape, X_test_tfidf.shape)

import joblib
joblib.dump(tfidf, 'tfidf_vectorizer.pkl')
