---
layout: post
title: Creating a Cordova Plugin (iOS implementation)
tags: cordova, ionic, ios
---

In this post, I'm going to go over how to create a Cordova plugin and implement the native APIs for the iOS platform. Cordova allows developers to target multiple mobile platforms using a special web view wrapper to write once and deploy anywhere. In this tutorial, I will implement the JS interface and the underlying iOS implementation for a simple "hello world" plugin.

## Setup
To create a plugin, we will start with an empty git repo. Create the repo on your hosted Git repo named cordova-hello-world (or a name of your choosing), clone it to your local, then create the following file/folder structure:

```
cordova-hello-world
  - plugin.xml
  - src/
    - ios
  - www
    - hello-world.js
```

## Implementing the Javascript interface
Open the file `cordova-hello-world/www/hello-world.js` we created. This is going to be the hook in to our native implementation from our web view.
