# impel.js
A module loading pattern 

## Questions
- Which modules does a page require on page load?  How do we tell it to load those modules?
- What about dynamically built pages from back-end templates?  Based on some conditionals templates may be dynamically loaded. If you have modules that are specific to dynamic templates, should we have to load that JS whether the DOM is present or not?  Ideally we only load the module with the template.
- What about dynamically built pages from front-end templates?  Sometimes we load a blank slate and some front-end templates fill in the content.  Those front-end templates may require a/many modules to function properly.  How do we manage the module loading there?
- What about simply lazy loading modules based on events that occur on the page?
- What if we want to do all these things, all at once, on a single page?

Extra questions:
- On this page, can I easily find out which modules have been loaded from my browser's inspector / view source?  
- Is a certain module relevant to the whole page or just some small section/component of the page?


## Existing solutions
- Bundle all your assets into one file.  It's cached anyways.  This works up to a certain point, but once that file starts to grow beyond 500kb gzipped you begin to wonder if you're really doing it right.  Also load time !== execution time.  Also source maps don't always work nicely.
- Manually managing it what needs to be loaded in some area of your UI/views?
- Manually managing it in disparate JS files?
- A front-end router?
- Some isomorphic custom strategy perhaps?


## My Answer
impel.js is a strategy to solve all these issues as effeciently as possible.  It aims to help developers write code that is easier to reason, manage and debug.

### How it works
// kinda needs work :: Handles duplicates by loading all requirements once then executing modules
