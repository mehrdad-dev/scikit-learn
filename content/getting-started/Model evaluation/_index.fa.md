---
title: "ارزیابی مدل"
title-en: "Model evaluation"
date: 2020-12-09
lastmod: 2020-12-28
weight: 4
draft: false
# search related keywords
keywords: ["ارزیابی", "مدل"]
---

متاسب کردن یک مدل بر روی برخی از داده ها به این معنی نیست که بر روی داده هایی که دیده نشده اند هم به خوبی پیش بینی خواهد کرد.
این موضوع نیاز به ارزیابی مستقیم دارد،
train_test_split را دیدیم که یک مجموعه داده را به مجموعه آزمون و آموزش تقسیم می‌کند،
اما scikit-learn ابزار های زیادی برای ارزیابی مدل دارد،
به ویژه برای cross-validation (اعتبار سنجی متقابل).

ما در اینجا با استفاده از 
[cross_validate](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.cross_validate.html#sklearn.model_selection.cross_validate)
به طور خلاصه روش ارزیابی متقابل
5-fold را نشان می‌دهیم.

توجه داشته باشید که امکنا تکرار دستی fold ها،
استفاده از استراتژی های مختلف تقسیم داده و استفاده از توابع امتیاز دهی سفارشی نیز وجود دارد.

لطفا برای اطلاعات بیشتر به
[راهنمای کاربر](https://scikit-learn.org/stable/modules/cross_validation.html#cross-validation)
ما مراجعه کنید:

```python
from sklearn.datasets import make_regression
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import cross_validate

X, y = make_regression(n_samples=1000, random_state=0)
lr = LinearRegression()

result = cross_validate(lr, X, y)  # defaults to 5-fold CV
result['test_score']  # r_squared score is high because dataset is easy
```