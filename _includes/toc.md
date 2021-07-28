{% for cat in site.data.global.categories %}

    {% assign pages=site.pages | where: "category", cat | where:"lang", page.lang | sort:"order" %}
    {% if pages.size == 0 %}
        {% continue %}
    {% endif %}

### {{ site.data.languages[page.lang].categories[cat] | default: site.data.languages["en"].categories[cat] }}

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

{% endfor %}
