---
layout: post
title: Go - First Impressions
---

I recently started down the path of learning the Go programming language and wanted to share my experience so far for anyone looking to get started.

# Why Go?
Go is typically labeled as a [systems programming](https://en.wikipedia.org/wiki/System_programming) language, making it a great tool for building CLIs and backend services that support other applications. It has concurrency baked in with goroutines and is also very fast. The compiler and static typing are welcome features coming from a Java background, making it a scalable language for larger projects. I see Go as another great addition to the programmer's toolbox, and I would advise anyone interested in growing their skill set to take a look at this great language.

![Go gopher](/assets/go-gopher.png "Go gopher"){: .center-image}

# Working on a Project
My first Go project is go-reddit, an API wrapper for the Reddit API. I had the idea that it might be cool to make a Reddit CLI for browsing, but the API wrappers currently available are a little lacking in functionality.  

# Pros
In my short amount of time working with Go, I have been impressed with the simple yet powerful syntax. Having a compiler and static type checking took a little bit of getting usedto but overall 

Gofmt 

Testing

# Cons
I ran in to some early issues with not having my $GOPATH set correctly, so be sure to follow the [instructions](https://golang.org/doc/code.html#GOPATH). Also, 

# Learning Resources
* [A Tour of Go](https://tour.golang.org/list) is the official tutorial and a great way to get your feet wet with the language. I'd recommend starting here since it has an interactive console you can follow along without having to setup your development environment.
* [Code School](http://codeschool.com) recently launched a new course titled "On Track With Golang" that is a pretty great introduction to the language. Usually their courses are enough to only get the basic syntax of a language down, but I found myself feeling like I had a significant handle on Go once I finished it. If you have an account, definitely spend the time to go through this one.
* [awesome-go](https://github.com/avelino/awesome-go) is a curated list of Go packages that you can use in your projects. It's always nice to have one of these when exploring a new community to see what is available and to get some quality real-world examples.
* [GoDoc](https://godoc.org/) is the official documentation host for Go packages. Any open-source project on GitHub, GitLab, Bitbucket has its documentation published here and is in a clean viewable format. Very useful when importing and using an open-source package in your project.

# Tools
* [vim-go](https://github.com/fatih/vim-go) is a must-have if you are a vim user (like me). Syntax highlighting, gofmt on save, and being able to jump to a declaration are invaluable. 
* [golint](https://github.com/golang/lint) is a linter for Go and a great way to ensure you are writing well formatted and documented code. 

*Go Gopher created by Renee French and licensed under [Creative Commons Attributions 3.0](https://creativecommons.org/licenses/by/3.0/us/).*
