
---

### `WEEK6.md`
```markdown
# Week 6 — Final Model & Submission

**Goal:** Finalize model, save artifacts, write the final report.

**Cells**

1. Save final model and vectorizer
```python
final_model = best  # from week5
import joblib
joblib.dump(final_model, 'final_model.pkl')
joblib.dump(tfidf, 'tfidf_vectorizer.pkl')

pred = final_model.predict(X_test_tfidf)
from sklearn.metrics import classification_report
print(classification_report(y_test, pred))

def predict_text(text):
    c = clean_text(text)
    v = tfidf.transform([c])
    return final_model.predict(v)[0]

print(predict_text("Breaking: Some new statement"))
