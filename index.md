---		 
layout: default		
---	
 <!-- Begin MailChimp Signup Form -->
<link href="//cdn-images.mailchimp.com/embedcode/slim-10_7.css" rel="stylesheet" type="text/css">
<style type="text/css">
	#mc_embed_signup{background:#fff; clear:left; font:14px Helvetica,Arial,sans-serif; }
	/* Add your own MailChimp form style overrides in your site stylesheet or in this style block.
	   We recommend moving this block and the preceding CSS link to the HEAD of your HTML file. */
</style>
<div id="mc_embed_signup">
<form action="https://github.us17.list-manage.com/subscribe/post?u=6f86671c44fdb0978c52ea2e6&amp;id=70c7d1976e" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
    <div id="mc_embed_signup_scroll">
	<label for="mce-EMAIL">Subscribe to our mailing list</label>
	<input type="email" value="" name="EMAIL" class="email" id="mce-EMAIL" placeholder="email address" required>
    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_6f86671c44fdb0978c52ea2e6_70c7d1976e" tabindex="-1" value=""></div>
    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>
    </div>
</form>
</div>

<!--End mc_embed_signup-->
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
