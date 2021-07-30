{% for cat in site.data.global.categories %}

    {% assign pages=site.pages | where: "category", cat | where:"lang", "en" | sort:"order" %}

### {{ site.data.languages[page.lang].categories[cat] | default: site.data.languages["en"].categories[cat] }}

<ul>
    {% for p in pages %}
        {% if p.url == page.url %}
            {% continue %}
        {% endif %}
        {% assign tp=site.pages | where: "ref", p.ref | where:"lang", page.lang | first %}
        {% if tp.size > 0 %}
            <li>
                <a href="{{ tp.url | relative_url }}">{{ tp.title }}</a>
                {% if tp.version != p.version %}
                <span style="float:right">⚠️ {{site.data.languages[page.lang].outdated-translation}}</span>
                {% endif %}
                <br/>
                {{ tp.description }}
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
