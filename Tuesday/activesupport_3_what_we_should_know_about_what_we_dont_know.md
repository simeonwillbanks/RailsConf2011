Bryan Liles (Smarticus)

NOTES
  ActiveSupport provides the robustness behind Rails
  http://smartic.us/doodads/presentations/railsconf2011/

HISTORY LESSON
  Ruby facets
    Fill in gapping hole with niceties that ruby should give you
  Split into 
    Core
      Hash.keys_to_symbols
    More
      Memoization
    Awesome
  Y-Combinators

ActiveSupport
  Extracted from ActionPack and ActiveRecord
  Convert a String to a Constant
  Singularize and Pluralize
  Time Zones
  
Accessors
  Becoming More Accessible
  Module and class level accessors  
  mattr_accessor / cattr_accessor
    both in facets!
  attr_accessory_with_default

Benchmarks
  benchmark method is passed a block
  
Callbacks
  set_callback
  after_save
  
Concerns
  DSL allows you to get rid of setup for module/mixin
  Defines API which keeps you from mucking around Rails internals
  
Configurable
  Include the module and get freebie configuration
  app.config
  Notifications/Listeners than Act
  Code with problem at hand instead of worrying about every single case
  
Random
  Gzip
  Generate random strings
  
Rails 3
  Can require individual pieces of ActiveSupport instead of entire module
    Ruby Facets already does this, so lesson learned
    
Questions?
  What is up with facets?
    On github
  How do I learn more about Ruby Facets?
    Ruby Works website
    Read the source
  How do I learn more about ActiveSupport?
    Read the source!
  


















