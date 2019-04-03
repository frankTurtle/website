---
layout: archive
author_profile: true
permalink: /
---

# Hello

This site is under construction. Most links do not work yet. When I get some free time - Hah! - I continue to update the content.

Thanks!

<h3 class="archive__subtitle">{{ site.data.ui-text[site.locale].recent_posts | default: "Recent Posts" }}</h3>

{% for post in paginator.posts %}

{% include archive-single.html %}

{% endfor %}

{% include paginator.html %}
