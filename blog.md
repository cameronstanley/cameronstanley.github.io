---
layout: default
title: Blog
permalink: /blog/
---

<div class='container'>
  <div class='row'>
    <div class='col-md-12'>
      <div class='page-header'>
        <div class='pull-right'>
          <a href="{{ "/feed.xml" | prepend: site.baseurl }}">
            <span class='fa fa-rss'></span>
            Subscribe via RSS
          </a>
        </div>
        <h3>Blog</h3>
      </div>
      {% for post in site.posts %}
        <div class='media'>
          <div class='media-body'>
            <div class='media-heading'>
              <h4><a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h4>
            </div>
            <p>{{ post.excerpt }}</p>
            <span class="post-meta text-muted">
              <span class='fa fa-calendar'></span>
              {{ post.date | date: "%b %-d, %Y" }}
            </span>
          </div>
        </div>
      {% endfor %}
    </div>
  </div>
</div>
