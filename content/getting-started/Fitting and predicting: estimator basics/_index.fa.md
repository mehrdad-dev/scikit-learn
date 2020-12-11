---
title: "برازش و پیش بینی: اصول برآوردگر"
title-en: "Fitting and predicting: estimator basics"
date: 2020-12-09
lastmod: 2020-12-09
weight: 1
draft: false
# search related keywords
keywords: ["برازش", "پیش بینی"]
---

Scikit-learn
ده ها الگوریتم و مدل یادگیری ماشین built-in را فراهم می‌کند،
که
[برآوردگرد](https://scikit-learn.org/stable/glossary.html#term-estimators)
نامیده می‌شوند.

هر براوردگر می‌تواند بر روی برخی از داده ها با استفاده از متد fit، متناسب شود.

در اینجا یک مثال ساده آورده شده است که ما یک RandomForestClassifier را بر روی برخی داده های بسیار پایه ای fit می‌کنیم:


```python
from sklearn.ensemble import RandomForestClassifier
clf = RandomForestClassifier(random_state=0)
X = [[ 1,  2,  3],  # 2 samples, 3 features
     [11, 12, 13]]
y = [0, 1]  # classes of each sample
clf.fit(X, y)
```