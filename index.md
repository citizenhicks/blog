---
layout: default
title: "Blog | citizenhicks"
---

<header>
    <h1>{{ site.data.site.author.name }}</h1>
    <p class="subtitle">{{ site.data.site.author.blogsub }}</p>
    <nav style="margin: 1rem 0;">
        <a href="{{ site.data.site.author.portfolio }}" class="back-to-home">portfolio</a>
        <span style="margin: 0 1rem;">|</span>
        <a href="{{ site.data.site.author.twitter }}" target="_blank">X/Twitter</a>
        <a href="{{ site.data.site.author.github }}" target="_blank">GitHub</a>
    </nav>
</header>

<section class="section">
    <h2>Latest Posts</h2>
    {% if site.posts.size > 0 %}
        <div class="blog-posts">
            {% for post in site.posts limit:5 %}
            <article class="blog-post-preview">
                <h3 class="blog-post-title">
                    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                </h3>
                <div class="blog-post-meta">
                    <time>{{ post.date | date: "%B %d, %Y" }}</time>
                    {% if post.author %}
                    <span> • by {{ post.author }}</span>
                    {% endif %}
                    {% if post.tags and post.tags.size > 0 %}
                    <div class="post-tags">
                        {% for tag in post.tags %}
                        <span class="tag">{{ tag }}</span>
                        {% endfor %}
                    </div>
                    {% endif %}
                </div>
                <div class="blog-post-excerpt">
                    {% if post.excerpt %}
                        {{ post.excerpt | strip_html | truncatewords: 30 }}
                    {% else %}
                        {{ post.content | strip_html | truncatewords: 30 }}
                    {% endif %}
                </div>
                <a href="{{ post.url | relative_url }}" class="read-more">Read more →</a>
            </article>
            {% endfor %}
        </div>
        
        {% if site.posts.size > 5 %}
        <div style="text-align: center; margin-top: 2rem;">
            <a href="{{ '/archive' | relative_url }}" class="blog-nav-link">View All Posts →</a>
        </div>
        {% endif %}
    {% else %}
        <div class="no-posts">
            <h3>No posts yet</h3>
            <p>Check back soon for content on AI, multi-agent systems, and software engineering.</p>
        </div>
    {% endif %}
</section>

<section class="section">
    <h2>About</h2>
    <p>indie ml engineer and ai enthusiast specializing in multi-agent systems and autonomous ai architectures. building the next generation of multi agent applications that enable complex startegic modeling, planning, and tool use. passionate about creating intelligent systems that can decompose problems, coordinate across specialized agents, and deliver sophisticated solutions through orchestrated workflows.</p>
    <div class="skills">
        {% for skill in site.data.site.skills.about %}
        <span class="tag">{{ skill }}</span>
        {% endfor %}
    </div>
</section>
<footer>
<p>Find me on <a href="{{ site.data.site.author.twitter }}" target="_blank">X</a> | <a href="{{ site.data.site.author.github }}" target="_blank">GitHub</a> | built with passion</p>
</footer>
