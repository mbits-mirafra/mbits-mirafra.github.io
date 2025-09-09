---
layout: page
title: Contributors
permalink: /contributors/
---

<style>

.contributor-block p {
  color: rgb(0,0,0);
  font-size: 1em;
}

.contributor-block {
  height: 150px;
  padding-top: 30px;
  padding-bottom: 30px;
  padding-right: 15px;
  background-color: lightblue;
  width: 80%;
  margin-left: auto;
  margin-right: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

.left-section {
  width: 40%;
  height: 100%
}

.profile-pic {
  border-radius: 50%;
  width: 100px;
  height: 100px;
  margin-right: auto;
  margin-left: auto;
  overflow: hidden;
}

.view-articles {
  background-color: #f08080;
  width: 80%;
  border-radius: 10px;
  margin-top: 15px;
  height: 30%;
  margin-right: auto;
  margin-left: auto;
  display: flex;
  align-items: center;
  justify-content: center;
}

.view-articles:hover {
  background-color: #ef6f6f;
}

.text {
  width: 60%;
  
}

.name {
  font-weight: bold;
}

</style>

{% for contributor in site.contributors %}
{% assign filtered_projects = site.projects | where_exp: 'project', "project.contributors contains contributor.short_name" %}

<div class="contributor-block">

  <div class="left-section">

    <div class="profile-pic">
      <img src="/assets/contributors/{{ contributor.profile_pic }}">
    </div>

    <div onclick="window.location.href = '{{ contributor.url | absolute_url }}';" class="view-articles">
      -> {{ filtered_projects.size }}
      {% if filtered_projects.size == 1 %}
        Project
      {% else %}
        Projects
      {%- endif -%}
     </div>

  </div>

  <div class="text">

    <div class="name">
      <a href="{{ contributor.url }}">{{ contributor.name }}</a>
    </div>

    <div class="bio">
      {{ contributor.excerpt }}
    </div>

  </div>

</div>

{% endfor %}

