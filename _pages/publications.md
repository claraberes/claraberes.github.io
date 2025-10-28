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
    {% assign posts_in_category = posts_in_category | where_exp: "item", "item.status == 'published' or item.status == 'working paper'" %}
    {% if posts_in_category.size > 0 %}
      <h2>{{ category[1].title }}</h2><hr />
      {% for post in posts_in_category reversed %}
        {% include archive-single.html %}
      {% endfor %}
    {% endif %}
  {% endfor %}
{% else %}
  {% for post in site.publications reversed %}
    {% if post.status == "published" or post.status == "working paper" %}
      {% include archive-single.html %}
    {% endif %}
  {% endfor %}
{% endif %}
