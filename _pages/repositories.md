---
layout: page
permalink: /repositories/
title: Repositories
description: My GitHub activity, top repositories, and contribution trophies.
nav: true
nav_order: 4
---

<style>
  .repositories {
    gap: 5px !important;
  }

  .repositories .repo {
    flex: 1 1 48%;
    margin-bottom: 8px !important;
    padding-bottom: 0 !important;
    padding-top: 0 !important;
  }

  @media (max-width: 768px) {
    .repositories .repo {
      flex: 1 1 100%;
    }
  }
</style>

{% if site.data.repositories.github_users %}

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for user in site.data.repositories.github_users %}
    {% include repository/repo_user.liquid username=user %}
  {% endfor %}
</div>

{% if site.repo_trophies.enabled %}
{% for user in site.data.repositories.github_users %}
{% if site.data.repositories.github_users.size > 1 %}

  <h4>{{ user }}</h4>
  {% endif %}
  <div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% include repository/repo_trophies.liquid username=user %}
  </div>

{% endfor %}
{% endif %}
{% endif %}

<br>

{% if site.data.repositories.github_repos %}

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.liquid repository=repo %}
  {% endfor %}
</div>
{% endif %}
