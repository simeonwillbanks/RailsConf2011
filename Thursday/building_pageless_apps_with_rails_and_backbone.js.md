# Building Pageless Apps with Rails and Backbone js
## Matt Kelly (ZURB)
[Slides](http://assets.en.oreilly.com/1/event/59/Building%20Pageless%20Apps%20with%20Rails%20and%20Backbone%20js%20Presentation.pdf)
[@mkelly12](http://twitter.com/mkelly12)   
[Kesha - Blow](http://www.youtube.com/watch?v=mpzYLM7PWak)  

**Backbone.js is a single file, 4KB and source is totally readable**   

[Christopher Jeris](http://twitter.com/ystael)
> good talk. also best use of Ke$ha in programming conference.

### NOTES
* Read JavaScript: Only The Good Parts
* Backbone.js is smaller and lower learning curve than Sproutcore
* Sproutcore has more features
* Backbone.js requires you to write logic a second time if you want to degrade with no JS
* #! Google replaces with escape token, so google will make new request, and you can give content to google
* [http://chopapp.com](http://chopapp.com/)  

### WHY IS THIS GOOD?
* Quick under 100 milliseconds
* Don't loose users attention because stay in context
* Users have very measured response times
  *   We must aim for responses in under a second!
  *   Anything that takes longer than one seconds, the user looses the flow
  *   If it takes longer than 10 seconds, we loose the user
    
### WE NEED GLUE CODE BETWEEN JQUERY AND RAILS
* Don't want to harm user
* Need to be able to bookmark pages
  
### LETS BUILD AN APP
* Use JavaScript templates for loading partials on client side!
* In backbone, Views combine both presentation and behavior
* `this.$('form')` is backbone shortcut for `$('form', this.ele)`
  *   Keep views within context
* Backbone follow the convention where this is current object!
* Models abstract away persistence layer
* Backbone deals with shallow objects!
* Be careful of events which do not bubble, look up on jQuery site
* Bind events on view, and backbone will handle the magic
* MVC covered, but one more thing called collections
  *   Give it model and url
  *   It is a helper
* You can inherit from existing views, so you can overwrite actions you'd like to behave differently
  
**Design for people!**
