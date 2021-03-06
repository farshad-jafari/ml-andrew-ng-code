---
title: "تجزیه اجزای اصلی الگوریتم"
date: 2020-10-26T09:17:16+03:30
draft: false
weight: 80
---

قبل از استفاده از PCA ، یک مرحله پیش پردازش داده وجود دارد که باید انجام دهیم:

### پیش پردازش داده

- گرفتن مجموعه آموزشی: $x^{(1)}, x^{(2)}, ... , x^{(m)}$
- پیش پردازش (feature scaling/mean normalization):
$\mu _j = \frac{1}{m} \sum _ {i=1} ^ m x ^ {(i)} _j  $

- جایگزین کردن هر $x ^ {(i)} _j $ با $x ^ {(i)} _j - \mu _j$
- اگر ویژگی های مختلف در مقیاس های متفاوت باشند (مثلا $= x_1$ اندازه خانه، $ = x_2$ تعداد اتاق خواب ها)،
ویژگی ها را برای داشتن دامنه ای قابل مقایسه از مقادیر تغییر مقیاس دهید.



در بالا ، ابتدا میانگین هر ویژگی را از ویژگی اصلی کم می‌کنیم. سپس تمام ویژگی ها را مقیاس بندی می کنیم:
$$
x ^ {(i)} _j = \frac{x ^ {(i)} _j - \mu _j}{s_j}
$$

می‌توان به طور خاص کاهش از ۲ بعدی به ۱ بعدی داده را به این صورت تعریف کرد:

$$
\sum  = \frac{1}{m} \sum _ {i=1} ^ m (x ^ {(i)}) (x ^ {(i)}) ^ T
$$

مقادیر z، همه اعداد حقیقی هستند و پیش بینی ویژگی های ما بر روی $u ^{(1)}$ هستند.

بنابراین PCA دو وظیفه دارد: 
کشف کردن $u^{(1)}, u^{(2)}, ..., u^{(k)}$ ها، 
و پیدا کردن $z_1, z_2, ... , z_m$

اثبات ریاضی برای روش زیر پیچیده و فراتر از محدوده این دوره است.

**1. محاسبه ماتریس کو واریانس**
$$
\sum  = \frac{1}{m} \sum _ {i=1} ^ m (x ^ {(i)}) (x ^ {(i)}) ^ T
$$

این را می‌توان در اوکتاو به صورت زیر برداری کرد:

<div align="left">

```
Sigma = (1/m) * X' * X
```

</div>

