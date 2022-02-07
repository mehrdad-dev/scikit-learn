---
title: "پایپ لاین ها: پیش پردازنده های زنجیره ای و برآوردگر ها"
title-en: "Pipelines: chaining pre-processors and estimators"
date: 2020-12-09
lastmod: 2020-12-28
weight: 3
draft: false
# search related keywords
keywords: ["برآوردگر ها", "پیش پردازنده ها"]
---

ترانسفورماتورها و برآوردگرها (پیش بینی کننده ها) می‌توانند با هم در یک شی واحد ترکیب شوند:
یک [Pipeline](https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html#sklearn.pipeline.Pipeline)

Pipeline همان API را به عنوان یک برآوردگر منظم ارائه می‌دهد:
که می‌تواند متناسب شود و برای پیش‌بینی ها استفاده شود توسط
`fit` و `predict`.
همانطور که بعدا خواهیم دید، استفاده از پایپ لاین همچنین از نشت داده ها جلوگیری می‌‌کند.
به طور مثال برخی داده های آزمون در داده های آموزش شما افشا می‌شوند.

در مثال زیر،
[مجموعه داده Iris را بارگذاری می‌کنیم،](https://scikit-learn.org/stable/datasets.html#datasets)
آن را به مجموعه آزمون و آزمایش تقسیم می‌کنیم،
و معیار accuracy یک پایپ لاین را بر روی داده های آزمون محاسبه می‌کنیم:

```python
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.pipeline import make_pipeline
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# create a pipeline object
pipe = make_pipeline(
    StandardScaler(),
    LogisticRegression()
)

# load the iris dataset and split it into train and test sets
X, y = load_iris(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0)

# fit the whole pipeline
pipe.fit(X_train, y_train)


# we can now use it like any other estimator
accuracy_score(pipe.predict(X_test), y_test)
```