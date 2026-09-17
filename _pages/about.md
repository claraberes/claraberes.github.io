---
permalink: /
title: "Clara Berestycki"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I am a 6th-year PhD student in the [Sustainable Development program](https://www.sipa.columbia.edu/sipa-education/phd-sustainable-development) at Columbia University's School of International and Public Affairs. I am an environmental economist working on climate change adaptation with interests in spatial mobility, air pollution, and green innovation. 

Before starting the PhD, I graduated from Ecole Normale Supérieure Paris-Saclay and worked as consultant at the OECD. I hold a Master in Economics from ENSAE and Ecole Polytechnique. Please find my CV <a href="/files/cv_clara_berestycki.pdf" target="_blank">here</a>.

**I am on the 2026-27 job market.** 
{% if site.publication_category %}
  {% for category in site.publication_category %}
    {% assign posts_in_category = site.publications | where: "category", category[0] %}
    {% assign posts_in_category = posts_in_category | sort: "date" | reverse %}
    {% if posts_in_category.size > 0 %}
### {{ category[1].title }}
      {% for post in posts_in_category %}
{% assign data_link = post.dataurl | default: post.data_url | default: post.data.url | strip %}
{% if post.coauthors or post.links or post.status %}
<div class="pub">
<span class="pub-title">{{ post.title }}</span><br>
{% if post.coauthors %}<span class="pub-meta">with {{ post.coauthors }}</span><br>{% endif %}
{% if post.status or post.venue %}<span class="pub-meta">{% if post.status %}<em>{{ post.status }}</em>{% if post.venue %}, {% endif %}{% endif %}{% if post.venue %}<strong>{{ post.venue }}</strong>{% endif %}</span><br>{% endif %}
{% if post.links or data_link != "" %}<span class="pub-links">{% for l in post.links %}<a href="{{ l.url }}" target="_blank" rel="noopener">[{{ l.label }}]</a>{% endfor %}{% if data_link != "" %}<a href="{{ data_link }}" target="_blank" rel="noopener">[Data]</a>{% endif %}</span>{% endif %}
{% if post.note %}<br><span class="pub-meta"><em>{{ post.note }}</em></span>{% endif %}
</div>
{% else %}
- {% if post.citation %}{{ post.citation }}{% else %}{{ post.authors | join: " & " }}{% if post.date %}, {{ post.date | date: "%B %Y" }}{% endif %}. "{{ post.title }}"{% if post.series %}. *{{ post.series }}*{% endif %}{% if post.number %} No. {{ post.number }}{% endif %}{% endif %}{% if post.paperurl %}. [Download paper]({{ post.paperurl }}){% endif %}{% if data_link != "" %}. [Download data]({{ data_link }}){% endif %}
{% if post.note %}  <br> *{{ post.note }}*{% endif %}
{% endif %}
      {% endfor %}
    {% endif %}
  {% endfor %}
{% else %}
  {% assign all_posts = site.publications | sort: "date" | reverse %}
  {% for post in all_posts %}
{% assign data_link = post.dataurl | default: post.data_url | default: post.data.url | strip %}
{% if post.coauthors or post.links or post.status %}
<div class="pub">
<span class="pub-title">{{ post.title }}</span><br>
{% if post.coauthors %}<span class="pub-meta">with {{ post.coauthors }}</span><br>{% endif %}
{% if post.status or post.venue %}<span class="pub-meta">{% if post.status %}<em>{{ post.status }}</em>{% if post.venue %}, {% endif %}{% endif %}{% if post.venue %}<strong>{{ post.venue }}</strong>{% endif %}</span><br>{% endif %}
{% if post.links or data_link != "" %}<span class="pub-links">{% for l in post.links %}<a href="{{ l.url }}" target="_blank" rel="noopener">[{{ l.label }}]</a>{% endfor %}{% if data_link != "" %}<a href="{{ data_link }}" target="_blank" rel="noopener">[Data]</a>{% endif %}</span>{% endif %}
{% if post.note %}<br><span class="pub-meta"><em>{{ post.note }}</em></span>{% endif %}
</div>
{% else %}
- {% if post.citation %}{{ post.citation }}{% else %}{{ post.authors | join: " & " }}{% if post.date %}, {{ post.date | date: "%B %Y" }}{% endif %}. "{{ post.title }}"{% if post.series %}. *{{ post.series }}*{% endif %}{% if post.number %} No. {{ post.number }}{% endif %}{% endif %}{% if post.paperurl %}. [Download paper]({{ post.paperurl }}){% endif %}{% if data_link != "" %}. [Download data]({{ data_link }}){% endif %}
{% endif %}
  {% endfor %}
{% endif %}
