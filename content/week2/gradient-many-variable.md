---
title: "گرادیان کاهشی چند متغیره"
date: 2020-09-09T21:27:26+04:30
draft: false
weight : 20
---

الگوریتم جدید ما برای گرادیان کاهشی با چندین متغیر
به این صورت است:

![image61.png](../images/image61.png?width=25pc)

و قسمت $ \frac{1}{m} \sum_{i=1}^m (h_\theta(x^{(i)}) - y^{(i)} ) x_j^{(i)} $ همان مشتق جرئی $\frac {\partial} {\partial\theta_0} J(\theta)$ است.

به طور مثال برای دو متغیره و یا بیشتر خواهیم داشت:

![image64.png](../images/image64.png?width=25pc)

{{% notice note %}}
یادآوری:  مقدار $x_0$ برابر $1$ است.
{{% /notice %}}
