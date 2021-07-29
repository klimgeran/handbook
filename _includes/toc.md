{% for cat in site.data.global.categories %}

    {% assign pages=site.pages | where: "category", cat | where:"lang", "en" | sort:"order" %}

### {{ site.data.languages[page.lang].categories[cat] | default: site.data.languages["en"].categories[cat] }}

<ul>
    {% for p in pages %}
        {% if p.url == page.url %}
            {% continue %}
        {% endif %}
        {% assign tp=site.pages | where: "ref", p.ref | where:"lang", page.lang %}
        {% if tp.size > 0 %}
            <li>
                <a href="{{ tp[0].url | relative_url }}">{{ tp[0].title }}</a>
                {% if tp[0].version != p.version %}
                <span style="float:right">⚠️ {{site.data.languages[page.lang].outdated-translation}}</span>
                {% endif %}
                <br/>
                {{ tp[0].description }}
            </li>
        {% else %}
            <li class="missing_translation">
                <a href="{{ p.url | relative_url }}">{{ p.title }}</a>
                <span style="float:right">⚠️ {{site.data.languages[page.lang].missing-translation}}</span>
                <br/>
                {{ p.description }}
            </li>
        {% endif %}
    {% endfor %}
</ul>

{% endfor %}
