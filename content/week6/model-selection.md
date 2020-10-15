---
title: "انتخاب مدل"
date: 2020-10-15T17:25:10+03:30
draft: false
weight: 20
---


فقط به این دلیل که یک الگوریتم یادگیری متناسب با مجموعه آموزشی ما است، به این معنی نیست که آن فرضیه خوبی است!

می‌تواند overfit شده باشد، که در نتیجه پیش بینی های شما برای
مجموعه آزمون ضعیف خواهد بود.

اگر خطای فرضیه خود را با داده هایی که با آن پارامتر ها را آموزش داده اید محاسبه کنید،
کمتر از مجموعه داده های دیگر خواهد بود!

برای انتخاب مدل خود، می‌توانید هر درجه از چند جمله ای ها را آزمایش کرده و به نتیجه خطای آن توجه کنید.

**بدون مجموعه اعتبار سنجی:**

(توجه داشته باشید: این روش بدی است - از آن استفاده نکنید!)

- بهنیه سازی پارامتر های $\Theta$، با استفاده از مجموعه آموزشی برای هر یک از درجات چند جمله ای.
- با استفاده از مجموعه آزمون، درجه چند جمله ای d را که کمترین خطا را دارد پیدا کنید.
- خطای تعمیم را با استفاده از مجموعه آزمون محاسبه کنید $J_{test}(\Theta^{d})$

در این حالت ما متغیر d یا درجه چند جمله ای را با استفاده از مجموعه آزمون آموزش می‌دهیم.

**CV set:**

برای انجام این کار می‌توانیم از مجموعه  Cross Validation به عناون یک مجموعه میانی برای آموزش دادن d استفاده کنیم، و سپس
مجموعه آزمون خطایی دقیق و غیر خوش بینانه  به ما می‌دهد.

یکی از روش های تجزیه مجموعه داده مان به سه مجموعه این است:
- مجموعه آموزشی: ۶۰ درصد
- مجموعه cross validation:  درصد ۲۰
- مجموعه آزمون: ۲۰ درصد

اکنون می توانیم سه مقدار خطای جداگانه را برای سه مجموعه مختلف محاسبه کنیم.

**با مجموعه اعتبار سنجی:**