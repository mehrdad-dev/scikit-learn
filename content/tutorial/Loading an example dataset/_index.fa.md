---
title: "بارگیری یک مجموعه داده نمونه"
title-en: "Loading an example dataset"
date: 2021-03-13
lastmod: 2022-03-25
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

به عنوان مثال، در مورد مجموعه داده اعداد، `digits.data` به ویژگی هایی دسترسی می‌دهد که میتوان از آنها برای طبقه بندی نمونه های ارقام استفاده کرد:

```python
>>> print(digits.data)
[[ 0.   0.   5. ...   0.   0.   0.]
 [ 0.   0.   0. ...  10.   0.   0.]
 [ 0.   0.   0. ...  16.   9.   0.]
 ...
 [ 0.   0.   1. ...   6.   0.   0.]
 [ 0.   0.   2. ...  12.   0.   0.]
 [ 0.   0.  10. ...  12.   1.   0.]
```

و label ،`digits.target` ها را برای مجموعه داده رقمی ارائه می‌دهد، این عدد متناظر به هر تصویر رقمی است که ما سعی در یادگیری آن داریم:

```python
>>> digits.target
array([0, 1, 2, ..., 8, 9, 8])
```

{{< notice info >}}
**شکل داده آرایه ها**  
داده ها همواره یک آرایه دو بعدی، به شکل (n_samples, n_features) می‌باشند، هر چند داده های اصلی ممکن است شکل متفاوتی داشته باشند. در مورد ارقام، هر نمونه اصلی به شکل یک تصویر از آرایه (۸، ۸) است که به شکل زیر قابل دسترسی است:
```python
>>> digits.images[0]
array([[  0.,   0.,   5.,  13.,   9.,   1.,   0.,   0.],
       [  0.,   0.,  13.,  15.,  10.,  15.,   5.,   0.],
       [  0.,   3.,  15.,   2.,   0.,  11.,   8.,   0.],
       [  0.,   4.,  12.,   0.,   0.,   8.,   8.,   0.],
       [  0.,   5.,   8.,   0.,   0.,   9.,   8.,   0.],
       [  0.,   4.,  11.,   0.,   1.,  12.,   7.,   0.],
       [  0.,   2.,  14.,   5.,  10.,  12.,   0.,   0.],
       [  0.,   0.,   6.,  13.,  10.,   0.,   0.,   0.]])
```
[مثال ساده در این مجموعه داده](https://scikit-learn.org/stable/auto_examples/classification/plot_digits_classification.html#sphx-glr-auto-examples-classification-plot-digits-classification-py) نشان می‌دهد که چگونه می‌توان با شروع از مشکل اصلی، داده ها را برای استفاده در scikit-learn شکل داد.
{{< /notice >}}

{{< notice info >}}
**بارگیری از مجموعه داده های خارجی**  
برای بارگیری از یک مجموعه داده خارجی، لطفا به [بارگیری مجموعه داده های خارجی](https://scikit-learn.org/stable/datasets/loading_other_datasets.html#external-datasets) مراجعه کنید.
{{< /notice >}}

