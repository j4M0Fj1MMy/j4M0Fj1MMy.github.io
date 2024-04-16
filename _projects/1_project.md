---
layout: page
title: Calligraphy Generation
description: An Autoregressive Generative Model, pixel by pixel.
img: assets/img/calligraphy.jpg
importance: 1
category: project
# related_publications: einstein1956investigations, einstein1950meaning
---

{::nomarkdown}
{% assign jupyter_path = "assets/jupyter/autoregressive_model.ipynb" | relative_url %}
{% capture notebook_exists %}{% file_exists assets/jupyter/blog.ipynb %}{% endcapture %}
{% if notebook_exists == "true" %}
    {% jupyter_notebook jupyter_path %}
{% else %}
    <p>Sorry, the notebook you are looking for does not exist.</p>
{% endif %}
{:/nomarkdown}
