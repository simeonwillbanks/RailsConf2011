Mikel Lindsaar
ActionMailer
Top 20 committers
rubyx.com

NOTES
  http://speakerrate.com/talks/7575
  Ruby Patterns is an excellent book
  Thats how I get my sexy code off
  Ruby is easy!
    If you are writing Ruby and its pissing you off, you are doing it wrong
    Go and read the standard Ruby documentation online

WHAT IS ON THE TRACKS?
  Context switch rapidly
  Future proof
  Scalable
  Two ends
    Working code
      Maybe tested, but not refactored
    Sexy code
      Time waster especially when code is used little
  What is in between?
    Maintainable code
      Has the correct pattern applied, yet not a case study on the pattern
      Code must be readable! Code must be trivial to understand
  Product is Only a Product if its Exchanged
    Don't waste your time by coding products which don't get used
  Budget Matters
    Beautiful code is ugly if no one buys it
  Trade-Offs are Life
    Decide where and how to refactor
      Code which is core to business should be refactored
  You are not selling code
    You sell a solution
    They want product to work and be maintainable
    Running App must work in production!
 
HOW DO YOU KEEP A RAILS APP ON THE TRACKS? 
Deployment is a First Class Citizen
  Should be Documented
    Must be trivial to deploy to staging and production
  Repeatable Configuration
    Use chef or puppet
    Use common deployment methods
  Use Bundler
    Be explicit with versions
    Only lock to git repos you own
  Make a db/seeds.rb
    Make it easy for other Developers
    Other developer may be you
  Link in Security
    Don't store passwords in the app
    Use some other data store!!!
    app gem
      http://rubygems.org/gems/app
      Constant which can be called from anywhere in app
      app.config
      symlink shared directory on production which is deployed separately
    List where ssh keys will be located
    
Fast Page == Happy Client
  Combine JS & CSS
    3.1 has asset pipelining
  Caching Optimization
    Fragment Caching
      Can have issue with not expiring
      For fragment name, use sha from current version
      Push to production, invalidate all fragment cache
  
Big Session == Slow Site  
  Store values, not objects
    Store a string or a number
  Pick Your Fights
    Don't make a persisted session cart for each user
  Only fire up session in controllers actions where you need it
  
Opinions Matter
  Don't buck the conventions in Rails
    Use pluralization
  Ruby also has opinions
    Use idioms
  Remove useless code
    Less codes equals less bugs
    
Being Smart can be Stupid
  Don't do something cute your future self will want to kick you!
  Explicit Methods
    Don't use before, after and around filters for obj instantiation
      Filters inherit to subclasses which can introduction confusion
  Keep Tests Simple
    Computers are good at nesting code but humans are not!
    Instead of nested context, use a declarative helper
    Can be WET but who cares! Tests are for humans not computers
  Simple is better than Complex
    What you leave out is almost more important than what you put in
    Meta Programming has its place, but probably not in a Rails app
  Good code is Easy to Read
  
Reinvention is Overrated
  Use Rails instead of reinventing a controller

Use the right tool for the right job
  Cucumber is not unit test! Write a spec!!!
  
Databases have feelings too
  You don't need database agnostic code
  Be aware you have a database, and use SQL where you need to handle data
  Use DB tools available for specific DB
    Example: PostgreSQL COPY with generated CSV
  Don't share the DB
    Refactor into API calls
    
Beware the Train Wreck
  Give responsibilities to code underneath a very long chain of methods
  i.will.beware.of.nil
    
Control Flow is actually Code Smell
  If you have a lot of case statements or a very LARGE if statement
  
SUMMARY
  Apps that work, easy to maintain and are bug free!!!
  Make your Rails code maintainable
    
    
    
    
  
  
  
  
  
  
  
  
  
  
  