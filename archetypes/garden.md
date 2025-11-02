---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
type: garden
date: {{ .Date }}
created: {{ now.Format "2006-01-02 Mon 3:04pm" }}
updated: {{ now.Format "2006-01-02 Mon 3:04pm" }}
state: seed
tags: []
share: true
---

Your garden entry content goes here.

<!-- Example of Dataview-style metadata (optional) -->
<!--
- [category::thought]
- [inspiration::source]
-->
