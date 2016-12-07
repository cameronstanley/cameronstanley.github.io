---
layout: post
title: "Using Glyphicons PRO with Rails"
date: 2015-08-14 10:30:00
tags: rails glyphicons
---

[Bootstrap 3](http://getbootstrap.com) comes packaged with a fancy set of over 250 free icons called [Glyphicons](http://glyphicons.com/) that can easily be used to make your application more user friendly. After using them for some time, but needing a little more variety in my icon choice, I decided to upgrade to Glyphicons PRO which provides close to 1000 icons in various formats and sizes. It also includes a web font which plays nicely with Rails after a little configuration. Here's how to get Glyphicons PRO working in your Rails project:

**Note: This tutorial assumes a Rails 4 project using Sass.**

First, make the web fonts available in the asset pipeline by copying them to app/assets/fonts (create this directory if it doesn't already exist).

~~~ bash
mkdir <rails_root>/app/assets/fonts   
cp glyphicons_pro/glyphicons/web/html_css/fonts/* <rails_root>/app/assets/fonts/   
~~~

Next, copy the provided glyphicons.css file to app/assets/stylesheets and name it with a .css.scss extension. 

~~~ bash
cp glyphicons_pro/glyphicons_all/glyphicons/web/html_css/css/glyphicons.css <rails_root>/app/assets/stylesheets/glyphicons.css.scss
~~~

Finally, the URL paths for the fonts inside of glyphicons.css.scss need to be modified to use the asset helper `font-url`. Remove the `../fonts/` portion of the path and wrap the filename in `font-path()` for each font file.

~~~ css
@font-face {
  font-family:'Glyphicons Regular';
  src:url(font-path('glyphicons-regular.eot'));
  src:url(font-path('glyphicons-regular.eot?#iefix')) format('embedded-opentype'),
  url(font-path('glyphicons-regular.woff2')) format('woff2'),
  url(font-path('glyphicons-regular.woff')) format('woff'),
  url(font-path('glyphicons-regular.ttf')) format('truetype'),
  url(font-path('glyphicons-regular.svg#glyphiconsregular')) format('svg')
}
...
~~~

Restart your rails server and the icons will now be available in your app. 

Note the difference in naming between the CSS class for Bootstrap Glyphicons (`glyphicon`) and Glyphicons PRO (`glyphicons`). If your project was previously using Bootstrap 3 Glyphicons, each usage will need to be modified to take advantage of Glyphicons PRO.

~~~ html
<span class="glyphicons glyphicons-thumbs-up">
~~~
