---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

title: index
layout: default 
---
`openFlightHPC` is an open-source community developing a flexible, functional and stable HPC stack that can be launched on any platform.

By developing separate, modular tools, the process of designing, deploying and managing architecture to workflow can be effectively delivered. 

------

{%- assign collections = site.collections |sort: 'order' -%}
{%- for collection in collections -%}
{% if collection.label != "posts" %}
{% assign label = collection.label | split: '-' %}
## {% for word in label %}{{ word | capitalize }} {% endfor %}
    {% assign docs = collection.docs |sort: 'order' %}
    {% for page in docs %}
* [{{ page.title }}]({{ page.url }})
    {% assign h2 = page.content |split: '<h2' | shift %}
    {% for line in h2 %}
    {% assign entry = line |split: '/h2>' %}
    {% assign heading = entry |split: '"' %}
    {% assign id = heading[2] |remove: '\' %}
    {% assign title = heading[3] |remove: '<' |remove: '>' %}
    * [{{ title |capitalize }}]({{ page.url }}#{{ id }})
    {% endfor %}
    {% endfor %}
{% endif %}
{%- endfor -%}

------

{% assign categories = site.pages | group_by: 'category' %}
{% for category in categories %}
    {% if category.name != "" %}
# {{ category.name }}
    {% assign pages = category.items |sort: 'order' %}
    {% for page in pages %}
Page {{ page.title }} will be at {{ page.path }}
    {% endfor %}
    {% endif %}
{% endfor %}
