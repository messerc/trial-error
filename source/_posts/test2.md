---
title: React SPA from scratch (2 of 6) 
date: 2017-01-20 18:31:51
tags:
---

### Part 2: Starting...with stuff that isn't javascript 

_note: If you're already comfortable with npm, webpack, and project structuring, you're good to skip to the bottom 'summary' section and run that code_

Let's start from a blank directory. Open up your terminal and input the following:

__note: If you don't have nodeJS, that's the very first thing [we'll be getting](https://nodejs.org/en/). All we're getting nodeJS for is for its ["npm"](https://docs.npmjs.com/getting-started/what-is-npm)  - node package manager.__

```bash
mkdir twitchreact   # makes the directory 
cd twitchreact   # goes into the directory
npm init -y  # 'initializes' a package.json file for you in the directory and the -y just means "say yes to all defaults"
```
<!-- more -->

If you've never worked with a package.json file before, I promise it's very gentle and won't hurt you with scary syntax. If you open up the directory, all you'll see for now is that one package.json file, seen below. 

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

This package.json file will be a hub of information about our project. It will tell anybody, including yourself, what "dependencies" we have (like React), and include some simple "scripts" for us to run our project. It helps keep track of everything, and it does so automatically. 

_note: a "script" is something that just runs in the command line, and is essentially for convenience / standardization. For example, if you type "npm test" in the command line right now, it will go into this file, find "test" in the scripts section, and just run "echo \"Error: no test specified\" && exit 1" in the command line. So there is zero difference between typing "npm test" and "echo \"Error: no test specified\" && exit 1", you're just saving keystrokes. Maybe I am the only one who did not figure this out right away...but felt it was worth clarifying._

#### Installing our first dependencies

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

Now install react (and react-dom, which is needed for some stuff we'll cover later)

```bash
npm install -save react react-dom # shorthand for this would be: npm i -S react react-dom 
```

#### Structuring your project directory 

As you learn about react, one thing you'll notice is that you'll be making a lot of "components". So if you've been throwing all of your javascript code into one file, that will change here. As a result, you need to have a way to have all of the separate js files you write "bundle" into one javascript file at the end with all libraries included. This is what webpack does for you...and webpack is concerned with how you have your project directory setup to a certain degree. At its core, webpack is going to be looking for an "entry" point (as in "what files am I bundling for you?") and an "output" point ("where do you want me to dump this one massive file I've made for you?").

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

TO ADD NEXT: getting dist setup with files 
THEN - adding first JS file to source (client.js) 
THEN - summary section - summary code - and onto part 3 



















