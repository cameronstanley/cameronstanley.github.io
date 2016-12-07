---
layout: post
title: Go - First Impressions
tags: go
---

I recently started down the path of learning the Go programming language and wanted to share my experience for anyone interested in becoming a Gopher.

# Why Go?
Go is typically labeled as a [systems programming](https://en.wikipedia.org/wiki/System_programming) language, making it a great tool for building CLIs and backend services that support other applications. It has concurrency baked in with [goroutines](https://tour.golang.org/concurrency/1) and is also very fast. The compiler and static typing are welcome features coming from a Java background, making it a scalable language for larger projects. I see Go as another great addition to the programmer's toolbox, and I would advise anyone interested in growing their skill set to take a look at this great language.

![Go gopher](/assets/go-gopher.png "Go gopher"){: .center-block}

# Working on a Project
I always find the best way to progress in a new language is to pick a non-trivial project and see it through to completion. I've been making [go-reddit](https://github.com/cameronstanley/go-reddit), a wrapper for the Reddit API for a few weeks now. I thought it might be cool to make a Reddit CLI for light console browsing, but the API wrappers currently available are a little lacking in functionality. Development has been pretty steady in my off-time, there are just a ton of endpoints to implement and the response objects can be a little tricky to parse. The main challenges have been:

## Decoding of JSON
Parsing the JSON responses from the API is handled using the [encoding/json package](https://godoc.org/encoding/json). The json package will decode the body of a response to a struct, provided that struct's named fields matches the keys in the JSON object (if not you can explicity declare the mapping using the backticks format as shown below). Here's an example:

```go
var trophyListing struct {
  Kind string `json:"kind"`
  Data struct {
    Trophies []*Award `json:"trophies"`
  } `json:"data"`
}

err = json.NewDecoder(resp.Body).Decode(&trophyListing)
if err != nil {
  return nil, err
}
```

Where it starts to get tricky is when you have multiple types that can be returned in a listing, which requires more dynamic parsing. I'm still working through the cleanest way to implement this functionality.

## Implementing OAuth2
The [oauth2 package](golang.org/x/oauth2) does a lot of the heavy lifting for implementing OAuth2, but I have still been struggling with a HTTP 429 Too Many Requests error when exchanging the authentication code for an access token according to the protocol:

```
oauth2: cannot fetch token: 429 Too Many Requests
```

Reddit requires a unique User-Agent header to be set for all authenticated requests, and will heavily rate limit any calls not providing it. Doing some Googling suggests that is the cause of my HTTP 429 error code, but the oauth2 package does not have the functionality to set the User-Agent during the token exchange. It looks like I'm going to need to implement the token exchange manually, which shouldn't be too difficult.

# Initial Thoughts
In my short amount of time working with Go, I have been impressed with the simple yet powerful syntax. Having a compiler and static type checking took a little bit of getting used to but really increases productivity by catching complation errors. I'm also particularly fond of the [gofmt](https://golang.org/cmd/gofmt/) tool that will autocorrect formatting issues leading to more readable and consistent code. The [testing package](https://golang.org/pkg/testing/) provides a nice framework to write and run tests and I'm going to try out one of the BDD packages when I have some time. Go feels similar to in spirit to C, but I feel like it is easier to produce fast, working, well tested and documented code using it.

I did run in to some early issues with not having my $GOPATH set correctly, so be sure to follow the [install instructions](https://golang.org/doc/code.html#GOPATH). Also, when working on go-reddit it took me a little while to figure out that if you are going to use your package locally in a `package main` program it needs to be located within your $GOPATH to be able to import it. My project was located in directory outside my $GOPATH and it was a bit of a headache trying to debug it.

Overall, I am loving Go and would highly recommend it to anyone looking to add a great language to their skill set.

# Learning Resources
Here's a list of resources I utilized while learning Go:

* [A Tour of Go](https://tour.golang.org/list) is the official tutorial and a great way to get your feet wet with the language. I'd recommend starting here since it has an interactive console you can follow along without having to setup your development environment.
* [Code School](http://codeschool.com) recently launched a new course titled "On Track With Golang" that is a pretty great introduction to the language. Usually their courses are enough to only get the basic syntax of a language down, but I found myself feeling like I had a significant handle on Go once I finished it. If you have an account, definitely spend the time to go through this one.
* [awesome-go](https://github.com/avelino/awesome-go) is a curated list of Go packages that you can use in your projects. It's always nice to have one of these when exploring a new community to see what is available and to get some quality real-world examples.
* [GoDoc](https://godoc.org/) is the official documentation host for Go packages. Any open-source project on GitHub, GitLab, or Bitbucket has its documentation published here and is in a clean viewable format. It is very useful when importing and using an open-source package in your project.

# Tools
* [vim-go](https://github.com/fatih/vim-go) is a must-have if you are a vim user (like me). Syntax highlighting, gofmt on save, and being able to jump to a declaration are all invaluable. 
* [golint](https://github.com/golang/lint) is a linter for Go and a great way to ensure you are writing stylistically correct and GoDoc ready code. 

*Go Gopher created by Renee French and licensed under [Creative Commons Attributions 3.0](https://creativecommons.org/licenses/by/3.0/us/).*
