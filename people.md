---
title: Research Group
language: en
tab: people
layout: feature
---

{% comment %}
  默认用文件名前缀区分（更省事）：
  PI_xxx.md        -> PI
  Postdoc_xxx.md   -> Postdoc
  PhD_xxx.md       -> PhD
  Master_xxx.md    -> Master
  Alumni_xxx.md    -> Alumni
  如果你想用 YAML 里的 category 字段，把下面 assign 里的判断改掉即可。
{% endcomment %}

<section id="PI">
  <h2>PI</h2>
  <div class="people-grid">
  {% for p in site.people %}
    {% assign name = p.path | split:'/' | last %}
    {% if name contains 'PI_' %}
      <div class="person-card">{% include person-card.html person=p %}</div>
    {% endif %}
  {% endfor %}
  </div>
</section>

<section id="Postdocs">
  <h2>Postdocs</h2>
  <div class="people-grid">
  {% for p in site.people %}
    {% assign name = p.path | split:'/' | last %}
    {% if name contains 'Postdoc_' %}
      <div class="person-card">{% include person-card.html person=p %}</div>
    {% endif %}
  {% endfor %}
  </div>
</section>

<section id="PhD">
  <h2>PhD Students</h2>
  <div class="people-grid">
  {% for p in site.people %}
    {% assign name = p.path | split:'/' | last %}
    {% if name contains 'PhD_' %}
      <div class="person-card">{% include person-card.html person=p %}</div>
    {% endif %}
  {% endfor %}
  </div>
</section>

<section id="Master">
  <h2>Master Students</h2>
  <div class="people-grid">
  {% for p in site.people %}
    {% assign name = p.path | split:'/' | last %}
    {% if name contains 'Master_' %}
      <div class="person-card">{% include person-card.html person=p %}</div>
    {% endif %}
  {% endfor %}
  </div>
</section>

<section id="Alumni">
  <h2>Alumni</h2>
  <div class="people-grid">
  {% for p in site.people %}
    {% assign name = p.path | split:'/' | last %}
    {% if name contains 'Alumni_' %}
      <div class="person-card">{% include person-card.html person=p %}</div>
    {% endif %}
  {% endfor %}
  </div>
</section>