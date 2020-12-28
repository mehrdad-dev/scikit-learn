---
title: "ترانسفورماتور ها و پیش پردازنده ها"
title-en: "Transformers and pre-processors"
date: 2020-12-09
lastmod: 2020-12-28
weight: 2
draft: false
# search related keywords
keywords: ["ترانسفورماتور ها", "پیش پردازنده ها"]
---

جریان کاری یادگیری ماشین اغلب از قسمت های مختلفی تشکیل شده است.
یک پایپ لاین معمول و متداول تشکیل شده از یک مرحله پیش پردازش است که داده ها را
transform یا imputes می‌کند،
و در نهایت یک پیش‌بینی کننده مقادیر هدف را پیش‌بینی می‌کند.

در `scikit-learn`،
پیش پردازنده ها و ترانسفورماتورها به دنباله API مشابه ای که
برای براوردگر استفاده می‌کنیم می‌آیند.
(در واقع همه آن ها از یک کلاس به اسم `BaseEstimator` ارث می‌برند.)

اشیاء ترانسفورماتور متد
[predict](https://scikit-learn.org/stable/glossary.html#term-predict)
ندارند بلکه یک متد
[transform](https://scikit-learn.org/stable/glossary.html#term-transform)
دارند که به عنوان خروجی ماتریس X که دگرگون شده است را می‌دهند:


```python
from sklearn.preprocessing import StandardScaler
X = [[0, 15],
     [1, -10]]
# scale data according to computed scaling values
StandardScaler().fit(X).transform(X)
```
گاهی اوقات، شما می‌خواهید تغییرات مختلفی را در ویژگی های مختلف اعمال کنید:
[ColumnTransformer](https://scikit-learn.org/stable/modules/compose.html#column-transformer)
برای این موارد استفاده طراحی شده است.
