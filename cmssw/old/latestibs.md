---
title: CMS Offline Software
layout: default
related:
  - name: Project page
    link: 'https://github.com/cms-sw/cmssw'
  - name: Feedback
    link: 'https://github.com/cms-sw/cmssw/issues/new'
---

# latestIBs

|  {% assign previous\_name = '' %} {% for arch in sortedArchs %} |  {% assign name = arch \| split:"\_" %} {% if previous\_name != name\[0\] %} {{ name\[0\] }} {% endif %} {% assign previous\_name = name\[0\] %} {% endfor %} |
| --- | --- | --- | --- | --- | --- |
|  {% assign previous\_name = '' %} {% assign previous\_os = '' %} {% for arch in sortedArchs %} |  {% assign name = arch \| split:"\_" %} {% if previous\_name != name\[1\] or previous\_os != name\[0\]%} {{ name\[1\] }} {% endif %} {% assign previous\_name = name\[1\] %} {% assign previous\_os = name\[0\] %} {% endfor %} |
|  {% for arch in sortedArchs %} |  {% assign name = arch \| split:"\_" %} {{ name\[2\] }} {% endfor %} |
|  {% for releaseQueue in sortedReleaseQueues reversed %} {% if releaseQueue\[0\] != 'all\_archs' %} |  |
|  {{ releaseQueue\[0\] }} {% for arch in sortedArchs %} |  {% if releaseQueue\[1\] contains arch %} {% assign ib\_name\_parts = releaseQueue\[1\]\[arch\]\['latest\_IB'\] \| split:"\_201" %} {% if releaseQueue\[1\]\[arch\]\['status'\] == 'ok' %} {% assign text\_color = 'green' %} {% elsif releaseQueue\[1\]\[arch\]\['status'\] == 'unknown' %} {% assign text\_color = 'gray' %} {% elsif releaseQueue\[1\]\[arch\]\['status'\] == 'warning' %} {% assign text\_color = 'GoldenRod' %} {% else %} {% assign text\_color = 'red' %} {% endif %} [201{{ ib\_name\_parts\[1\] }}](http://cms-sw.github.io/showIB.html#{{%20releaseQueue[1][arch]['latest_IB']%20}}) {% endif %} {% endfor %} |
|  {% endif %} {% endfor %} |  |



