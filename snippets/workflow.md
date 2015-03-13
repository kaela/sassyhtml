---
layout: page
title: Workflow
permalink: /snippets/workflow/
---

Back to [Snippets]({{ site.baseurl }}/snippets)
<ul>
	{% for post in site.categories.workflow %}
	<li>
		<a href="{{post.permalink}}">{{post.title}}</a>
	</li>
	{% endfor %}
</ul>