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
    {% assign title_shown = false %}
    {% for post in posts_in_category reversed %}
      {% if post.status == "published" or post.status == "working paper" %}
        {% unless title_shown %}
### {{ category[1].title }}
          {% assign title_shown = true %}
        {% endunless %}

- {{ post.title }}{% if post.authors %}. {{ post.authors | join: ", " }}{% endif %}{% if post.date %}. {{ post.date | date: "%B %Y" }}{% endif %}{% if post.status %}. {{ post.status }}{% endif %}

      {% endif %}
    {% endfor %}
  {% endfor %}
{% else %}
  {% for post in site.publications reversed %}
    {% if post.status == "published" or post.status == "working paper" %}
- {{ post.title }}{% if post.authors %}. {{ post.authors | join: ", " }}{% endif %}{% if post.date %}. {{ post.date | date: "%B %Y" }}{% endif %}{% if post.status %}. {{ post.status }}{% endif %}
    {% endif %}
  {% endfor %}
{% endif %}
