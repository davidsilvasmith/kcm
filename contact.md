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

# {{ site.data.information.company }} Authors

{% assign names_arr = names_str | split: delimiter %}
{% for name in names_arr %}
{% assign author = site.data.people.[name] %}
  <ul>
  	<div itemscope itemtype="http://schema.org/Person">
      {% if author.image and author.name %} <div itemprop="photo"><img src="{{author.image}}" alt="{{author.name}}" title="{{author.name}}"/> {% endif %}
      {% if author.name %} <div itemprop="name"><strong>{{author.name}}</strong></div> {% endif %}
      {% if author.description %}<div itemprop="description">{{author.description}}</div> {%endif %}
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
   
   {%if companyContact.telephone %} Tel:<span itemprop="telephone">{{ companyContact.telephone}} </span>, {% endif %}
   {%if companyContact.faxNumber %} Fax:<span itemprop="faxNumber">{{ companyContact.faxNumber}}</span>, {% endif %}
   {%if companyContact.email %} E-mail: <a href="mailto:{{companyContact.email}}"><span itemprop="email">{{ companyContact.email}}</span></a> {% endif %}
  {%if site.data.information.logo %} <img itemprop="logo" src="{{site.data.information.logo }}" /> {% endif %}
   {%if companyContact.telephone %} Phone: <span itemprop="telephone">{{ companyContact.telephone}}</span> {% endif %}
   {%if site.data.information.url %} <a href="{{site.data.information.url}}" itemprop="url">{{site.data.information.url}}</a> {% endif %}
</div>

<hr />