---
layout: default
title: Blog
permalink: /blog/
---

<div class="container-fluid container-content">
  <div class="row">
    <div class="col-md-8 col-md-offset-2">
      <div class="page-header">
        <div class="pull-right">
          <a href="{{ "/feed.xml" | prepend: site.baseurl }}" class="btn btn-md btn-primary">
            <span class="fa fa-rss"></span>
            RSS Feed
          </a>
        </div>
        <h2>
          <span class="fa fa-book"></span>
          Blog
        </h2>
      </div>
    </div>
  </div>
  <div class="row">
    <div class="col-md-8 col-md-offset-2">
      {% for post in site.posts %}
        <div class="media">
          <div class="media-body">
            <div class="media-heading">
              <h3><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h3>
            </div>
            <p class="media-meta">
              <span class="fa fa-calendar"></span>
              {{ post.date | date: "%b %-d, %Y" }}
              {% if post.tags.size > 0 %}
                <span class="pull-right">
                {% for tag in post.tags %}
                  <span class="label label-primary">{{ tag }}</span>
                {% endfor %}
                </span>
              {% endif %}
            </p>
            <p class="media-text">{{ post.excerpt | remove: "<p>" | remove: "</p>" }}</p>
          </div>
        </div>
      {% endfor %}
    </div>
  </div>
</div>
