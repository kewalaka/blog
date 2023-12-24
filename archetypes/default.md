---
date: '{{ .Date }}'
description: ''
title: '{{ replace .File.ContentBaseName `-` ` ` | title }}'
slug: '{{ .Date | time.Format "2006" }}/{{ .Date | time.Format "01" }}/{{ .File.ContentBaseName }}'
image: ''
categories:
 -
tags:
 -
draft: true
---
