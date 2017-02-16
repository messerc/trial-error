---
title: React SPA from scratch (3 of 6) 
date: 2017-01-20 18:31:56
tags:
---

## Part 3: 'Hello API' with React

Working with APIs can be a real hurdle in getting your idea from your brain to the browser. The concept is intuitive, but the execution can feel delicate. 

I want to walk through getting setup with the Twitch API as I generally didn't find many resources that walked through each step in detail. 

```bash
touch src/client.js
```

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(
	<h1>Waddup Dawg</h1>, 
	document.getElementById('app')
)
```
First commit from my mac, this is very cool. 

