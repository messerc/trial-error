---
title: React SPA from scratch (2 of 6) 
date: 2017-01-20 18:31:51
tags:
---

### Part 2: Starting...with stuff that isn't javascript 

_initial note: If you already know what npm and webpack are, and familiar with project structuring, you're good to skip to the bottom 'summary' section and run that code. If you've never opened up the terminal, I hope this is gentle enough._


If you don't have nodeJS, that's the very first thing [we'll be getting](https://nodejs.org/en/). All we're getting nodeJS for is for its ["npm"](https://docs.npmjs.com/getting-started/what-is-npm) - node package manager. 

Now let's start from a blank directory. Open up your terminal, navigate your way to any reasonable folder, and input the following:

```bash
mkdir twitchreact   # makes the directory 
cd twitchreact   # goes into the directory
npm init -y  # 'initializes' a package.json file for you in the directory and the -y just means "say yes to all defaults"
```
<!-- more -->

If you've never worked with a package.json file before, I promise it won't hurt you with scary syntax. If you open up the directory, all you'll see for now is that one package.json file, seen below. 

```json
{
  "name": "twitchreact",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

This package.json file will be a hub of information about our project. It will tell anybody what "dependencies" we have (like React), and include some simple "scripts" for us to run our project. It helps keep track of everything, and it does so automatically. 

_note: a "script" is something that just runs in the command line, and is essentially for convenience / standardization. For example, if you type "npm test" in the command line right now, it will go into this file, find "test" in the scripts section, and just run "echo \"Error: no test specified\" && exit 1" in the command line. Another common script is "start" and it typically starts up your application, which only makes sense. Absolutely use these, [read more here.](https://docs.npmjs.com/misc/scripts)_

### Installing our first dependencies

To see package.json in action, let's install a build tool called [Webpack](http://webpack.github.io/). 

_note: At first, I was a little intimidated by Webpack and build tools in general. The configs looked a little strange, and I didn't quite "get" it. However, I can assure you that between reading their docs and getting through this project, you'll not only understand Webpack better, but truly appreciate what it does for you._

```bash
npm install -save webpack # saying: "hey node package manager, install webpack and save it as a dependency"
```

A couple of key things have now happened. 

* In your package.json file, you will see that Webpack has been added as a dependency. 

```json
{
  "name": "twitchreact",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "webpack": "^1.14.0"
  }
}
```
* In your project directory, there is now a "node_modules" folder, and it has Webpack and whatever else Webpack needs to do its thing.

Let's also install [Babel](https://babeljs.io/). Babel and its various modules will help Webpack compile our code. 

```bash
npm i -S babel babel-core babel-loader babel-preset-es2015 babel-preset-react 
```

Now install react (and react-dom, which is needed for some stuff we'll cover later)

```bash
npm install -save react react-dom # shorthand for this would be: npm i -S react react-dom 
```

### Structuring your project directory 

As you learn about react, one thing you'll notice is that you'll be making a lot of "components". So if you've been throwing all of your javascript code into one file, that will change here. As a result, you need to have a way to have all of the separate js files you write "bundle" into one javascript file at the end with all libraries included. This is what webpack does for you...and webpack needs to know how your project directory is setup to a certain degree. At its core, webpack is going to be looking for an "entry" point (as in "what files am I bundling for you?") and an "output" point ("where do you want me to dump this one massive file I've made for you?").

With this in mind, let's start making the project structure. 

```bash
mkdir dist # this directory is going to hold what we want to 'distribute' out to the world, and will contain our "output" point for webpack
mkdir src # this will be our source folder, it will hold all of the files we'll be actively working on 
mkdir src/js # this will contain all of our js files, and will contain webpack's "entry" point
```

So now your directory should look like this. 

```
twitchreact (main directory)
│   package.json
│      
│
└───src (folder)
│   │   
│   │   
│   │
│   └───js (sub-folder) <-- this is where we'll be adding most of our work 
│       │   
│       │  
│       │   ...
│   
└───dist (folder)  <-- this is where we'll have all the "final" files ready to be consumed by the browser 
│ 
│          
│        
│       
│   
└───node_modules (folder)
    │   all your dependency stuff ... (just webpack and react stuff for now)

```
### Setting up the 'dist' directory

```bash
touch dist/index.html
touch dist/twitch.css # this is optional, and there are many opinions on styling react. 
```
index.html is simple.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- Slate CSS Theme -->
  <link rel="stylesheet" href="https://bootswatch.com/slate/bootstrap.min.css" />
  <link rel="stylesheet" href="twitch.css" />
  <title>twitch.show</title>
</head>
<body>

  <div id="app"></div>


<script src="https://use.fontawesome.com/470e91b33f.js"></script>
<script src="bundle.js"></script>
</body>
</html>
```

A very basic html file with the most critical parts being:

a) a div with the id "app" to receive our entire react application.
b) a script with source "bundle.js" which has yet to be created, but that will be webpack's job later on.

I've also grabbed a simple bootswatch theme to start with.


## Summary

We initialized a package.json, started installing some of our dependencies, shaped our basic project structure, and created our index.html file. The next section will dive into getting React working. 

## The code we ran in this section:

### In the terminal

```bash
mkdir twitchreact   
cd twitchreact   
npm init -y  

npm install -save webpack
npm install -save react react-dom

mkdir dist
mkdir src
mkdir src/js 

touch dist/index.html
touch dist/twitch.css
```
### Index.html 

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- Slate CSS Theme -->
  <link rel="stylesheet" href="https://bootswatch.com/slate/bootstrap.min.css" />
  <link rel="stylesheet" href="twitch.css" />
  <title>twitch.show</title>
</head>
<body>

  <div id="app"></div>


<script src="https://use.fontawesome.com/470e91b33f.js"></script>
<script src="bundle.js"></script>
</body>
</html>
```






















