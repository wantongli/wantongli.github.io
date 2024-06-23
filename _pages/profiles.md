---
layout: page
permalink: /Team/
title: Team
description:
nav: true
nav_order: 1
---

{% assign groups = site.members | sort: "group_rank" |  map: "group" | uniq %}
{% for group in groups %}
### {{ group }}
 {% assign members = site.members | sort: "group_order" | where: "group", group %}
    {% for member in members %}
<p>
    <div class="card {% if member.inline == false %}hoverable{% endif %}">
        <div class="row no-gutters">
            <div class="col-sm-4 col-md-3">
                <img src="{{ '/assets/img/team/' | append: member.profile.image | relative_url }}" class="card-img img-fluid" alt="{{ member.profile.name }}" />
            </div>
            <div class="team col-sm-8 col-md-9">
                <div class="card-body">
                    {% if member.inline == false %}{% if member.external == true %} <a href="{{ member.profile.website }}">{% else %}<a href="{{ member.url | relative_url }}">{% endif %}{% endif %}
                    <h5 class="card-title">{{ member.profile.name }}</h5>
                    {% if member.profile.position %}
                    {% if member.profile.team-position %}<h6 class="card-subtitle mb-2 text-muted">{{ member.profile.team-position }}</h6>
                    {% else %}<h6 class="card-subtitle mb-2 text-muted">{{ member.profile.position }}</h6>{% endif %}{% endif %}
                    <p class="card-text">
                        {{ member.teaser }}
                    </p>
                    {% if member.inline == false %}</a>{% endif %}
                    {% if member.profile.email %}
                        <a href="mailto:{{ member.profile.email }}" class="card-link"><i class="fas fa-envelope"></i></a>
                    {% endif %}
                    {% if member.profile.google %}
                        <a href="{{ member.profile.google }}" class="card-link" target="_blank"><i class="fa-brands fa-google-scholar"></i></a>
                    {% endif %}
                    {% if member.profile.website %}
                        <a href="{{ member.profile.website }}" class="card-link" target="_blank"><i class="fa-brands fa-linkedin-in"></i></a>
                    {% endif %}
                </div>
            </div>
        </div>
    </div>
    {% endfor %}
    <br />
    <br />
</p>
{% endfor %}