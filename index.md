---
layout: default
title: ApacheExpress ✭ Make Apache great again!
tags: apache swift server side mod_swift
---

<p>
  <img src="https://img.shields.io/badge/apache-2-yellow.svg" />
  <img src="https://img.shields.io/badge/swift-3-blue.svg" />
  <img src="https://img.shields.io/badge/swift-4-blue.svg" />
  <img src="https://img.shields.io/badge/os-macOS-green.svg?style=flat" />
  <img src="https://img.shields.io/badge/os-tuxOS-green.svg?style=flat" />
  <img src="https://travis-ci.org/ApacheExpress/ApacheExpress.svg?branch=master" />
</p>

**ApacheExpress**
is a way to rapidly write reliable and feature rich web applications
in the [Swift](http://swift.org/) programming language.
Without ever leaving Xcode, or using the Swift Package Manager environment
on Linux.
**ApacheExpress** applications run directly within the 
[Apache WebServer](http://httpd.apache.org/)
as native Apache modules - without any interpreters or proxies.

<center><i>Server Side Swift the right way.</i></center>

ApacheExpress can be used alongside any other Apache module and hence can
exploit the proven functionality of Apache.
This includes pretty much any kind of authentication mechanism you can 
think of,
rate limiting / anti-DoS modules, or
[mod_ssl](https://httpd.apache.org/docs/current/mod/mod_ssl.html)
to secure the web application as well as mod_h2 to provide
[HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) support.
The latter are preconfigured when running ApacheExpress
modules and provide full HTTP/2 access out of the box.

### Simple Example

Developing ApacheExpress applications use a Swift version of the mechanisms
and APIs used by the [Express.js](http://expressjs.com) framework.
Hence its name. Example:

```swift
let app = apache.express(cookieParser(), session())

app.get("/express/cookies") { req, res, _ in
  try res.json(req.cookies)
}

app.get("/express/") { req, res, _ in
  let values = [
    "viewCount"   : req.session["viewCount"] ?? 0,
    "cowOfTheDay" : cows.vaca()
  ]
  try res.render("index", values)
}
```

It grabs the application object representing the module,
configures two builtin middleware objects (`cookieParser`, `session`)
and then registers two routes
([docs](http://docs.apacheexpress.io/routing/)).
The middleware attached to the `/express/cookies` route simply extracts all
HTTP cookies set in the request and returns them as JSON.
The other sets up a dictionary which is then rendered using a 
[Mustache](http://mustache.github.io) template
([docs](http://docs.apacheexpress.io/templates/)).

### Database Access


To provide access to a collection of SQL databases, including 
[PostgreSQL](https://www.postgresql.org) and
[SQLite3](http://www.sqlite.org), ApacheExpress uses the Apache 
[mod_dbd](https://httpd.apache.org/docs/2.4/mod/mod_dbd.html) module.
Apache is used to configure the database connection and Apache is maintaining
the database connection pool.

ApacheExpress then provides the *mod_dbd* middleware,
which stacks the powerful [ZeeQL](http://zeeql.io/)
database access framework on top of Apache's module
([docs](http://docs.apacheexpress.io/mod_dbd/)).


### WORK IN PROGRESS, STAY TUNED

ApacheExpress is still being prepared. Please stay tuned for the release.
If you want to stay up to date, subscribe to the
[ApacheExpress Blog](/blog/).

ApacheExpress documentation can be found here:
[docs.apacheexpress.io](http://docs.apacheexpress.io/).

<hr />

<div class="posts">
  {% for post in site.posts %}
    <article class="post">

      <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>

      <div class="entry">
        {{ post.excerpt }}
      </div>
      
      <div class="date">
        <table border="0" width="100%"> <!-- old skool -->
          <tr>
            <td>{{ post.date | date: "%B %e, %Y" }}</td>
            <td style="text-align:right;"><a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a></td>
          </tr>
        </table>
      </div>
    </article>
  {% endfor %}
</div>
