---
layout: page
title: Posts by Date
permalink: /archive/
sitemap: false
published: true
---

<div id="index">
    {% for post in site.posts %}
        {% unless post.next %}
            <h2>{{ post.date | date: '%Y' }}</h2>
        {% else %}
            {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
            {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
            {% if year != nyear %}
            {% if forloop.index != 1 %}{% endif %}
                <h2>{{ post.date | date: '%Y' }}</h2>
            {% endif %}
        {% endunless %}

    {% capture month %}{{ post.date | date: '%m%Y' }}{% endcapture %}
    {% capture nmonth %}{{ post.next.date | date: '%m%Y' }}{% endcapture %}
    {% if month != nmonth %}
    {% if forloop.index != 1 %}{% endif %}
        <h2>{{ post.date | date: '%B %Y' }}</h2>
    {% endif %}


    {% if post.link %}
        <h3 class="link-post">
            <a href="{{ post.url | prepend: site.baseurl }}" title="{{ post.title }}">{{ post.title }}</a>
            <a href="{{ post.link }}" target="_blank" title="{{ post.title }}"><i class="fa fa-link"></i></a></h3>
    {% else %}
        <h3><a href="{{ post.url | prepend: site.baseurl }}" title="{{ post.title }}">{{ post.title }} - <span class="date">{{ post.date |  date: "%e %B, %Y" }}</span></a></h3>
    {% endif %}
    {% endfor %}
  <br/>
</div>
