Jamis Buck (37signals), Jeffrey Hardy (37signals)

@jamis
@packagethief 

Services!
  How we share
  Some of the patterns we've used
  How it all works in concert
  500 requests per second across all apps
  
What's the glue?
  3 or 4 different ways will be presented
  Typical problems are shared concerned like billing, user auth, etc that don't want to duplicate
    Overtime took simple pieces out and split them out
  1. Plugins
  2. Redirect-to-Service
  3. Web-Service
  4. Shared Database
  No silver bullet!
    Don't usually try for bullet-proof
    We try for something simple and refactor
    Start small and Group up!
  
Plugins
  First resort when creating a service or identify shared concerns
  Services that aren't remote
  See duplication across apps, we abstract and create a plugin
  Very flexible and adaptable
  In essence, this is away to provide a service to your application
  Sadly
    Painful to maintain across all apps
    Should always write tests for plugin and run them

Redirect-to-Service
  Move plugin to standalone application which accepts requests
  App is its own entity
  Has a generic UI with maybe color scheme change
  Can't access these apps without going through another app
  Conventions
    Every application has an /account path which can be redirected back to from service
    Perishable signed url to POST needed data back and forth across domains, stateless
  Sadly
    Bypasses pain of plugins, there are still some pains
    Big win because we deploy to one location
    Pain is availability, when you punt someone over the wall, you can't guarantee success
    Hard to make completely external service look native
    
Web-Service   
  Supplement redirect-to-service to handle cases where stateless requests fail
  Expose REST API in each app
    Use plugin which creates a backchannel
    Thin layer/controllers for your apps to consume
    Plugin doesn't make an public requests on open internet
  Sadly
    Network latency
    Hidden complexity!
    In real life, its not as simple as you'd think
 
Shared Database
  Eliminates many network issues where tons of REST requests fail
  Engine style-plugin for shared models
    Feel like first call models
  Easy to read and write data
  Can nest database transactions which eliminates issues from errors across networks
  Where do you run migrations?
    Very tight integration
    Master/slave replication
    Migrate slave and promote it to master
    Simple schema, so its not changing often
    You can namespace tables
 
How are you doing it?
  Instead of redirect, hide everything behind a proxy with Apache
  Memcache shares info, but only for info which can be stale
  
Rails 3 going to solve problems with Engines?
  Much better organized
  Nice clean rails 3 engine file
  Provides better API for loading scheme
  Less tightly coupled
  
  
  
  
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
    
    
    
    
    
    
    