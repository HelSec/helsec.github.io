---
title: About

layout: page
category: page-about
permalink: /about
---

Cybersecurity group by the community, for the community.

<div>
<h2>Organizers</h2>
{% for organizer in site.data.organizers %}

  <li class="organizer">
    <img src="/assets/avatars/{{organizer.nickname}}.png" height="100px">
    <p> {{organizer.nickname}} </p>
    <ul class="list-inline qtext-center">
    <li><a href="{{organizer.twitter}}" class="btn-social btn-outline"><i class="fa fa-fw fa-twitter"></i></a></li>
    <li><a href="{{organizer.linkedin}}" class="btn-social btn-outline"><i class="fa fa-fw fa-linkedin"></i></a></li>
    </ul>
  </li>
{% endfor %}
</div>

## Contact

Drop us an email to {{ site.email }}
