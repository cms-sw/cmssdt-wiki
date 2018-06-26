---
title: CMS Offline Software
layout: default
related:
  - name: Project page
    link: 'https://github.com/cms-sw/cmssw'
  - name: Feedback
    link: 'https://github.com/cms-sw/cmssw/issues/new'
---

# categories

## L1 Conveners

*  {% for person in site.data.categories.L1 %}
*  [{{ person }}](https://github.com/{{%20person%20}})
*  {% endfor %}

## L2 Conveners

*  {% for category in site.data.categories.categories\_to\_people %}
*  **{{ category\[0\] }}:** {% for person in category\[1\] %} [{{ person }}](https://github.com/{{%20person%20}}) {% endfor %}
*  {% endfor %}

## Package Categories

*  {% for category in site.data.categories.categories\_to\_packages %}
*  **{{ category\[0\] \| capitalize }}**
  *  {% for package in category\[1\] %}
  *  {{ package }}
  *  {% endfor %}
*  {% endfor %}

