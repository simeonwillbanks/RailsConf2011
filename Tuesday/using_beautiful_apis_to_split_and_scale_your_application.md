# Using Beautiful APIs to Split and Scale Your Application 
## John Crepezzi (Patch) 
[Website](http://seejohncode.com/)  
[GitHub](http://github.com/seejohnrun)  
[@seejohnrun](http://twitter.com/seejohnrun)  

*Splittin 'Yo' App*  

### GEMS
[flexible\_api\_server](https://github.com/seejohnrun/flexible_api_server)  
[flexible_api](https://github.com/seejohnrun/flexible_api)  

### SERVICES
*  Taking app and making separate pieces which talk to each other to accomplish a unified goal
*  Import Facets
  *    Scaling
  *    Testing
    *      Can test individually and speed up testing
  *    Maintainability 
*  How does this relate to an API?
  *    Differences
  *    Similarities
    *      Application logic such as sign up a user
    *      Data is the same from app and services
*  What does this mean?
  *    You duplicate logic from app and API  
*  Who eats their own dogfood? Who uses a thin web service on their own web site?
  *    Twitter
  *    City's Best
  
### CURRENT APPROACHES WITH PROBLEMS
*  respond_to
*  respond_with
  *    On PUT, will redirect to new object
*  mkdir app/controllers/api
*  `cp -Rf app app_api`
  
### BETTER APPROACH
*  FlexibleApi
  *    Commonalities have been abstracted
  *    Request Levels
    *      Determine what people need instead of giving them the entire object
  *    Notations
    *      Same as setting request level, but accepts block which can customize response
  *    Inclusions
    *      Request levels can include relations
*  FlexibleApiServer
  *    Built on top of Sinatra
  *    Builds documentation based on requests
    
### MORE CONSIDERATIONS
*  Clients interfacing with API
  *    constructor-rb
*  Rate limiting
  *    middleware
  *    apache phusion
*  Authentication
  *    Use pass or halt in sinatra
  *    Delegate an authenticated request to specific request level, request level knows nothing of auth
  *    Certain request levels aren't available to public and only available to your app
*  Tests
  *    On consumer side, stub out tests, use vcr
*  Versioning
  *    Namespace entire api with number segment in url path

### REMEMBER    
*  Think in terms of services.
*  Vertical vs Horizontal
    *  Don't want to scale an entire stack
  
  
  