---
title: "بارگیری یک مجموعه داده نمونه"
title-en: "Loading an example dataset"
date: 2021-03-13
lastmod: 2021-03-13
weight: 2
draft: false
# search related keywords
keywords: ["loading", "بارگیری", "مجموعه داده", "data set"]
---

`scikit-learn` به همراه چند دیتاست استاندارد ارائه شده است،
به عنوان مثال: مجموعه داده [iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) و [اعداد](https://archive.ics.uci.edu/ml/datasets/Pen-Based+Recognition+of+Handwritten+Digits) برای
طبقه بندی و [مجموعه داده دیابت](https://www4.stat.ncsu.edu/~boos/var.select/diabetes.html) برای رگرسیون.

در ادامه ما مفسر پایتون را با استفاده از shell اجرا می‌کنیم
و سپس مجموعه داده های `iris`  و `اعداد` را بارگیری می‌کنیم.
قرارداد ما این است که `$` نشان دهنده ی اعلان پیوسته است درحالی که  `<<<` نشان دهنده اعلان مفسر پایتون است.


```python
$ python
>>> from sklearn import datasets
>>> iris = datasets.load_iris()
>>> digits = datasets.load_digits()
```

یک دیتاست شبیه به یک شی دیکشنری است که تمام داده ها و متا داده های مربوط به داده را در خود نگه می‌دارد. این داده ها در
`data.`
ذخیره می‌شوند، که یک آرایه
`n_samples, n_features`
است.
در مسائل با نظارت یک یا چند متغیر پاسخ در
`target.`
ذخیره می‌شود.
جرئیات بیشتر در مورد مجموعه داده های مختلف را می‌توان در یک
[بخش اختصاصی](https://scikit-learn.org/stable/datasets.html#datasets)
پیدا کرد.



