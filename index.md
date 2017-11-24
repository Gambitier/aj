---		 
layout: default		
---	
<!-- Section -->
<section>
	<header class="major">
		<h2>Categories</h2>
	</header>
	<div class="features">
		<article>
			<span  class="image left"><img src="assets/images/Python.ico" alt="" /></span>
			<div class="content">
				<h3><a href="/category/Python Tutorials.html">Python Tutorials</a></h3>
				<p></p>
			</div>
		</article>
		<article> 
			<div class="content">
			<span  class="image left"><img src="assets/images/R.svg.png" alt="" /></span>
				<h3><a href="/category/R Tutorials.html">R Tutorials</a></h3>
				<p> </p>
			</div>
		</article>
		<article> 
			<div class="content">
			<span  class="image left"><img src="assets/images/Maths.png" alt="" /></span>
				<h3><a href="/category/Maths Tutorials.html"> Maths for Data Science </a></h3>
				<p> </p>
			</div>
		</article>		
		<article> 
			<div class="content">
			<span  class="image left"><img src="assets/images/Projects.png" alt="" /></span>
				<h3><a href="#"> Projects </a></h3>
				<p> </p>
			</div>
		</article>
	</div>
</section>

 <!-- Section   <span class="icon fa-rocket"></span> -->		
 <section>		
 	<header class="major">		
 		<h2>Recent Posts</h2>		
 	</header>		
 <div class="posts">		
 {% for post in site.posts limit:6 %}		
	<article>
         <header>
              <h3>{{ post.title }}</h3>
             <h6><time datetime="{{ post.date | date_to_xmlschema }}" class="by-line">{{ post.date | date_to_string }}</time></h6>
        </header>
           <p>{{  post.content | strip_html | truncatewords:30 }}</p>
           <ul class="actions">
  <li><a href="{% if site.baseurl == "/" %}{{ post.url }}{% else %}{{ post.url | prepend: site.baseurl }}{% endif %}" class="button">More</a></li>
           </ul>
		    <span>[Tags: 
			  {% for tag in post.tags %}
			    {% capture tag_name %}{{ tag }}{% endcapture %}
			   |<a  href="/tag/{{ tag_name }}"><nobr>{{ tag_name }}</nobr>&nbsp;</a>|
			  {% endfor %}
		   ]</span>
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
