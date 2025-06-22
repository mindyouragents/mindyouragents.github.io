---
layout: page
title: Software Engineering Blogs
permalink: /software/
includelink: true
comment: false
---

<div class="posts">
    {% for post in site.software reversed %}
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