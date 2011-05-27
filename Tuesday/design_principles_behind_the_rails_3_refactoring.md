# SOLID Design Principles Behind The Rails 3 Refactoring
## José Valim (Plataforma Tec)
[Slides](http://assets.en.oreilly.com/1/event/59/SOLID%20Design%20Principles%20Behind%20The%20Rails%203%20Refactoring%20Presentation.pdf)  
[@josevalim](http://twitter.com/josevalim)    

### SOLID
[Uncle Bob's Principles of OOD](http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod)

### Rails 3 Refactor
#### Followed SOLID principles

### SINGLE RESPONSIBILITY PRINCIPLE
#### Views 
*  Resolver
  *  Look for template
  *  If found, compile and return
  *  Resolver object no longer restricts templates to the filesystem like web service
*  Resolver API is public API
  *  You can create your own abstractions, allowing you to read templates from the database
*  Lookup context
  *  Tracking details
  *  Handles communication/params from Controller to ActionView::Base
*  ActionView::Renderer
  *  rendering templates
*  Get rid of huge objects and create small objects which can be easily replaced
  *  No more monkey patching!
  *  When you want to make a small change, you know exactly where to do it
    
### OPEN/CLOSED PRINCIPLE
*  Language feature which we must implement well
*  Easy to follow because Ruby classes all open for extensions...but easy to violate because ruby classes are not closed for modifications

#### ActiveRecord::Base
*  Can be modified from configs and app/plugins/etc are changed!
*  Lets inherit and lets modify the subclass

### DEPENDENCY INVERSION PRINCIPLE
*  Easier to understand for dynamic languages
*  Don't depend on anything concrete
*  How do we accomplish DIP with Ruby?
    1. Define protocol
        *  Argument must respond to .call or specified method
        *  routes can accept RackApp
    2. Remove hard-coded dependancies 
        *  Ruby 1.9 FTW!
        *  Parameter default set in argument list
    3. Define hooks
        *  rails console --sandbox
        *  Use to be tightly coupled to ActiveRecord in Rails < 3

#### Rails::Railtie
* Example DIP in Rails 3 refactor    
    
### LISKOV SUBSTITUTION PRINCIPLE
* Again, easier to understand for dynamic languages
* Make explicit what you want, so people know exactly what to implement, so it is substitutable
* How do we ensure objects are substitutable?  
    * `ActiveModel::Lint` 
    * [ActiveModel Lint Test for RSpec](http://library.edgecase.com/Rails/2010/10/30/activemodel-lint-test-for-rspec.html)

#### ActiveModel
* These are the methods which must be implemented and should return specific value  
   `User.model_name`  
   `User.persisted?`  
* [Active Relation & Active Model](http://rubyonrails.org/screencasts/rails3/active-relation-active-model)
* [ActiveModel: Make Any Ruby Object Feel Like ActiveRecord](http://yehudakatz.com/2010/01/10/activemodel-make-any-ruby-object-feel-like-activerecord/)
    
### INTERFACE SEGREGATION PRINCIPLE
* Clients should depend on as narrow protocol as possible
* How to ensure a narrow protocol
  * Test with mocks instead of unit tests
  * Mock the methods which are the minimum methods to substitute (persisted?, to_param)
  * Code to well-defined and narrow protocols
* Best way to define interfaces
    * LintTests
      * Test suite to very basic stuff
        * what is definitely required
        * data structures in/out
    * Documentation
  
#### ActiveModel
* Datamapper only needs to implement ten methods to substitute (persisted?, to_param)
* See ActiveModel notes from *LSP*

### NOTES  
* Rails Engines
  * Gems which behave a lot like applications
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  