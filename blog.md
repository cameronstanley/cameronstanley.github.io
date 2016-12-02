---
layout: default
title: Blog
permalink: /blog/
---

<div class='container-fluid container-content'>
  <div class='row'>
    <div class='col-md-8 col-md-offset-2 col-xs-10 col-xs-offset-1'>
      <div class='page-header'>
        <div class='pull-right'>
          <a href="{{ "/feed.xml" | prepend: site.baseurl }}" class='btn btn-md btn-primary'>
            <span class='fa fa-rss'></span>
            RSS Feed
          </a>
        </div>
        <h2>
          {% icon fa-book %}
          Blog
        </h2>
      </div>
    </div>
  </div>
  <div class='row'>
    <div class='col-md-8 col-md-offset-2 col-xs-10 col-xs-offset-1'>
      {% for post in site.posts %}
        <div class='media'>
          <div class='media-body'>
            <div class='media-heading'>
              <h3><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h3>
            </div>
            <p class='media-meta'>
              {% icon fa-calendar %}
              {{ post.date | date: "%b %-d, %Y" }}
            </p>
            <p class='media-text'>{{ post.excerpt | remove: '<p>' | remove: '</p>' }}</p>
          </div>
        </div>
      {% endfor %}
    </div>
  </div>
</div>
