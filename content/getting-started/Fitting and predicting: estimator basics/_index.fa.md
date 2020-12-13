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

متد [fit](https://scikit-learn.org/stable/glossary.html#term-fit)
به طور کلی ۲ ورودی می‌گیرد:

- ماتریس نمونه ها (یا ماتریس طراحی) [X ](https://scikit-learn.org/stable/glossary.html#term-x). اندازه X معمولا به صورت
`(n_samples, n_features)` است.
که به این معنی است که نمونه ها به صورت سطر و ویژگی ها به عنوان ستون نشان داده می‌شوند.

- مقادیر هدف [y](https://scikit-learn.org/stable/glossary.html#term-177)
که اعداد حقیقی برای کار های رگرسیون یا اعداد صحیح برای برای کار های طبقه بندی هستند.
y نیازی  به مشخص شدن ندارد.
y معمولا یک آرایه ۱ بعدی است،
که i امین ورودی
مربوط به هدف i امین نمونه (سطر) 
X است.

از هر دو X و y انتظار می‌رود که
با آرایه های numpy یا انواع داده های
[مشابه آرایه]()
معادل باشند، اگر چه برخی از برآوردگر ها با فرمت های دیگری مانند ماتریس های پراکنده کار می‌کنند.

هنگامی که برآوردگر متناسب می‌شود، می توان از آن برای پیش بینی مقادیر هدف داده های جدید استفاده کرد. نیازی به آموزش مجدد برآوردگر ندارید:

```python
clf.predict(X)  # predict classes of the training data
clf.predict([[4, 5, 6], [14, 15, 16]])  # predict classes of new data
```

