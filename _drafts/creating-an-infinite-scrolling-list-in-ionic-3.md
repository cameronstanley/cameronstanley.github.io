---
layout: post
title: Creating an Infinite Scrolling List in Ionic 3
tags: ionic mobile
---

  In this tutorial, I’ll show you how to create a mobile app with a list view that handles pagination with infinite scrolling, pull to refresh, and filtering using the Ionic 3 framework. We will be integrating with the Reddit API for a live data source to retrieve a list of posts for display in our list view. When you are finished the end product will look like this:

*If you haven’t already installed Ionic, follow the [installation instructions](https://ionicframework.com/docs/intro/installation/).*

# Generating a New Project

To get started, we need to generate a new Ionic project. Run `ionic start ionic-list-tutorial blank` and when prompted to “Integrate your new app with Cordova to target native iOS and Android?” press `y` if you want to be able to run the app natively on an iOS or Android device. Hit `n` when prompted to “Install the free Ionic Pro SDK and connect your app?” as it is outside the scope of this tutorial. If all went successfully, you should now be able to run `cd ./ionic-list-tutorial` to get into the newly generated project. To see the changes we are making live as we are coding, the Ionic CLI allows us to run the app in the browser and live reload changes by running `ionic serve`. After a few seconds you should see a browser window open pointed at `localhost:8100`.

# Fetching Posts from Reddit

The first thing we need to do is fetch some posts using the Reddit API. For the purposes of this example, we will grab the “hot” posts from the front page of reddit using the endpoint `https://reddit.com/hot.json`. Using a REST client like Postman, we can see the data is structured like this *(edited for readability)*:

```
{
    "kind": "Listing",
    "data": {
        "modhash": "",
        "dist": 25,
        "children": [
            {
                "kind": "t3",
                "data": {
                    "subreddit": "legaladvice",
                    "title": "Employer lured me with an offer letter that has terms that are impossible to meet.",
                    "score": 7060,
                    "created": 1542489370,
                    "id": "9xwae6",
                    "author": "Three-letter-misery"
                }
            }, {
                "kind": "t3",
                "data": {
                    "subreddit": "AskReddit",
                    "title": "You get $1,000,000 however, it's because $100 is taken from 10,000 random people. If nobody knows that you got the money, would you do it, why/why not?",
                    "score": 63071,
                    "created": 1542489786,
                    "id": "9xwc0a",
                    "author": "Orb_Detsoob"
                }       
            }
        ]
    },
    "after": "t3_9y08db",
    "before": null
}
```
