---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

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
- {{ post.title }}{% if post.authors %}. {{ post.authors | join: ", " }}{% endif %}{% if post.date %}. {{ post.date | date: "%B %Y" }}{% endif %}{% if post.status == "working paper" %}. *Submitted*{% endif %}{% if post.paperurl %}. [Download paper]({{ post.paperurl }}){% endif %}
{% if post.note %}  <br> *{{ post.note }}*{% endif %}
      {% endfor %}
    {% endif %}
  {% endfor %}
{% else %}
  {% assign all_posts = site.publications | sort: "date" | reverse %}
  {% for post in all_posts %}
- {{ post.title }}{% if post.authors %}. {{ post.authors | join: ", " }}{% endif %}{% if post.date %}. {{ post.date | date: "%B %Y" }}{% endif %}{% if post.status == "working paper" %}. *Submitted*{% endif %}{% if post.paperurl %}. [Download paper]({{ post.paperurl }}){% endif %}
  {% endfor %}
{% endif %}
