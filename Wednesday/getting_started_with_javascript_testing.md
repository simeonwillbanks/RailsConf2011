# Getting Started With JavaScript Testing
## CJ Kihlbom (Elabs)
## Jonas Nicklas (Elabs)
[Slides](http://front-end-testing-talk.elabs.se/)  
[@jonicklas](http://twitter.com/jonicklas)  
[@cjkihlbom](http://twitter.com/cjkihlbom)  

### NOTES
  [@trevmex](http://twitter.com/trevmex) [presentation notes](http://trevmex.com/post/5608062141/getting-started-with-javascript-testing)

### HOW TO TEST JAVASCRIPT
1.  Unit testing
2.  Integration testing
  
### UNIT TESTING WHAT?
* Good for widgets
* Anything that doesn't use rails
* Standalone on client side
* Use Evergreen & Jasmine 

### INTEGRATION TESTING WHAT?
* View code like Ajax
* Complicated DOM
* Use Capybara & Cucumber 
  
### CAPYBARA
* Use for integration testing
* Simulates user behavior
* Key diff with webrat is capybara is driver agnostic
  *   Drivers execute API
  *   See slides for drivers table with good and bad characteristics 
  *   Default is selenium
* Bundles cucumber
* Specs
  *   :js => true
* Scenarios
  *   tag with @javascript
* Capybara is smart, so you don't need to rewrite your integration tests
* Capybara will use JS driver under the hood
  
#### CAPYBARA DONE WELL
* Write tests with the user in mind
  *   When writing tests, get into head space of user
  *   How does user understand app?
  *   Tests should read as users would have written them
  *   Use DSL to create your own tests
    *     Describe test as action
    *     Abstract method, create module, and include module
    *     `sign_in_as('jacob')`
    *     Extend Capybara to create DSL for your site

#### USE CUCUMBER TO ABSTRACT COMMON PATTERNS
* Cucumber is meant to create user workflows
* Write step text in plain english
  *   Features more stable because more resistant to change
* Keep away anything code related from your tests
  *   As an example, don't scope with CSS selector!
* Test must be something the user understands!
  
#### USE CAPYBARA API SELECTORS GRACEFULLY
* `find(:whiskey, name)`
* Capybara.add_selector
* Speaking in terms of whiskeys instead of XPath selectors
  
#### ASSERT ON WHAT USER CAN SEE
* On things user can see or care about should be asserted on!
* Asserting on URLs, cookies, sessions are brittle and resistant to change
* Should be able to refactor code without breaking specs
  *   Avoid tying test to implementation
  
#### BE AS LENIENT AS POSSIBLE
* Don't use selectors like IDs
* Tests shouldn't care about the markup of the page
 
#### MAKE GENERIC ASSERTS
* Do not be brittle
* Assert on text or text should be in particular area
  
### JASMINE
* Stable and maintained by Pivotal
* Small but featured filled
  *   Assertions
  *   Spies
* General Purpose
  *   Can test for standalone JS or test script in Rails app
  *   Not tied to specific JS code
    
### EVERGREEN
* Well packaged Jasmine
* No generators since everything is bundled in the gem
  *   Easy to update once new versions come out
  *   No setup
  *   Works great with rails
  *   Just added to Gemfile!
* Not tied to rails so can use in Sinatra or even PHP
* Nice syntax via CoffeeScript
* Number of ways to run tests
  *   Easiest is to load /evergreen in browser
  *   Mounts engine in rack app
  *   Perfect for TDD for quick feedback loop, tests run quickly in any rack app
* Run JS tests in any browsers
* Run JS from command line in order to run the entire suite
  *   rake spec:javascripts
  *   rake spec:javascripts CHROME=true
  *   Use any capybara driver so you can run headlessly 
* Finds tests in spec/javascripts with _spec.js
* Syntax is familiar, looks like RSpec
* Has require to include JS
* Has JS fragments so you can include DOM fragments in tests
  *   Evergreen reloads fragments for each tests so you don't get collisions
* Remember, this is normal Jasmine, so all other features are available
* Yet, some custom selectors have been added like .toHaveElement()
* If you change _spec.js to _spec.coffee, you can write CoffeeScript tests
  *   Cleaner syntax and more clear what the tests are actually doing
  *   Less line noise

### SUGGESTIONS ON HOW TO WRITE BETTER JS UNIT TESTS
* Write more testable code
* Structure code into more units
  *   Use functional aspects OR
  *   Use Objects
    *     Use prototype inheritance to create units of code
    *     CoffeeScript has class concept which is thin wrapper around prototype inheritance
      *       Looks like Ruby!
      *       OO Makes it familiar and closer to Ruby
      *       Take knowledge from writing good Ruby code and translate into good JS
  *   Needs some kind of structure
* Don't do jQuery DOM spaghetti (see slides)
  *   Iterate, inject DOM elements, add events
* Stick to single JS pattern throughout application
* Separate JS code into files!
  *   Done for you via Asset Pipeline in Rails 3.1
* Always tests class methods
  * Mostly test the event bindings
    *   Sometimes it gets really complicated and feels like your bending over backwards
    *   Let integration tests catch event bindings
    *   Experiment and see how it feels
* Write custom matchers!!! 
* Isolate Away AJAX
  *   Real pain point when unit testing
  *   Abstract into component which isn't tested by unit tests
  *   Use integration tests
* Mock AJAX if necessary
  *   Spy framework in Jasmine
* Treat templates as fixtures
  *   Update them manually
  *   This is encouraged by Evergreen
* Use integration tests to validate templates
* Simplify your DOM which will simplify your templates
  *   Views change frequently
  *   Tests shouldn't test complicated views?  
  
  
  
  
  
  
      
      
      
      
      
      
      
      
      
      
      
