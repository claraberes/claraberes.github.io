---
permalink: /
title: "Clara Berestycki"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---
<style>
  h1 { margin-bottom: 0.2em; }
  h1 + h3, h1 + p:empty + h3 { margin-top: 0.3em; }
  p:empty { display: none; }

  .pub { position: relative; padding-left: 1.2em; margin-bottom: 1.6em; line-height: 1.55; }
  .pub::before { content: "•"; position: absolute; left: 0; top: 0; opacity: 0.6; }
  a.pub-title { font-weight: 700; font-size: 1.05em; text-decoration: none; }
  a.pub-title:hover { text-decoration: underline; }
  .pub-meta { opacity: 0.8; font-size: 0.93em; }
  .pub-links a { margin-right: 0.85em; font-size: 0.9em; text-decoration: none; opacity: 0.75; }
  .pub-links a:hover { opacity: 1; }
</style>

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
{% assign title_url = post.links[0].url | default: post.paperurl | default: post.permalink %}
<div class="pub">
<div>{% if title_url and title_url != "" %}<a class="pub-title" href="{{ title_url }}" target="_blank" rel="noopener">{{ post.title }}</a>{% else %}<span class="pub-title">{{ post.title }}</span>{% endif %}</div>
{% if post.coauthors != "" and post.coauthors %}<div class="pub-meta">with {{ post.coauthors }}</div>{% endif %}
{% if post.status or post.venue %}<div class="pub-meta">{% if post.status %}<em>{{ post.status }}</em>{% if post.venue %}, {% endif %}{% endif %}{% if post.venue %}<strong>{{ post.venue }}</strong>{% endif %}</div>{% endif %}
{% if post.links or data_link != "" %}<div class="pub-links">{% for l in post.links %}<a href="{{ l.url }}" target="_blank" rel="noopener">[{{ l.label }}]</a>{% endfor %}{% if data_link != "" %}<a href="{{ data_link }}" target="_blank" rel="noopener">[Data]</a>{% endif %}</div>{% endif %}
{% if post.note %}<div class="pub-meta"><em>{{ post.note }}</em></div>{% endif %}
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
{% assign title_url = post.links[0].url | default: post.paperurl | default: post.permalink %}
<div class="pub">
<div>{% if title_url and title_url != "" %}<a class="pub-title" href="{{ title_url }}" target="_blank" rel="noopener">{{ post.title }}</a>{% else %}<span class="pub-title">{{ post.title }}</span>{% endif %}</div>
{% if post.coauthors != "" and post.coauthors %}<div class="pub-meta">with {{ post.coauthors }}</div>{% endif %}
{% if post.status or post.venue %}<div class="pub-meta">{% if post.status %}<em>{{ post.status }}</em>{% if post.venue %}, {% endif %}{% endif %}{% if post.venue %}<strong>{{ post.venue }}</strong>{% endif %}</div>{% endif %}
{% if post.links or data_link != "" %}<div class="pub-links">{% for l in post.links %}<a href="{{ l.url }}" target="_blank" rel="noopener">[{{ l.label }}]</a>{% endfor %}{% if data_link != "" %}<a href="{{ data_link }}" target="_blank" rel="noopener">[Data]</a>{% endif %}</div>{% endif %}
{% if post.note %}<div class="pub-meta"><em>{{ post.note }}</em></div>{% endif %}
</div>
{% else %}
- {% if post.citation %}{{ post.citation }}{% else %}{{ post.authors | join: " & " }}{% if post.date %}, {{ post.date | date: "%B %Y" }}{% endif %}. "{{ post.title }}"{% if post.series %}. *{{ post.series }}*{% endif %}{% if post.number %} No. {{ post.number }}{% endif %}{% endif %}{% if post.paperurl %}. [Download paper]({{ post.paperurl }}){% endif %}{% if data_link != "" %}. [Download data]({{ data_link }}){% endif %}
{% endif %}
  {% endfor %}
{% endif %}
