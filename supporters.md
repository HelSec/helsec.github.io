---
title: Supporters

layout: page
category: page-supporters
permalink: /supporters
---

{% for year in site.data.supporters %}

## Supporters for year {{ year[0] }}

<ul class="supporters">
  {% for supporter in year[1] %}
    <li><a href="{{ supporter["website"]}}"><img src="{{ site.baseurl }}assets/img/{{ supporter["logo_img"] }}" title="{{ supporter["name"] }}" alt="{{ supporter["name"] }}"/></a></li>
  {% endfor %}
</ul>
{% endfor %}

<hr />

## Supporter Membership

You can apply HelSec Ry supporter membership with this application. If you are looking to join HelSec as a member, you can do it here: [https://forms.gle/PRbLQXddCY9wZFoN6](https://forms.gle/PRbLQXddCY9wZFoN6)

After the application is reviewed, you will receive payment information for membership fee.

HelSec Ry management recommends membership fee of 1000 euros per year and we currently receive only bank transfers with reference number.

Supporter members will get following:

* Supporter status to our website and welcome presentation
* Right to participate in our HelSec Ry's spring and fall meetings
* Two seats to workshops organized by HelSec Ry
