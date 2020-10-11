---
title: "Backpropagation قسمت اول"
date: 2020-10-01T12:30:31+03:30
draft: false
weight: 20
---

اصطلاح **Backpropagation** یا به فارسی **پس انتشار**
در شبکه های عصبی، برای به حداقل رساندن تابع هزینه (minimizing cost function)
مثل کاری که با گرادیان کاهشی در رگرسیون لجستیک و خطی انجام می‌دادیم، استفاده می‌شود.

هدف ما محاسبه این است:

$$
min_\Theta J(\Theta)
$$

یعنی می‌خواهیم تابع هزیه $J$ را با استفاده از یک محموعه
بهینه از پارامتر $\Theta$ به حداقل برسانیم
(یا به عبارتی دیگر مینیمم کنیم).

در این بخش به معادلاتی که برای محاسبه مشتق جزئی تابع $J(\Theta)$ استفاده می‌کنیم، خواهیم پرداخت:

$$
\frac{\partial}{\partial \Theta_ {i,j} ^{(l)}} J(\Theta)
$$

در Backpropagation ما برای هر گره (node) محاسبه خواهیم کرد:

$
= \delta_j ^{(l)}
$
خطا هر گره $j$ ام در لایه $l$

{{% notice note %}}
به خاطر آورید که 
$ \delta_j ^{(l)} $
گره فعال ساز $j$ در لایه $l$ است.
{{% /notice %}}

برای آخرین لایه یا همان لایه خروجی، می‌توانیم وکتور مقادیر دلتا را به این صورت حساب کنیم:
$$
\delta ^{(L)} = a ^{(L)} - y
$$

به طوری که $L$ تعداد کل لایه های ما است و
$a ^{(L)}$ وکتور خروجی گره های فعال ساز در آخرین لایه است.
بنابراین مقادیر خطای ما برای آخرین لایه، تفاوت نتایج واقعی در لایه آخر و خروجی صحیح در 
$y$ است.


برای محاسبه مقادیر دلتای، لایه های قبل از لایه آخر می‌توانیم از معادله ای استفاده کنیم که ما را از سمت راست به چپ عقب می‌‌برد:

$$
\delta ^{(l)} = ( (\Theta ^ {(l)}) ^ T  \delta ^ {(l+1)}) \hspace{0.2cm} .*  \hspace{0.2cm} {g}' (z^{(l)})
$$

مقادیر دلتای لایه $l$ با ضرب مقادیر دلتا در لایه بعدی با ماتریس تتا لایه $l$ محاسبه می‌شود،
سپس به صورت element-wise آن را در تابعی به اسم g-prime یا همان $g'$ ضرب می‌کنیم.

که $g'$ مشتق تابع فعال سازی $g$ است، و به عنوان ورودی $z^{(l)}$ را می‌گیرد.

بخش $g'$ را به صورت زیر نیز می‌توان نوشت:
$$
g'(u) = g(u) \hspace{0.2cm} .*  \hspace{0.2cm} (1 - g(u))
$$

و معادله کامل B‌ackpropagation برای گره های داخلی را به این شکل می‌نویسیم:
$$
\delta ^{(l)} = ( (\Theta ^ {(l)}) ^ T  \delta ^ {(l+1)}) \hspace{0.2cm} .*  \hspace{0.2cm} a^{(l)}
\hspace{0.2cm} .*  \hspace{0.2cm}  (1 -  a^{(l)})
$$

ما می‌توانیم با ضرب مقادیر فعال ساز در مقادیر خطا برای هر نمونه آموزشی $t$، 
مشتق جزئی خود را محاسبه کنیم:
$$
\frac{\partial}{\partial \Theta_ {i,j} ^{(l)}} J(\Theta) = \frac{1}{m} \sum_{t=1} ^m
a_j ^{(t) (l)} \delta _ i ^{(t) (l+1)}
$$

**نکته:**

$\delta ^{(l+1)}$ و $a ^{(l+1)}$
وکتور هایی با $s_ {l+1}$ عضو هستند و
$a ^ {(l)}$ وکتوری با $s_l$ عضو است،
که ضرب آن ها ماتریسی تولید می‌کند که $s_ {l+1}$ در  $s_l$  است،
که ابعاد آن شبیه به $\Theta^{(l)}$ است.

که این فرایند برای هر عنصر موجود در $\Theta^{(l)}$ گرادیان تولید می‌کند.

### الگوریتم Backpropagation

تصور کنید چنین مجموعه آموزشی داریم:
$
\\{  (x^{(1)}, y^{(1)}) ... (x^{(m)}, y^{(m)}) \\}
$

- تنظیم $\Delta _{i,j} ^{(l)} := 0 $ برای همه $(l,i,j)$ ها

برای نمونه آموزشی از $t=1$ تا $m$:

- تنظیم $a ^{(1)} := x ^{(t)}$
- برای انجام forward propagation محاسبه $a ^{(1)}$ برای $l = 1,2,3, ... , L$ را انجام می‌دهیم
- با استفاده از $y^{(t)}$ ، محاسبه $\delta ^{(L)} = a ^{(L)} - y^{(t)}$ را انجام می‌دهیم
- محاسبه $\delta^{(L-1)},\delta^{(L-2)}, ... , \delta^{(2)} $ با استفاده از $\delta ^{(l)} = ( (\Theta ^ {(l)}) ^ T  \delta ^ {(l+1)}) \hspace{0.2cm} .*  \hspace{0.2cm} a^{(l)}
\hspace{0.2cm} .*  \hspace{0.2cm}  (1 -  a^{(l)})$

- محاسبه $\Delta _{i,j} ^{(l)} := \Delta _{i,j} ^{(l)} + a_j ^{(l)} \delta _i ^{(l+1)} $ یا به صورت vectorization محاسبه $\Delta ^{(l)} := \Delta ^{(l)} + \delta ^{(l+1)} (a^{(l)})^ T$

- $D _{i,j} ^{(l)} := \frac{1}{m} (\Delta _{i,j} ^{(l)} + \lambda \Theta _{i,j} ^{(l)}) $ اگر $j \neq 0$ 

- $D _{i,j} ^{(l)} := \frac{1}{m} \Delta _{i,j} ^{(l)} $ اگر $j = 0$ 

ماتریس دلتا بزرگ یا همان $\Delta$ به عنوان **جمع کننده** (accumulator) برای جمع آوری
مقادیر ما در طول کار و محاسبه مشتق جزئی استفاده می‌شود.

اثبات واقعی این الگوریتم کاملا پیچیده است، همانطور که Andew Ng می‌گوید که 
استنتاج و اثبات آن پیچیده است، اما ما می‌توانیم از معادلات برای انجام کارمان استفاده کنیم بدون دانستن جزئیات آن.

و $D _{i,j} ^{(l)} $ جمله ای است که ما برای
مشتقات جزئی و نتایج به دنبال آن هستیم:

$$
D_ {i,j} ^{(l)} = \frac{\partial}{\partial \Theta_ {i,j} ^{(l)}} J(\Theta)
$$


![andrew-meme-1.webp](../images/andrew-meme-1.webp?width=30pc)
<p align="center" style="margin-top:-30px; margin-bottom: 50px; color: gray;" >
خلاصه که اینجوریه دیگه 😅
<p>