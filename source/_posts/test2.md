---
title: React SPA from scratch (2 / 6)
date: 2017-01-20 18:31:51
tags:
---

### Part 2: Starting...with stuff that isn't React

#### It starts with one file - package.json 

_note: If you're already comfortable with npm, webpack, and getting a project started, you're good to skip this section_

If you're like me, you value doing examples on codepen and jsfiddle only to a certain degree. I was always thinking "this is cool...but I still don't really get how this all comes together start to finish for a real page".

So let's start from a blank directory. Open up your terminal and input the following:

__note: If you don't have nodeJS, that's the very first thing [we'll be getting](https://nodejs.org/en/). All we're getting nodeJS for is for its ["npm"](https://docs.npmjs.com/getting-started/what-is-npm) - node package manager.__

```bash
mkdir twitchreact   # makes the directory 
cd twitchreact   # goes into the directory
npm init -y  # 'initializes' a package.json file for you in the directory and the -y just means "say yes to all defaults"
```
If you've never worked with a package.json file before, I promise it's very gentle and won't hurt you with scary syntax. And the best part is that *not much magic is happening*, you will quickly get a handle on this.  

So if you open up that directory, all you'll see for now is that one package.json file, and here are the contents.

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

_note: a "script" is something that just runs in the command line, and is purely for convenience. For example, if you type "npm test" in the command line right now, it will go into this file, find "test" in the scripts section, and just run "echo \"Error: no test specified\" && exit 1" in the command line. So there is zero difference between typing "npm test" and "echo \"Error: no test specified\" && exit 1", you're just saving keystrokes. I did not figure this out right away...and it helps to clarify at least one more part of the file._

#### Webpack

To see package.json in action, let's install a build tool called [Webpack](http://webpack.github.io/). 

_note: At first, I was a little intimidated by Webpack and build tools in general. The configs looked scary, and I didn't quite "get" it. However, I can assure you that between reading their docs and getting through this project, you'll not only understand Webpack better, but truly appreciate what it does for you._

```bash
npm install -save webpack # saying: "hey node package manager, install webpack and save it as a dependency"
```

A couple of key things have now happened. 

1. If you check your package.json file, you will see that Webpack now makes an appearance. 

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

2. 









