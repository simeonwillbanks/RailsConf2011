# ActiveSupport 3: What We Should Know About What We Don't Know
## Bryan Liles (Smarticus)
[Slides]("http://smartic.us/doodads/presentations/railsconf2011/")  
[@bryanl]("http://twitter.com/bryanl")  

### HISTORY LESSON
* Ruby facets  
  *  Fill in gapping hole with niceties that ruby should give you
  *  Split into   
      `Hash.keys_to_symbols`  
      `Memoization`  
* Y-Combinators

### ActiveSupport
* Extracted from ActionPack and ActiveRecord
* Convert a String to a Constant
* Singularize and Pluralize
* Time Zones
  
### ACCESSORS
* Becoming More Accessible
* Module and class level accessors  
* `mattr_accessor` / `cattr_accessor`
* `attr_accessory_with_default`

### BENCHMARKS
* benchmark method is passed a block
  
### CALLBACKS
* `set_callback`
* `after_save`
  
### CONCERNS
* DSL allows you to get rid of setup for module/mixin
* Defines API which keeps you from mucking around Rails internals
  
### CONFIGURABLE
* Include the module and get freebie configuration
  `app.config`
* Notifications/Listeners than Act
* Code with problem at hand instead of worrying about every single case
  
### RANDOM
* Gzip
* Generate random strings
  
### RAILS 3
* Can require individual pieces of ActiveSupport instead of entire module
  * Ruby Facets already does this, so lesson learned
    
### QUESTIONS?
* What is up with facets?
  *   On github
* How do I learn more about Ruby Facets?
  *   Ruby Works website
  *   Read the source
* How do I learn more about ActiveSupport?
  *   Read the source!
  


















