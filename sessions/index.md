---
layout: page
title:  Sessions Notes
---

{% comment %}
The code below dynamically generates a sidebar nav of pages with
`layout: page` in the front-matter. See readme for usage.


<ul>
{% for page in site.session %}
{% if page.session == true %}

<entry>
 <li>Session {{ page.session_number }} &middot; <a href="{{ page.url }}">{{ page.title }}</a>
 </li>
</entry>

{% endif %}
{% endfor %}
</ul>
{% endcomment %}

<li>Session 1 - [welcome to backends for mobile application](http://uchicago.cloud/sessions/session1/)</li>
<li>Session 2 - [google app engine](http://uchicago.cloud/sessions/session2/)</li>

{% comment %}
<h1>Final Project Requirements</h1>
* Final project [checklist](https://{{ site.cdn }}/MPCS51030/2015-Winter/2015-Winter-FinalProjectRequirements.pdf)
{% endcomment %}
