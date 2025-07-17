---
layout: page
title: Blog
permalink: /blog/
includelink: true
comment: false
---
<div class="posts">
    <br />

    {% for post in site.posts %}
    <div>
        <span class="post-date">{{ post.date | date: "%b %-d, %Y" }}</span>
        <br />
        <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        <br />
        {{ post.excerpt }}
        <br />
        <br />
        <br />
    </div>
    {% endfor %}
</div>
