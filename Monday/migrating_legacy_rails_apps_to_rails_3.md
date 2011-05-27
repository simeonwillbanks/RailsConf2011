# Upgrading Legacy Rails Applications to Rails 3
## Clinton R. Nixon (CRNixon Development)
[@crnixon]("http://twitter.com/crnixon")  
[Slides [PDF]](http://assets.en.oreilly.com/1/event/59/Upgrading%20Legacy%20Rails%20Applications%20to%20Rails%203%20Presentation.pdf)  
[Curated list of links on upgrading which provide foundation for talk]("http://pinboard.in/u:crnixon/t:rails3upgrade")  

### TOP 10 REASONS TO UPGRADE
 10.ARel - ActiveRelation  
 9. jQuery - unobtrusive JS via attributes  
 8. Bundler now painless  
 7. Easier to hire new developers  
 6. Get ready for Rails 4 - Rails 3.1 in beta  
 5. Way faster than Rails 2.x - Decoupled   
 4. ActiveModel lets you treat everything like ActiveRecord - Niceties/Helpers/Etc abstracted into Modules  
 3. Don't have to use ActiveRecord - See #4  
 2. Cut your controllers down to size with respond_to  
 1. Get some sleep - Antidotal for conf  
    
### GETTING READY WITH RAILS 2.3
Improve practices in application since 2.3 gets you ready for 3.x and makes upgrade process easier  
        
#### RAILS 2.3.11
*  rake rails:update
*  Getting rid of all deprecations
*  Install rails_xss plugin and fix views
      Most painful part!
      Don't need to use h helper, its the default
      Choose parts of view to escape or not
      Whitelist don't blacklist
         
### RAILSXSS
*  Strings are not safe by default
*  String interpolation always makes strings not safe
*  raw helper is opposite of h helper
*  .html_safe marks strings as safe  
    `def clippy()
      "#{unsafe} string" # but really it is
      html.html_safe
    end`
    
### FAKE_AREL
*  Actually lazily loaded
*  Uses named scopes which will be deprecated in Rails 3
  
### RESTFUL CONTROLLERS
*  Now is a great time to refactor your controllers to be RESTful
*  New routes syntax in Rails 3 works great with RESTful
  
### OTHER IMPROVEMENTS
*  Use YAJL for JSON processing if installed yajl-ruby
*  Flash:alert and notice promoted  
     `redirect_to(@post, :notice => 'Post was created')`
*  Object#presence
*  Object#tap instead of Object#returning which is removed  
      `[].tap do {|x| x << "hello"}`  
   *  Can tap into chain of methods at any point and pass a block  
   *  Good for debugging  
*  Non-ActiveRecord fixtures will break in test/fixtures
  
### WORKING WITH BUNDLER  
*  Auto-generate your initial Gemfile using the rails_upgrade plugin  
   $ rake rails:upgrade:gems
*  bundle install --deployment, automated by capistrano
   
### USING BUNDLER EFFECTIVELY
*  Install gems locally instead of into system location (alternative to gemsets)  
    $ bundle install --path vendor
   *  Easier to inspect packaged gems since there in project path
*  Package gems
    $ bundle package
*  Check your Gemfile.lock into VCS
*  Make bundle alias especially for bundle exec
*  bundle install in production  
   *  installs gems with native C extensions directly on each environment
*  bundle update  
   *  use when upgrading/updating gems
*  [Details on bundler workflow]("http://ryan.mcgeary.org/2011/02/09/vendor-everything-still-applies/")

  
### PLUGINS & GEMS
Popular plugins are now gems, so replace plugin with gem
  
### USING THE RAILS_UPGRADE PLUGIN
*  When ready to upgrade, make sure this is installed as plugin
  *    Since it will work in Rails 2 and Rails 3
*  rake rails:upgrade:check
  *    Save stdout to file for reference and a checklist which needs to be done
*  rake rails:upgrade:backup
  *    Not useful if on git since VCS handles this for you
*  rake rails:upgrade:gems
   *  Doesn't check environments, so not perfect
   *  Checks config/environment.rb for config.gem lines and then spits out a Gemfile
*  rake rails:upgrade:routes
   *  Automatically converts all old-style routes to Rails 3-style routes but Not Perfect!
   *  Old style routes are deprecated so complicated routes will still work
   *  Rails 3 routes
      *  Can have optional segments
      *  Matches top to bottom instead of bottom to top (rails 2)
*  rake rails:upgrade:configuration
   *  Not very useful
    
### TAKING THE RAILS 3 PLUNGE
$ rails new . -d <database>
  
### IMMEDIATE FIXES
*  Remove preinitializer.rb which was for bundler
*  lib/directory not autoloaded by default but in lib path  
   `config.load_paths += %W(#{config.root}/lib)`
    
### JAVASCRIPT FIXES
*  Unobtrusive JS!
   *  JavaScript adapter adds behavior through element attributes
*  JavaScript just works different in Rails 3
*  javascript_include_tag :defaults in views
*  Add csrf_meta_tag method to <head> which emits things like authenticity_token
*  Use new methods for  
    `link_to_remote`    >   `link_to`  
    `form_remote_tag`   >   `form_tag`  
    `form_remote_for`   >   `form_tag`  
    `remote_form_for`   >   `form_for`  
*  RJS files might have to be rewritten
    
### FORM FIXES
*  form.error_messages is gone!
*  use simple_form for rails 3 and be happy
  
### JSON
*  [as\_json intead of to\_json]("http://jonathanjulian.com/2010/04/rails-to_json-or-as_json/")
  
  
### FIXING & REPLACING DEPENDENCIES
*  RSpec must be upgraded to rspec 2
*  Cucumber uses test instead of its own environment
*  Factory Girl requires `factory_girl_rails` gem for rails 3
*  will_paginate has beta branch, but checkout kaminari gem as replacement
*  Searchlogic does model based search suitable for admin interface
  *  Now use MetaSearch!
*  AttachmentFu wont work so use Paperclip or possibly CarrierWave 
    *  Paperclip and CarrierWave both work with Rails 2
    *  Paperclip is good for basic file upload like avatars
    *  CarrierWave is very different and good for image/document processing (decouple files from models)
*  For Solr, you should use `sun_spot` instead of `acts_as_solr`
    
### RAILS 3.1 UPGRADE NOTES
*   Get [Jeremy McAnally's upgrade to Rails 3 ebook]("http://omgbloglol.com/post/344792822/the-path-to-rails-3-introduction")
*   Look for discreet parts you can upgrade without breaking your application
*   git add --patch  
      show changes which have been made   
      allow you to directly edit changes to be applied
*   Test things that are hard
*   Don't write tons of unit tests; write tracer bullets via capybara 
*   Real time search can be done in Solr; Sphinx fudges with deltas

*   3.0 deprecations are removed in 3.1
*   Old query syntax for ActiveRecord is removed
*   Assets work with sprockets
      app/assets
      Unlimited filters
      Uses preprocessors
      Uses SASS by default
      Files are all cached in production
  


















    
    
    
    
    

  
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
  
  
  
  
  
  
  
  
  
  
    