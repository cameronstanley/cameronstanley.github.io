# cameronstanley.github.io
Jekyll project for my personal blog and portfolio at [cameronstanley.com](cameronstanley.com).

## Getting Started
``` bash
gem install jekyll
bundle exec jekyll serve
```

## Build Instructions for Deploying to GitHub pages
GitHub Pages serves the site from `master`, but `source` is treated as the 
default. Make all changes to `source`, then run the following to push the
changes live.

``` bash
git checkout source
JEKYLL_ENV=production jekyll build
git checkout master
cp -R _site/* .
git add .
git commit -m <commit_message>
git push origin master
```
