---
title: Research Group
language: en
tab: people          # 仅用于导航高亮，可保留
layout: default      # 关键：改成 default，不再用 feature
---

<!-- 引入简单内联样式；也可放在 main.css -->
<style>
.people-section{margin-bottom:3rem}
.people-section h2{border-bottom:2px solid #e0e0e8;padding-bottom:.3rem;margin-bottom:1rem;font-size:1.8rem}
.people-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:2rem}
.person-card{text-align:center}
.person-card img{width:140px;height:140px;border-radius:50%;object-fit:cover;margin-bottom:.5rem}
.person-card h3{margin:.3rem 0 .2rem;font-size:1.1rem}
.person-card .links a{margin:0 .2rem;font-size:1.2rem}
</style>

<!-- ================= PI ================= -->
<section class="people-section" id="pi">
  <h2>PI</h2>
  <div class="people-grid">
  {% assign list = site.people | where: "category","PI" | sort: "order" %}
  {% for person in list %}
    <div class="person-card">
      {% if person.image %}<img src="{{ person.image | relative_url }}" alt="{{ person.title }}">{% endif %}
      <h3><a href="{{ person.url | relative_url }}">{{ person.title }}</a></h3>
      <div class="links">
        {% for act in person.actions %}
          <a href="{{ act.url }}" title="{{ act.title }}" target="_blank" rel="noopener"><i class="{{ act.icon }}"></i></a>
        {% endfor %}
      </div>
    </div>
  {% endfor %}
  </div>
</section>

<!-- ================= Postdocs ================= -->
<section class="people-section" id="postdocs">
  <h2>Postdocs</h2>
  <div class="people-grid">
  {% assign list = site.people | where: "category","Postdoc" | sort: "order" %}
  {% for person in list %}
    <div class="person-card">
      {% if person.image %}<img src="{{ person.image | relative_url }}" alt="{{ person.title }}">{% endif %}
      <h3><a href="{{ person.url | relative_url }}">{{ person.title }}</a></h3>
      <div class="links">
        {% for act in person.actions %}
          <a href="{{ act.url }}" title="{{ act.title }}" target="_blank" rel="noopener"><i class="{{ act.icon }}"></i></a>
        {% endfor %}
      </div>
    </div>
  {% endfor %}
  </div>
</section>

<!-- ================= PhD Students ================= -->
<section class="people-section" id="phd">
  <h2>PhD Students</h2>
  <div class="people-grid">
  {% assign list = site.people | where: "category","PhD" | sort: "order" %}
  {% for person in list %}
    <div class="person-card">
      {% if person.image %}<img src="{{ person.image | relative_url }}" alt="{{ person.title }}">{% endif %}
      <h3><a href="{{ person.url | relative_url }}">{{ person.title }}</a></h3>
      <div class="links">
        {% for act in person.actions %}
          <a href="{{ act.url }}" title="{{ act.title }}" target="_blank" rel="noopener"><i class="{{ act.icon }}"></i></a>
        {% endfor %}
      </div>
    </div>
  {% endfor %}
  </div>
</section>

<!-- ================= Master Students ================= -->
<section class="people-section" id="master">
  <h2>Master Students</h2>
  <div class="people-grid">
  {% assign list = site.people | where: "category","Master" | sort: "order" %}
  {% for person in list %}
    <div class="person-card">
      {% if person.image %}<img src="{{ person.image | relative_url }}" alt="{{ person.title }}">{% endif %}
      <h3><a href="{{ person.url | relative_url }}">{{ person.title }}</a></h3>
      <div class="links">
        {% for act in person.actions %}
          <a href="{{ act.url }}" title="{{ act.title }}" target="_blank" rel="noopener"><i class="{{ act.icon }}"></i></a>
        {% endfor %}
      </div>
    </div>
  {% endfor %}
  </div>
</section>

<!-- ================= Alumni ================= -->
<section class="people-section" id="alumni">
  <h2>Alumni</h2>
  <div class="people-grid">
  {% assign list = site.people | where: "category","Alumni" | sort: "order" %}
  {% for person in list %}
    <div class="person-card">
      {% if person.image %}<img src="{{ person.image | relative_url }}" alt="{{ person.title }}">{% endif %}
      <h3><a href="{{ person.url | relative_url }}">{{ person.title }}</a></h3>
      <div class="links">
        {% for act in person.actions %}
          <a href="{{ act.url }}" title="{{ act.title }}" target="_blank" rel="noopener"><i class="{{ act.icon }}"></i></a>
        {% endfor %}
      </div>
    </div>
  {% endfor %}
  </div>
</section>