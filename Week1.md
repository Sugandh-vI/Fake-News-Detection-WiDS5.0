
---

### `WEEK1.md` (paste as a file)
```markdown
# Week 1 — Python Basics & Dataset Exploration

**Goal:** Learn Python basics, Colab, and understand dataset.

**Main tasks (cells to run in Colab)**

1. Imports
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('WELFake_Datast.csv')  # or load via Kaggle/Drive
df.head()
df.info()
df.describe(include='all')
df.isnull().sum()
df = df.dropna(subset=['text','label']).reset_index(drop=True)
print(df['label'].value_counts())
df['label'].value_counts().plot(kind='bar')
plt.show()
