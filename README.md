# Ember Data Starter Kit

Here is a very simple [Ember Data](https://github.com/emberjs/data) starter kit based on the following libraries

* Ember 1.0.0-rc.3
* Ember Data 3caadcc (2013-04-26 11:07:32 -0700)
* Handlebars 1.0.0-rc.3
* jQuery 1.9.1

# What does it do?

It will demonstrate retrieving some simple JSON from a REST API and displaying it as HTML.

# Do I have to install anything?

Probably not. However, you'll need a web server capable of serving files. For ease of use I tend to use the `SimpleHTTPServer` that comes with
python and is available by default in Mac OS. However, you might prefer Node.js, nginx or Apache. Anyway, just get a web server to point
at the project directory and you'll be fine.

If you go with the Python approach, just issue this at the project root

```
python -m SimpleHTTPServer
```

then navigate to [localhost:8000](http://localhost:8000). Port 8000 is the default for Python rather than 8080.

# What am I seeing?

If you see the text "This is the post you're looking for!" then you're in business.

# Nope not seeing that...

You'll need to do some debugging.

* Most likely you're not viewing `index.html` through a server (same origin problem)
* Don't go changing the .js files - compatibility in the release candidates is fraught with hazard
* Check the JavaScript console in your browser. Chrome and Firefox have comprehensive debugging tools.

# Yay! I'm in business! What's going on?

Let's work it back from the front end to the server

1. The file `index.html` got loaded and a bunch of scripts were initialized
2. The section script with `data-template-name="application"` is the HTML output for the Ember application
3. The section script with `data-template-name="index"` is the HTML template for the post

# OK, and where's the JavaScript?

All the magic happens in `app.js` take a look at the comments and you'll see how it fits together.

1. The application will log to the browser console
2. There is a model called Post with a `title` and `body` linked to a data store
3. There is a simple route that only gets the Post with id=1 (the path `posts` is implied through Ember naming conventions)
4. The `RESTAdapter` is configured to create URL paths using the template `/api/posts/{id}.json` which makes the simulated RESTful API easier
5. The data store uses Ember Data revision 12 and references the `RESTAdapter`

# Well that was easy! What next?

For a much bigger scale application involving a [Maven](http://maven.apache.org)-built [Dropwizard](http://dropwizard.codahale.com) back end combined
with a [Grunt.js](http://gruntjs.com)-built front end see my other public repos (TODO).