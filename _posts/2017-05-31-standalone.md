---
layout: post
title: ApacheExpress ✂️ mod_swift
tags: apache linux swift server side raspberry
---

Breaking news: A much enhanced **ApacheExpress** becomes its own project,
separate from [mod_swift](http://mod-swift.org/).

Our 
[original mod_swift technology demo](https://github.com/ApacheExpress/ApacheExpress/tree/standalone-demo-2017-04-24) 
contained various things:

- mod_swift, the C module which adds the `LoadSwiftModule` directive
- Module maps etc to expose the Apache C API to Swift
- ExExpress
- ApacheExpress
- a set of examples

All setup as a 'demo' environment to showcase how Apache modules can be written
in Swift, right within Xcode.

As it turns out, Swift is actually a great language to write Apache modules in!
And ApacheExpress is a pretty neat framework on top.
So in the last few months we worked on turning 
[mod_swift](http://mod-swift.org/)
from being just a neat technology demo 
into being a reliable hosting environment for Swift web applications.

During that, ApacheExpress
functionality has also grown a lot and evolved into a rather powerful web 
application framework (stay tuned!).
Hence we felt that we need to separate the two.
On one side
[mod_swift](http://mod-swift.org/) being just an integration point between Swift and Apache that is
framework independent.
On the other side 
ApacheExpress as a higher level framework with an
Express like API.

## The new mod_swift

The [new mod_swift](https://github.com/modswift) is not setup as a fancy demo 
but as an infrastructure component.
If you want a little like [Phusion Passenger](https://www.phusionpassenger.com),
but not really, because **mod_swift** is used to create fully native Apache 
modules instead of hosting foreign webapps within Apache.

Read more about it over here:
[The new mod_swift](http://mod-swift.org/standalone/#the-new-mod_swift).

## The new ApacheExpress

We split off 
[mod_swift](http://mod-swift.org/)
because we think it is generally useful as a
standalone component for various Swift server projects. Plugging into
"[The Number One HTTP Server On The Internet](https://httpd.apache.org)"
just makes more sense than trying to replicate its rich and proven 
functionality.

<a href="http://apacheexpress.io/" target="apex">
  <img src="http://zeezide.com/img/ApexIcon1024.svg"
       align="right" width="128" height="128" style="padding: 0.5em;"/></a>
However, we also have a neat, higher level, framework in the works:
**ApacheExpress**.
It is based on what was included in the
[mod_swift technology demo]([https://github.com/ApacheExpress/ApacheExpress/tree/standalone-demo-2017-04-24]),
but much enhanced and interfaces with our
[ZeeQL](http://zeeql.io/) database access framework.<br />
Work is still in progress to finish that up, stay tuned!

## Summary

We think this is pretty cool stuff,
but we love feedback.
Join the mailing list, Slack channel or just drop us
an email to tell us why this is crap (or not?): [Slack](http://slack.noze.io).
