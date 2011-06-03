# Solving Performance Problems with Horizontal Scale. (The Worker Pattern)
## Ryan Smith (Heroku)
[Slides](https://s3.amazonaws.com/ryandotsmith/deck.pdf)   
[@ryandotsmith](http://twitter.com/ryandotsmith)  

# RELATED BLOGPOSTS
[The Worker Pattern](http://ryandotsmith.heroku.com/2011/04/the-worker-pattern.html)  
[Background Processing, Queues & Ruby on Rails](http://ryandotsmith.heroku.com/2011/03/ruby-queues.html)

### NOTES
* One thread per one request!
* Cache TTL and setTimeout milliseconds are both arbitrary
* Once they are ready, web sockets could be alternative
* Before enqueue job, write cache key with no-data, when enqueue, check for key with no-data
 
### SIMPLE ARCHITECTURE
* Version Zero
* See slide for architecture graph
* Fat controller
* Problems
  *   When we get a request, that is the users time
  *   We need to do whatever we can to respond to request as fast as possible
  *   Inefficient with space and time
  *   UX suffers!
    
### THE WORKER PATTERN
* Explicitly decouples the web request from the services required to respond to the request
* Attributes
  *   Thin requests
    *     In and out of controller as quickly as possible
*   Decoupled services
  *     All sorts of services
*   Increased complexity
  *     Simple solution isn't going to work
  *     When you need to performance, you won't necessarily find simplicity 
      
### IDEAL ARCHITECTURE
* See slide for architecture graph
* Decoupling
  *   Client asks server for data
  *   Server communicates with Memcache / Workers
* Need a bridge between decoupled entities
  *   Introduce Fragment object
  *   Tie front-end services with back-end services
    
### FRAGMENT
* Gap between front-end and back-end
* Controller doesn't worry about cache
* Cache is optimization on back-end
  
### WHAT DOES THIS BUY US?
* Parallel Execution
* Asynchronously build the page
* Horizontal Scale
  
### SIDE NOTE
* [Queue Classic](https://github.com/ryandotsmith/queue_classic)
  * Awesome Postgres Features
  * On speakers github profile
  * [How to use in Rails 3](https://github.com/ryandotsmith/queue_classic_example)
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  