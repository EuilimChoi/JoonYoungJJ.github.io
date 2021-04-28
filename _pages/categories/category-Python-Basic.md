---
title: "파이썬 기초"
layout: archive
permalink: categories/python-basic
author_profile: true
sidebar_main: true
---


{% assign posts = site.categories['python-basic'] %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}