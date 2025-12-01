# How to run (Google Colab preferred)

## Option A — Recommended: load from Kaggle (no big upload)
1. Create `kaggle.json` from your Kaggle Account -> API -> Create Token.
2. In Colab run:
```python
!pip install kaggle
from google.colab import files
files.upload()  # upload kaggle.json
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
!kaggle datasets download -d saurabhshahane/fake-news-classification
!unzip -q fake-news-classification.zip

Option B -

from google.colab import drive
drive.mount('/content/drive')
df = pd.read_csv('/content/drive/MyDrive/WELFake_Datast.csv')
