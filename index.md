---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

title: index
layout: default 
---
`openFlightHPC` is an open-source community developing a flexible, functional and HPC stack that can be launched on any platform.

By developing separate, modular tools, the process of designing, deploying and managing architecture to workflow can be effectively delivered. 

{% assign categories = site.pages | group_by: 'category' %}
{% for category in categories %}
    {% if category.name != "" %}
<h1>{{ category.name }}</h1>
    {% assign pages = category.items |sort: 'order' %}
    {% for page in pages %}
Page {{ page.title }} will be at {{ page.path }}
    {% endfor %}
    {% endif %}
{% endfor %}
