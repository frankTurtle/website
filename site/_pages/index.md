---
layout: archive
author_profile: true
permalink: /
---

# Hello

Welcome to my site! I'm still working on getting the hang of Jekyll, but check back in from time to time.

Thanks!

<h3 class="archive__subtitle">{{ site.data.ui-text[site.locale].recent_posts | default: "Recent Posts" }}</h3>

{% for post in site.posts %}
  <article>
    <h2>
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
    </h2>
    <time datetime="{{ post.date | date: "%Y-%m-%d" }}">{{ post.date | date_to_long_string }}</time>
    {{ post.content }}
  </article>
{% endfor %}

{% include paginator.html %}
