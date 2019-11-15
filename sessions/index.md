---
layout: page
title:  Sessions Notes
---

{% comment %}
The code below dynamically generates a sidebar nav of pages with
`layout: page` in the front-matter. See readme for usage.
{% endcomment %}

<ul>
{% for page in site.pages | sort:"title" %}
{% if page.session == true %}

<entry>
 <li>Session {{ page.session_number }} &middot; <a href="{{ page.url }}">{{ page.title }}</a>
 </li>
</entry>

{% endif %}
{% endfor %}
</ul>



{% comment %}
<h1>Final Project Requirements</h1>
* Final project [checklist](https://{{ site.cdn }}/MPCS51030/2015-Winter/2015-Winter-FinalProjectRequirements.pdf)
{% endcomment %}
