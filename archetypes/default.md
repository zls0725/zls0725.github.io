<<<<<<< HEAD
+++
date = '{{ .Date }}'
draft = true
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
+++
=======
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
---

>>>>>>> 1cbf1ba8693f3e7cceb538d49f4060410de4abf3
