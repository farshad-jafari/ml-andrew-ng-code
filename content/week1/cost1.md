---
title: "تابع هزینه قسمت اول"
date: 2020-09-06T14:08:57+04:30
draft: false
weight : 50
---


### تابع هزینه | Cost Function
با این تابع می‌توانیم بهترین خط مستقیم را برای
داده هایمان به دست آوریم.
با انتخاب های متفاوت برای پارامتر های $\theta_1$ و $\theta_0$ 
 تابع های فرضیه متفاوتی به دست می‌آوریم:
![cost-1.png](../images/cost-1.png?width=30pc)


در <span class="top-dict" data-tipso="linear regression">رگرسیون خطی</span>
<span class="top-dict" data-tipso="training set">مجموعه آموزشی</span>
 مثل این نمودار داریم
و می‌خواهیم مقادیری برای
$\theta_0$ و $\theta_1$ به دست آوریم
به طوری که خط راستی که رسم می‌کنیم، بهترین تطابق
 را با داده هایمان داشته باشد.

![image10.png](../images/image10.png?width=10pc)

بنابراین مقادیر را باید طوری تعیین کنیم که خروجی 
تابع $h$ بر حسب $x$ تا جای ممکن به مقادیر واقعی $y$ در
 مجموعه داده آموزشی نزدیک باشد.

$$ h_\theta(x) = \theta_0 + \theta_1x $$
$$ J(\theta_0,\theta_1) =  \frac{1}{2m} \sum_{i=1}^{m} (\hat{y_i} - y_i)^2 =  \frac{1}{2m} \sum_{i=1}^{m} (h_\theta(x) - y_i)^2 $$

بنابراین تابع هزینه $J$ را به این صورت تعریف می‌کنیم.
که 
**<span class="top-dict" data-tipso="squared error function">تابع خطای مجذور</span>**
نیز نامیده می‌شود، و هدف آن 
مینیمم کردن $\theta_0$ و $\theta_1$ است.
دلیل حضور $\frac{1}{2m}$ نیز برای این است که فرمول ریاضی
آسان تر شود، با قرار دادن 2 در کسر یعنی عبارت را
نصف می‌کنیم چون می‌دانیم که مینیمم کردن نصف
چیزی مثل مینیمم کردن همان چیز است!