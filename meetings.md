---
layout: page
title: Meetings
permalink: /meetings/
---

Meetings are held monthly on Zoom, usually for one hour with time for discussion. All times are given in UTC. The Zoom link is sent to the [mailing list]({{ '/join/' | relative_url }}).

{%- assign meetings = site.meetings | sort: "date" -%}
{%- assign n_upcoming = 0 -%}
{%- assign n_past = 0 -%}
{%- for m in meetings -%}
  {%- if m.published == false -%}{%- continue -%}{%- endif -%}
  {%- if m.status == "held" or m.status == "cancelled" -%}
    {%- assign n_past = n_past | plus: 1 -%}
  {%- else -%}
    {%- assign n_upcoming = n_upcoming | plus: 1 -%}
  {%- endif -%}
{%- endfor %}

## Upcoming

{% if n_upcoming > 0 -%}
<ul class="meeting-list">
{%- for m in meetings -%}
  {%- if m.published == false or m.status == "held" or m.status == "cancelled" -%}{%- continue -%}{%- endif %}
  <li>
    <strong>{{ m.date | date: site.minima.date_format }}</strong> &mdash;
    <a href="{{ m.url | relative_url }}">{{ m.title | escape }}</a>
    {%- if m.speaker and m.speaker != "" %}<br><em>{{ m.speaker | escape }}{% if m.affiliation and m.affiliation != "" %}, {{ m.affiliation | escape }}{% endif %}</em>{% endif %}
  </li>
{%- endfor %}
</ul>
{%- else -%}
No meetings are scheduled yet. The schedule will be posted here once the organizers have met.
{%- endif %}

## Past

{% if n_past > 0 -%}
<ul class="meeting-list">
{%- assign past = meetings | reverse -%}
{%- for m in past -%}
  {%- if m.published == false -%}{%- continue -%}{%- endif -%}
  {%- if m.status != "held" and m.status != "cancelled" -%}{%- continue -%}{%- endif %}
  <li>
    <strong>{{ m.date | date: site.minima.date_format }}</strong> &mdash;
    <a href="{{ m.url | relative_url }}">{{ m.title | escape }}</a>
    {%- if m.status == "cancelled" %} (cancelled){% endif %}
    {%- if m.speaker and m.speaker != "" %}<br><em>{{ m.speaker | escape }}{% if m.affiliation and m.affiliation != "" %}, {{ m.affiliation | escape }}{% endif %}</em>{% endif %}
    {%- if m.recording and m.recording != "" %} &middot; <a href="{{ m.recording }}">Recording</a>{% endif %}
    {%- if m.slides and m.slides != "" %} &middot; <a href="{{ m.slides }}">Slides</a>{% endif %}
  </li>
{%- endfor %}
</ul>
{%- else -%}
No past meetings yet.
{%- endif %}

Recordings and slides are posted when speakers agree.
