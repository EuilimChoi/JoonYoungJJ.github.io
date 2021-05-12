---
title: "굿노트 템플릿"
layout: archive
permalink: categories/template
author_profile: true
sidebar_main: true
---


{% assign posts = site.categories['template'] %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}