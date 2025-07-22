---
layout: default
title: "Archive | citizenhicks"
permalink: /archive/
---

<header>
    <h1>All Posts</h1>
    <p class="subtitle">complete archive of thoughts and insights</p>
    <nav style="margin: 1rem 0;">
        <a href="{{ '/' | relative_url }}" class="back-to-blog">← back to blog</a>
    </nav>
</header>

<section class="section">
    {% if site.posts.size > 0 %}
        <div class="blog-posts">
            {% for post in site.posts %}
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
    {% else %}
        <div class="no-posts">
            <h3>No posts yet</h3>
            <p>Check back soon for content on AI, multi-agent systems, and software engineering.</p>
        </div>
    {% endif %}
</section>

<footer>
    <p><a href="{{ '/' | relative_url }}">← back to blog</a> | Find me on <a href="{{ site.data.site.author.twitter }}" target="_blank">X</a> | <a href="{{ site.data.site.author.github }}" target="_blank">GitHub</a></p>
</footer>