---		 
layout: default		
---	
<script type="text/javascript" src="//downloads.mailchimp.com/js/signup-forms/popup/embed.js" data-dojo-config="usePlainJson: true, isDebug: false"></script><script type="text/javascript">require(["mojo/signup-forms/Loader"], function(L) { L.start({"baseUrl":"mc.us17.list-manage.com","uuid":"6f86671c44fdb0978c52ea2e6","lid":"70c7d1976e"}) })</script>
 <!-- Section   <span class="icon fa-rocket"></span> -->		
 <section>		
 	<header class="major">		
 		<h2>Recent Posts</h2>		
 	</header>		
 <div class="posts">		
 {% for post in site.posts limit:6 %}		
		<article>
		    <span>[Tags: 
			  {% for tag in post.tags %}
			    {% capture tag_name %}{{ tag }}{% endcapture %}
			   |<a  href="/tag/{{ tag_name }}"><nobr>{{ tag_name }}</nobr>&nbsp;</a>|
			  {% endfor %}
		   ]</span>
			<header>
				<h3>{{ post.title }}</h3>
				<h6><time datetime="{{ post.date | date_to_xmlschema }}" class="by-line">{{ post.date | date_to_string }}</time></h6>
			</header>
			<p>{{  post.content | strip_html | truncatewords:30 }}</p>
			 <ul class="actions">
				 <li><a href="{% if site.baseurl == "/" %}{{ post.url }}{% else %}{{ post.url | prepend: site.baseurl }}{% endif %}" class="button">More</a></li>
			 </ul>	
		 </article>
 {% endfor %}		
 </div>		
 	<hr>	<br>	
 	<ul class="actions vertical">		
 		<li>		
 	    <a href="/archive/index.html" class="button fit">Load More Posts</a> 		
 		</li>		
 	</ul>		
 </section>   			
