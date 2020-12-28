---
title: "جستجوی خودکار پارامتر ها"
title-en: "Automatic parameter searches"
date: 2020-12-09
lastmod: 2020-12-28
weight: 5
draft: false
# search related keywords
keywords: ["پارامتر", "خودکار", "جستجو"]
---

همه برآوردگرها دارای پارامترهایی هستند (که در ادبیات اغلب به آنها hyper-parameter یا  اَبَرپارامتر گفته می‌شود) كه می توانند تنظیم شوند.

قدرت تعمیم یک برآوردگر اغلب به چند پارامتر بستگی دارد.
به عنوان مثال یک 
[RandomForestRegressor](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html#sklearn.ensemble.RandomForestRegressor)
دارای یک پارامتر `n_estimators` است که تعداد درختان در جنگل را تعیین می‌کند،
و یک پارامتر `max_depth` که حداکثر عمق هر درخت را تعیین می‌کند.
اغلب اوقات، مشخص نیست که مقادیر دقیق این پارامترها باید چه باشد، زیرا آنها به داده های موجود بستگی دارند.

`Scikit-learn` ابزارهایی را برای یافتن خودکار بهترین ترکیبات پارامترها (از طریق اعتبار سنجی متقابل) فراهم می‌کند.
در مثال زیر، ما به طور تصادفی در فضای پارامتر یک جنگل تصادفی توسط یک شی 
[RandomizedSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html#sklearn.model_selection.RandomizedSearchCV)
جستجو می‌کنیم.

وقتی جستجو به پایان رسید
[RandomizedSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html#sklearn.model_selection.RandomizedSearchCV) 
به عنوان
[RandomForestRegressor](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html#sklearn.ensemble.RandomForestRegressor)
رفتار می‌کند که با بهترین مجموعه پارامترها مجهز شده است.
در
[راهنمای کاربر](https://scikit-learn.org/stable/modules/grid_search.html#grid-search)
بیشتر بخوانید:


```python
from sklearn.datasets import fetch_california_housing
from sklearn.ensemble import RandomForestRegressor
from sklearn.model_selection import RandomizedSearchCV
from sklearn.model_selection import train_test_split
from scipy.stats import randint

X, y = fetch_california_housing(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0)

# define the parameter space that will be searched over
param_distributions = {'n_estimators': randint(1, 5),
                       'max_depth': randint(5, 10)}

# now create a searchCV object and fit it to the data
search = RandomizedSearchCV(estimator=RandomForestRegressor(random_state=0),
                            n_iter=5,
                            param_distributions=param_distributions,
                            random_state=0)
search.fit(X_train, y_train)

search.best_params_

# the search object now acts like a normal random forest estimator
# with max_depth=9 and n_estimators=4
search.score(X_test, y_test)
```

{{< notice note >}}
توجه:
در عمل، تقریباً همیشه می‌خواهید به جای یک برآوردگر تنها،
[در یک پایپ لاین جستجو کنید.](https://scikit-learn.org/stable/modules/grid_search.html#composite-grid-search)
یکی از دلایل اصلی این است که اگر یک مرحله پیش پردازش را بدون استفاده از پایپ لاین در کل مجموعه داده اعمال کنید و سپس هر نوع اعتبار سنجی متقابل را انجام دهید،
شما فرضیه اساسی استقلال بین داده های آموزش و آزمون را خواهید شکست.
در واقع، از آنجا که داده ها را با استفاده از کل مجموعه داده پیش پردازش کرده اید، برخی از اطلاعات مربوط به مجموعه های آزمون در دسترس مجموعه های آموزش است.
این امر منجر به تخمین بیش از حدی برای قدرت تعمیم برآوردگر می‌شود (می‌توانید اطلاعات بیشتر را در این [پست Kaggle](https://www.kaggle.com/alexisbcook/data-leakage) دریافت کنید).
استفاده از خط لوله برای اعتبار سنجی متقابل و جستجو تا حد زیادی شما را از دام این تله دور می‌کند.
{{</ notice >}}