---
title: People
permalink: /people/
---

<style type="text/css">
  a:link {color: black;}
  a:hover {color: black;} 
</style>

{% assign people_sorted = site.people | sort: 'last_name' %}
{% assign role_array = "faculty|student|alumni" | split: "|" %}

{% for role in role_array %}

{% assign people_in_role = people_sorted | where: 'position', role %}

<!-- Skip section if there's nobody -->
{% if people_in_role.size == 0 %}
  {% continue %}
{% endif %}

<div class="pos_header">
{% if role == 'faculty' %}
<h3>Faculty Members</h3>
 {% elsif role == 'student' %}
<h3>Student Members</h3>
{% endif %}
</div>

<div class="content list people">
  {% for profile in people_sorted %}
    {% if profile.position contains role %}
      <div class="list-item-people">
        <p class="list-post-title">
          <a href="{{ profile.homepage }}"><img class="profile-thumbnail" src="{{site.baseurl}}/images/people/{{profile.avatar}}"></a>
          <a class="name" href="{{ profile.homepage }}">{{ profile.name }}</a><br>
          {% if profile.homepage %}
            <a class="fa fa-home" href="{{ profile.homepage }}"></a>
          {% endif %}
          {% if profile.scholar %}
            <a class="fa fa-google" href="{{ 'https://scholar.google.com/citations?user=' | append: profile.scholar }}"></a>
          {% endif %}
          {% if profile.github %}
            <a class="fa fa-github" href="{{ 'https://github.com/' | append: profile.github }}"></a>
          {% endif %}
          {% if profile.twitter %}
            <a class="fa fa-twitter" href="{{ 'https://twitter.com/' | append: profile.twitter }}"></a>
          {% endif %}
          {% if profile.linkedin %}
            <a class="fa fa-linkedin" href="{{ 'https://linkedin.com/in/' | append: profile.linkedin }}"></a>
          {% endif %}
        </p>
      </div>    
    {% endif %}
  {% endfor %}
</div>
<hr>

{% endfor %}

<h3>Alumni</h3>

| Who are they | Current position |
| :------------- |:------------- |
| Yutong Lu | CANSTAT Fellow @ Unity Health Toronto |
| Yushu Zou | Research Assistant @ Public Health Ontario |
| Juan Pablo Díaz-Martinez | Research Associate @ Toronto Western Lupus Clinic |
| Rebecca Christensen | Postdoctoral fellow @ University of Toronto |
| Rose Garrett | Senior Statistician @ AstraZeneca |
| Rose Schmidt | PhD Student in Social and Behavioural Health @ DLSPH, University of Toronto |
