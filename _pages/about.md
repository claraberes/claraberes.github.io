---
permalink: /
title: "Clara Berestycki"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

Welcome to my website! I am a 5th-year PhD student in the [Sustainable Development program](https://www.sipa.columbia.edu/sipa-education/phd-sustainable-development) at Columbia University's School of International and Public Affairs. 

I am an environmental economist with research interests in spatial mobility, air pollution, behavioral responses, and green innovation. 

Before starting the PhD, I graduated from Ecole Normale Supérieure Paris-Saclay. I hold a Master in Economics from ENSAE and Ecole Polytechnique and obtained bachelor degrees in economics, sociology and philosophy from Sorbonne University. I also worked as consultant in the Environment Directorate at the OECD. 

Don't hesitate to be in touch! 

# Research
{% if site.author.googlescholar %}
You can also find my articles on [my Google Scholar profile]({{ site.author.googlescholar }}).
{% endif %}
{% if site.publication_category %}
  {% for category in site.publication_category %}
    {% assign posts_in_category = site.publications | where: "category", category[0] %}
    {% assign posts_in_category = posts_in_category | sort: "date" | reverse %}
    {% if posts_in_category.size > 0 %}
### {{ category[1].title }}
      {% for post in posts_in_category %}
{% assign data_link = post.dataurl | default: post.data_url | default: post.data.url | strip %}
- {% if post.citation %}{{ post.citation }}{% else %}{{ post.authors | join: " & " }}{% if post.date %}, {{ post.date | date: "%B %Y" }}{% endif %}. "{{ post.title }}"{% if post.series %}. *{{ post.series }}*{% endif %}{% if post.number %} No. {{ post.number }}{% endif %}{% endif %}{% if post.paperurl %}. [Download paper]({{ post.paperurl }}){% endif %}{% if data_link != "" %}. [Download data]({{ data_link }}){% endif %}
{% if post.note %}  <br> *{{ post.note }}*{% endif %}
      {% endfor %}
    {% endif %}
  {% endfor %}
{% else %}
  {% assign all_posts = site.publications | sort: "date" | reverse %}
  {% for post in all_posts %}
{% assign data_link = post.dataurl | default: post.data_url | default: post.data.url | strip %}
- {% if post.citation %}{{ post.citation }}{% else %}{{ post.authors | join: " & " }}{% if post.date %}, {{ post.date | date: "%B %Y" }}{% endif %}. "{{ post.title }}"{% if post.series %}. *{{ post.series }}*{% endif %}{% if post.number %} No. {{ post.number }}{% endif %}{% endif %}{% if post.paperurl %}. [Download paper]({{ post.paperurl }}){% endif %}{% if data_link != "" %}. [Download data]({{ data_link }}){% endif %}
  {% endfor %}
{% endif %}
