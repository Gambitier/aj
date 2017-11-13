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
 			<span class="icon fa-signal"></span>		
 			<div class="content">		
 				<a href="/category/Maths Tutorials.html"><h3>Maths for Data Science</h3></a>		
 				<p>The amount of math you'll need depends on the role. But, every data scientist needs to know some 					   statistics and probability theory. We have a guide for that.</p>		
 			</div>		
 		</article>		
 		<article>		
 			<span class="icon fa-github"></span>		
 			<div class="content">		
 				<a href="/category/R Tutorials.html"><h3>R Tutorials</h3></a>		
 				<p>R is an open source programming language and software environment for statistical computing and 			graphics. R is great for machine learning, data visualization and analysis, and some areas of scientific computing. </p>		
 			</div>		
 		</article>		
 		<article>		
 			<span class="icon fa-rocket"></span>		
 			<div class="content">		
 				<a href="/category/Python Tutorials.html"><h3>Python Tutorials</h3></a>		
 				<p>Python is a great multi-purpose programming language that you should definitely consider learning it. 				Also, it has very popular libraries like scikit-learn, NumPy, SciPy, Pandas and many more... </p>		
 			</div>		
 		</article>		
 	</div>		
 </section>		
 		
 <!-- Section   <span class="icon fa-rocket"></span> -->		
 <section>		
 	<header class="major">		
 		<h2>Recent Posts akash jadhav</h2>		
 	</header>		
 <div class="posts">		
 {% for post in site.posts % limit:4}		
 	   <article>	   		
 	    <header>		
 	        <h3>{{ post.title }}</h3>		
 		<h6><time datetime="{{ post.date | date_to_xmlschema }}" class="by-line">{{ post.date | date_to_string }}</time></h6>		
        	   </header>		
 		<p>{{ post.content | strip_html | truncatewords:50 }}</p>		
 		<ul class="actions">		
 		 <li><a href="{% if site.baseurl == "/" %}{{ post.url }}{% else %}{{ post.url | prepend: site.baseurl }}{% endif %}" 			     class="button">More</a></li>		
 		 </ul>			
            </article>		
 {% endfor %}		
 </div>		
 	<br>		
 	<ul class="actions vertical">		
 		<li>		
 	    <a href="/archive/index.html" class="button fit">Load More Posts</a> 		
 		</li>		
 	</ul>		
 </section>   		
 
