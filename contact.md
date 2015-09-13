---
layout: default
title: Contact
subtitle: Get in Touch 
includeJoin: 1
permalink: /contact/
---

{% assign delimiter = "," %}
{% assign names_str = "" %}

{% assign names_str = 'todd,jim,dave' %}

# {{ site.data.information.company }} Executives

{% assign names_arr = names_str | split: delimiter %}
{% for name in names_arr %}
{% assign author = site.data.people.[name] %}
  <ul>
  	<div itemscope itemtype="http://schema.org/Person">
      {% if author.image and author.name %} <div itemprop="photo"><img src="{{author.image}}" alt="{{author.name}}" title="{{author.name}}"/> {% endif %}
      <a href="{{author.link}}">{% if author.name %} <div itemprop="name"><strong>{{author.name}}</strong></div> {% endif %}
      {% if author.description %}<div itemprop="description">{{author.description}}</div> {%endif %}</a>
      {% if author.email %}<a href="mailto:{{author.email}}"><div itemprop="email">{{author.email}}</div></a>{% endif %}
    </div>
  </ul>
  <hr />
{% endfor %}


{% assign companyContact = site.data.people[site.data.information.companyContact] %}

<hr />

Get in Touch

<div itemscope itemtype="http://schema.org/Organization"> 
   <span itemprop="name">{{site.data.information.title}}</span> 
   Located at 

   {% include address.html param=companyContact %}
   
   {%if companyContact.telephone %} <div>Tel:<span itemprop="telephone">{{ companyContact.telephone}} </span></div> {% endif %}
   {%if companyContact.faxNumber %} <div>Fax:<span itemprop="faxNumber">{{ companyContact.faxNumber}}</span></div> {% endif %}
   {%if companyContact.email %} <div>E-mail: <a href="mailto:{{companyContact.email}}"><span itemprop="email">{{ companyContact.email}}</span></div></a> {% endif %}
  {%if site.data.information.logo %} <div><img itemprop="logo" src="{{site.data.information.logo }}" style="max-width:200px;"/></div> {% endif %}
   {%if companyContact.telephone %} <div>Phone: <span itemprop="telephone">{{ companyContact.telephone}}</span></div> {% endif %}
   {%if site.data.information.url %} <div><a href="{{site.data.information.url}}" itemprop="url">{{site.data.information.url}}</a></div> {% endif %}
</div>

<hr />