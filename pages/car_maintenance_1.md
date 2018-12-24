---
layout: post
---

# CAR MAINTENANCE APP PART 1: CREATING A HELLOWORLD NODE/EXPRESS SERVER FROM SCRATCH

REPO: HTTPS://GITHUB.COM/NEELKRISHNA/CAR-MAINTENANCE

Most of you have likely built or worked with a NodeJs/ExpressJs server, but if you haven’t, that’s ok! This part of the tutorial will explain how to build your server, and what each block of code does – I think it’s helpful to know your code at this level, rather than starting with a seed project. Let’s begin!

### STEP 1: CREATE YOUR PACKAGE FILE

Create a directory called car-maintenance, and inside it, another one called server-car-maintenance. Navigate inside server-car-maintenance on your command line. Run:

```
npm init
```

A wizard will walk you through creating a package.json file for your new NodeJs application. You can allow the wizard to enter default values for each attribute by pressing enter.

### STEP 2: ADD SOME CRUCIAL DEPENDENCIES

Add important dependencies to your project by running the following command inside server-car-maintenance:

```
npm install express --save
npm install morgan --save
npm install mysql --save
npm install path --save
npm install jade --save
```

**Express** is a web application framework for node that allows us to create a REST API. More on that later.
**Morgan** is a logging tool we’ll use to debug as needed.
We will be using a **MySQL** database to store our data.
**Path** allows us to load data or dependencies from file paths, as we’ll need to do later.
**Jade** is an HTML templating engine.
We will add more dependencies as we find a need for them.

### STEP 3: CREATE INDEX.JS

Create a file called *index.js* directly inside *server-car-maintenance*. This file will define all of your other files and packages for the node compiler. *This file is often also called server.js, or app.js*.

Inside *index.js*, first add four of the dependencies we have installed:

```
var express = require('express');
var logger = require('morgan');
var mysql = require('mysql');
var path = require('path');
```

Initiallize logging:

```
app.use(logger('dev'));
```

Add an error handler. This will make sure that a stacktrace is printed when an error occurs in your dev environment:

```
// development error handler
if (app.get('env') === 'development') {
	app.use(function(err, req, res, next) {
		res.status(err.status || 500);
		res.render('error', {
			message: err.message,
			error: err
		});
	});
}
```