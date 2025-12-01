
---

### `WEEK2.md`
```markdown
# Week 2 — Text Cleaning & Preprocessing

**Goal:** Clean text for feature extraction.

**Cells**

1. Install/import NLTK
```python
import nltk
nltk.download('punkt'); nltk.download('stopwords'); nltk.download('wordnet')
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer
from nltk.tokenize import word_tokenize
import re, string

stop_words = set(stopwords.words('english'))
lemmatizer = WordNetLemmatizer()

def clean_text(text):
    text = str(text).lower()
    text = re.sub(r'http\\S+|www\\.\\S+', '', text)
    text = text.translate(str.maketrans('', '', string.punctuation))
    words = word_tokenize(text)
    words = [w for w in words if w.isalpha() and w not in stop_words]
    words = [lemmatizer.lemmatize(w) for w in words]
    return ' '.join(words)

df['clean_text'] = df['text'].apply(clean_text)
df[['text','clean_text']].head()
