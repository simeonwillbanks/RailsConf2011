# OmniAuth from the Ground Up
## Michael Bleigh (Intridea)
[Slides](http://www.slideshare.net/mbleigh/omniauth-from-the-ground-up-railsconf-2011)  
[Screencast](http://intridea.com/2011/5/31/omniauth-from-the-ground-up)
[@mbleigh](http://twitter.com/mbleigh)  
[@sferik](http://twitter.com/sferik)  

### OMNIAUTH
* Auth lib for rack apps
* Goals
  * **Login with anything**
  * **Assume nothing!**
* Generic framework which gives you ability to do auth anywhere in your app
* Never wants to take control away from application
* Collection of gems, lots of dependencies, a little bit monolithic
  *   Simplicity but tradeoff
  
### NOTES
  [Tutorial for adding a new strategy](http://anti-pattern.com/2011/4/24/adding-a-new-strategy-to-omniauth)  
    
    
### PAST
* Why are there so many auth frameworks?
  *   These libraries all make assumptions:
    *     I only need one User model
    *     User will signup and provide password
  *   I don't want to customize too much what my auth library does!
* I'm building my app around my auth library, not inserting an auth library into my app
* I need a single NORMALIZED SYSTEM for auth
* I need Auth > Magic > User Info
  *   Right level of magic
  *   All I need is User Info!
  *   Idea behind OmniAuth
  *   Simple way for you to say I need auth, ok, here is the user info!
* It takes a very long time to make easy things!
  *   Very hard mental problem instead of development problem
  *   Don't want to constrain the user without giving them a lot of headaches
* Grown very large very quickly
  
### PRESENT
* Future is now which is 1.0 beta
* oa-identity
  *   username/password for each user
  *   Difficult because had to avoid assumptions
  *   Does almost nothing!
    *     No email verification
    *     No user model
  *   Way for person to specify a small amount of info like name/email and here is a password to verify my account
  *   Just another OmniAuth stradgey
  *   `/auth/identity`
  *   `/auth/identity/callback`
  *   `/auth/identity/register`
  *   Same error flow as other OmniAuth providers
  *   Bare minimum your app needs to identify the user! No bio
  *   OmniAuth as your ONLY auth with oa-identity!!!
* OmniAuth is a framework it isn't a blackbox
  *   Reality is its simple which can be hacked
  *   See "The Guts" slide
  *   See "Request Phase" slide
    *     Get everything setup, so I know enough about the person to build a user_info hash
  *   See "Callback Phase" slide
    *     Creates the user info hash!
* OmniAuth only requires Request and Callback phases to be a complete strategy
  *   Creating developer strategy on the fly!
* Framework which can login to anything and assume nothing
  
### FUTURE
* More Tests! 
  *   Figure out how to test 40+ strategies with all creds
* More Docs!
* Convenience helpers/methods/refactor
  *   Potentially building a strategy is a DSL
  *   Building a strategy should be super simple
* More Strategies!














