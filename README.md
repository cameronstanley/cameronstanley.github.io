# cameronstanley.github.io
Jekyll project for my personal blog and portfolio at [cameronstanley.com](cameronstanley.com).

## Build Instructions for Deploying to GitHub pages
``` bash
git checkout source
jekyll build
git checkout master
cp -R _site/* .
git add .
git commit -m <commit_message>
git push origin master
```
