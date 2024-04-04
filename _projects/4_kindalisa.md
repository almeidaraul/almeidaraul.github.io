---
layout: page
title: KindaLisa
description: Compare LoL characters with Blackpink members using machine learning
img: assets/img/blackpink_lisa.jpg
importance: 3
category: github
---

This is a joke project to map each League of Legends
character to one of the four Blackpink members with
a deep neural network.

<div class="row">
    <div class="col">
        {% include figure.html path="assets/img/lol_champions.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
As there are many LoL champions, it would be ridiculous to do this mapping by hand. It is _not ridiculous at all_ to do it using a neural network.
</div>

The neural network is trained on recognizing blackpink
members. An important part of the project consists of
scraping an image search platform for photographs of
each member and then processing this data (resize, face
crop).

You can [check it out on GitHub](https://github.com/almeidaraul/kindalisa/).
