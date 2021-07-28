---
title: "Selamat bergabung!"
lang: id
ref: welcome
---

![Welcome](../images/welcome.jpg){:width="100%"}

Inilah yang akan Anda temukan di dalam pedoman ini:

<!--
List all pages in the site which match the language of THIS page, sorted
by their "order" property, excluding THIS page.
 -->
{% assign pages=site.pages | where:"lang", page.lang | sort:"order" %}
<ul>
{% for p in pages %}
    {% if p.url != page.url %}
        <li>
            <a href="{{ p.url }}">{{ p.title }}</a><br/>
            {{ p.description }}
        </li>
    {% endif %}
{% endfor %}
</ul>
