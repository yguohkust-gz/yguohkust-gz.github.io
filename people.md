---
title: Research Group
language: en
tab: people
layout: feature
---

<style>
/* 简单的分栏排版，可放到 _sass/people.scss 里统一管理 */
.people-section { margin-bottom: 3rem; }
.people-section h2 {
  border-bottom: 2px solid #e0e0e0;
  padding-bottom: 0.3rem;
  margin-bottom: 1rem;
  font-size: 1.8rem;
}
.people-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 2rem;
}
.person-card {
  text-align: center;
}
.person-card img {
  width: 140px;
  height: 140px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 0.5rem;
}
.person-card h3 { margin: 0.3rem 0 0.2rem; font-size: 1.1rem; }
.person-card .links a { margin: 0 0.2rem; font-size: 1.2rem; }
</style>

<!-- =============== PI =============== -->
<section class="people-section" id="pi">
  <h2>PI</h2>
  <div class="people-grid">
  {% for person in site.people %}
    {% if person.category == "PI" %}
      <div class="person-card">
        {% if person.image %}<img src="{{ person.image | relative_url }}" alt="{{ person.title }}">{% endif %}
        <h3><a href="{{ person.url | relative_url }}">{{ person.title }}</a></h3>
        <div class="links">
          {% for act in person.actions %}
            <a href="{{ act.url }}" title="{{ act.title }}" target="_blank" rel="noopener"><i class="{{ act.icon }}"></i></a>
          {% endfor %}
        </div>
      </div>
    {% endif %}
  {% endfor %}
  </div>
</section>

<!-- =============== Postdocs =============== -->
<section class="people-section" id="postdocs">
  <h2>Postdocs</h2>
  <div class="people-grid">
  {% for person in site.people %}
    {% if person.category == "Postdoc" %}
      <div class="person-card">
        {% if person.image %}<img src="{{ person.image | relative_url }}" alt="{{ person.title }}">{% endif %}
        <h3><a href="{{ person.url | relative_url }}">{{ person.title }}</a></h3>
        <div class="links">
          {% for act in person.actions %}
            <a href="{{ act.url }}" title="{{ act.title }}" target="_blank" rel="noopener"><i class="{{ act.icon }}"></i></a>
          {% endfor %}
        </div>
      </div>
    {% endif %}
  {% endfor %}
  </div>
</section>

<!-- =============== PhD Students =============== -->
<section class="people-section" id="phd">
  <h2>PhD Students</h2>
  <div class="people-grid">
  {% for person in site.people %}
    {% if person.category == "PhD" %}
      <div class="person-card">
        {% if person.image %}<img src="{{ person.image | relative_url }}" alt="{{ person.title }}">{% endif %}
        <h3><a href="{{ person.url | relative_url }}">{{ person.title }}</a></h3>
        <div class="links">
          {% for act in person.actions %}
            <a href="{{ act.url }}" title="{{ act.title }}" target="_blank" rel="noopener"><i class="{{ act.icon }}"></i></a>
          {% endfor %}
        </div>
      </div>
    {% endif %}
  {% endfor %}
  </div>
</section>

<!-- =============== Master Students =============== -->
<section class="people-section" id="master">
  <h2>Master Students</h2>
  <div class="people-grid">
  {% for person in site.people %}
    {% if person.category == "Master" %}
      <div class="person-card">
        {% if person.image %}<img src="{{ person.image | relative_url }}" alt="{{ person.title }}">{% endif %}
        <h3><a href="{{ person.url | relative_url }}">{{ person.title }}</a></h3>
        <div class="links">
          {% for act in person.actions %}
            <a href="{{ act.url }}" title="{{ act.title }}" target="_blank" rel="noopener"><i class="{{ act.icon }}"></i></a>
          {% endfor %}
        </div>
      </div>
    {% endif %}
  {% endfor %}
  </div>
</section>

<!-- =============== Alumni =============== -->
<section class="people-section" id="alumni">
  <h2>Alumni</h2>
  <div class="people-grid">
  {% for person in site.people %}
    {% if person.category == "Alumni" %}
      <div class="person-card">
        {% if person.image %}<img src="{{ person.image | relative_url }}" alt="{{ person.title }}">{% endif %}
        <h3><a href="{{ person.url | relative_url }}">{{ person.title }}</a></h3>
        <div class="links">
          {% for act in person.actions %}
            <a href="{{ act.url }}" title="{{ act.title }}" target="_blank" rel="noopener"><i class="{{ act.icon }}"></i></a>
          {% endfor %}
        </div>
      </div>
    {% endif %}
  {% endfor %}
  </div>
</section>