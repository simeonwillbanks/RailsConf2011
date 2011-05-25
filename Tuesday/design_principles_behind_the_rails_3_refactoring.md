José Valim (Plataforma Tec)
Core Team Member

SOLID! Design Principles Behind The Rails 3 Refactoring
* Look at Uncle Bob's Principles of OOD pdf

Single Responsibility Principle
  Rails 3 Refactor 
    Views
  Resolver
    Look for template
    If found, compile and return
    Resolver object no longer restricts templates to the filesystem like web service
  Resolver API is public API
    You can create your own abstractions, allowing you to read templates from the database
  Lookup context
    Tracking details
    Handles communication/params from Controller to ActionView::Base
  ActionView::Renderer
    rendering templates
  Get rid of huge objects and create small objects which can be easily replaced
    No more monkey patching!
    When you want to make a small change, you know exactly where to do it
    
Open/Closed Principle
  Language feature which we must implement well
  Easy to follow because Ruby classes all open for extensions...
  ...but easy to violate because ruby classes are not closed for modifications
  ActiveRecord::Base
    Can be modified from configs and app/plugins/etc are changed!
    Lets inherit and lets modify the subclass

Dependency Inversion Principle
  Easier to understand for dynamic languages
  Don't depend on anything concrete
  How do we accomplish DIP with Ruby?
    1. Define protocol
        Argument must respond to .call or specified method
        routes can accept RackApp
    2. Remove hard-coded dependancies 
        Ruby 1.9 FTW!
        Parameter default set in argument list
    3. Define hooks
        rails console --sandbox
          tightly coupled to ActiveRecord in Rails < 3
  Rails 3 Refactor
    Rails::Railtie
    
Liskov Substitution Principle
  Again, easier to understand for dynamic languages
  Make explicit what you want, so people know exactly what to implement, so it is substitutable
  Rails 3 Refactor
     Active Model
     These are the methods which must be implemented and should return specific value
      User.model_name
      User.persisted?
  How do we ensure objects are substitutable?  
    LintTest!!!
    
Interface Segregation Principle
  Clients should depend on as narrow protocol as possible
  Rails 3 Refactor
     Active Model
     Datamapper only needs to implement ten methods to substitute (persisted?, to_param)
  How to ensure a narrow protocol
    Test with mocks instead of unit tests
    Mock the methods which are the minimum methods to substitute (persisted?, to_param)
  Code to well-defined and narrow protocols
  Best way to define interfaces
    LintTests
      Test suite to very basic stuff
        what is definitely required
        data structures in/out
    Documentation
  

NOTES  
Rails Engines
  Gems which behave a lot like applications
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  