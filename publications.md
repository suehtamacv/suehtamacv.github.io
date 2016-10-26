---
layout: post
title: Publications
description: Chronological publication list
image: assets/images/books.jpg
nav-menu: yes
---

<div class="main">
	
<p> Below there is my chronological publication list. </p>

	<div class="inner">
	{% assign artigosporano = site.publications | group_by:"ano" | sort:"name" | reverse %}
	{% for item in artigosporano %}
	{% assign sorted_artigos = item.items | sort:"titulo" %}
	{% for artigo in sorted_artigos %}
	{% capture this_year %}{{ artigo.ano }}{% endcapture %}
	{% if forloop.first %}
	<p>
	<div class="major">
	  <h2 id="{{ this_year }}-ref">{{ this_year }}</h2>
	  <a data-toggle="collapse" href="#{{ this_year }}"><i class="fa fa-caret-down"></i> {{ forloop.length }} {%if forloop.length == 1 %}article{% else %}articles{% endif %}</a>
	  <div id="{{ this_year }}" class="panel-collapse collapse">
		<ul>
	{% endif %}
		  <li>
			<h3>{{ artigo.titulo }}</h3>
			<a data-toggle="collapse" href="#{{ item.name }}-{{ forloop.index }}"><i class="fa fa-caret-down"></i> Details</a>
			<p><div id="{{ item.name }}-{{ forloop.index }}" class="panel-collapse collapse">
			  <p>{{ artigo.evento }}, {{ artigo.ano }}.</p>
			  <div>
			  Authors:
				<ul>
				  {% for autor in artigo.autores %}
				  <li> {{ autor.nome }} </li>
				  {% endfor %}
				</ul>
			  </div>
			</div></p>
		  </li>
		  {% if forloop.last %}
		</ul>
	  </div>
	</div></p>
	{% endif %}
	{% endfor %}
	{% endfor %}
  </div>
</div>
