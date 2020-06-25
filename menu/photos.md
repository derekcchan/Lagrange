---
layout: photos
title: Photos
---
<ul class="photos">
  {% for photos in site.photos %}

    {% unless photos.next %}
      <h3>{{ photos.date | date: '%Y' }}</h3>
    {% else %}
      {% capture year %}{{ photos.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ photos.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <h3>{{ photos.date | date: '%Y' }}</h3>
      {% endif %}
    {% endunless %}

    <li itemscope>
      <a href="{{ site.github.url }}{{ photos.url }}">{{ photos.title }}</a>
      <p class="photos-date"><span><i class="fa fa-calendar" aria-hidden="true"></i> {{ photos.date | date: "%B %-d" }} - <i class="fa fa-clock-o" aria-hidden="true"></i> {% include read-time.html %}</span></p>
    </li>

  {% endfor %}
</ul>
