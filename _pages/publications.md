---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if site.author.googlescholar %}
  <div class="wordwrap">You can also find my articles on <a href="{{ site.author.googlescholar }}">my Google Scholar profile</a>.</div>
{% endif %}

{% include base_path %}

{% if site.publication_category %}
  {% for category in site.publication_category %}
    {% assign posts_in_category = site.publications | where: "category", category[0] %}
    {% assign title_shown = false %}
    {% for post in posts_in_category reversed %}
      {% if post.status == "published" or post.status == "working paper" %}
        {% unless title_shown %}
## {{ category[1].title }}
          {% assign title_shown = true %}
        {% endunless %}
        {% include archive-single.html %}
      {% endif %}
    {% endfor %}
  {% endfor %}
{% else %}
  {% for post in site.publications reversed %}
    {% if post.status == "published" or post.status == "working paper" %}
      {% include archive-single.html %}
    {% endif %}
  {% endfor %}
{% endif %}
