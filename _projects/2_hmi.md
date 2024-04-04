---
layout: page
title: HMI
description: Calculate insulin dosage
importance: 2
img: assets/img/hmi_header.jpg
category: github
---

HMI (How Much Insulin) is an insulin dosage calculator for
carbohydrate-counting diabetes patients under insulin
therapy. Counting carbohydrates consists of taking insulin
according to some conditions (instead of taking a fixed
amount at a fixed time of day), and can better simulate a
natural pancreas.

These conditions are usually how high or low your blood
sugar is right now, how many grams of carbohydrates you
are about to consume (when dosaging before a meal) and
what time of day it is (your body might need more
insulin in the morning, for example).

HMI takes into account these three parameters and calculates
how many insulin units you should take. The way this dosage
is calculated can also be configured by the user.

<div class="text-center">
    {% include figure.html path="assets/img/hmi_screenshot.png" class="img-fluid rounded z-depth-1 mx-auto" zoomable=true %}
</div>
<div class="caption">
A screenshot of the dosage calculator view in HMI
</div>

Read more about HMI in
[its GitHub page](https://github.com/almeidaraul/hmi/) and
more about carbohydrate counting in
[its Wikipedia article](https://en.wikipedia.org/wiki/Carbohydrate_counting).
