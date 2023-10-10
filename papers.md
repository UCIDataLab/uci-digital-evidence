---
layout: page
permalink: /papers/
title: Papers
description: (*) denotes equal contribution
years: [2022, 2020, 2017]
---

<div class="publications">

{% for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>



