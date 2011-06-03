# Event Machine 
## Birds of a Feather (BoF) Session
[Website](http://emrubyconf.com/)  
[Dr Nic](http://twitter.com/drnic)  

### TALKS
#### Lessons in Concurrency: Threading vs Evented
#### Introduction to EventMachine
#### EventMachine and Testing
#### Threads, Fibers, EventMachine and Actors in Ruby
#### EventMachine Tutorial

[Aman Gupta](http://twitter.com/tmm1)  
[Nick Quaranto](http://twitter.com/qrush)  
[Mike Perham](http://twitter.com/tmm1)  
Lots of others...

### EVENTMACHINE THE SPEED DEMON
[Aman Gupta](http://twitter.com/tmm1)  
[Slides](http://scr.bi/em-railsconf)  

#### Talk
* Every EM app has EM.run
* `EM.stop` must be called to get to the rest of code in program
* Reactor responds to events
  *   Reactor is a while loop
    *     If you do anything slow, you block the loop from completing
    *     This means other events will be backed up
    *     Must make sure you don't call big blocking processes within reactor loop
      *       `Net::HTTP`
      *       `sleep`
      *       `while`
* Once you give control to reactor, everything happens with callbacks
* When you use callbacks, everything becomes async and operation takes a block and passes value into block
  *   When value is available, we can invoke this block 
* When writing async code, code won't happen linearly
  *   Code can get messy very quickly
  *   Your code gets nested, further, and further 
* When you try to make code async, you end up with lots of spaghetti code
* Async does get you concurrency
  *   Even though you have single thread, the thread can handle 1000s of connections in the same process without threads
* TCP is a stream
  *  Guarantees data will show up in same order but won't show up as same chunks
  *  Based on protocol you are implementing, you have to buffer data and pull out data and make sense of it
  *  Example uses text so using \n char as identifier
  *  This problem depends on protocol you are implementing
* Business logic is a state machine!
* `EM::Queue.new`
  *   Async
  *   pop
    *     whenever item is available run the passed block
  *   Have to use queue to we aren't executing parts of program at the same time
  *   Use EM.system so we don't block
  *   Not really recursive because telling EM to sometime in the future invoke this block 
* `EM::PeriodicTimeer`
  *   Also a regular timer
  *   Just a timer!
* Twitter integration use em-http
  *   Have to use gems prefixed with 'em'
  *   yajl is very async friendly
  
#### Summary
* Single threaded so only one thing can happen at a time, but all operations are quick, so pass block, and it will eventually be invoked
* Be extra careful to not block reactor loop
* EM is all about concurrency
  *   EM is all about I/O concurrency
    *     Deal with multiple network connections
    *     Great for I/O bound problems
* EM is great for building web services!!!
* Watch files, watch summaries, tons of gems
* EM is optimized for production use case
* Gearing up for 1.0 and will be production ready
* Look at mountain west presentation
* Look on wiki protocols page for list of EM aware/async capable gems
* Nicer documentation is coming soon! Go and help!!!
  
### EVENTMACHINE AND TESTING
**Nick Quaranto**
  
***EM does timing really well, and we need to test it!***

***Testing async code sucks***

#### Testing EM
* Write some test! 
* `em-hiredis`
  *   should be used for redis with EM
  *   didn't have tests
* `em-synchrony` is bad because monkey patches code be synchronous
* `em-spec`
  *   Gives you EM method which you can use in tests and pass it a block
  *   You have to stop EM for tests to be useful, do this by calling done
    *     You must remember to call done!
*` em-http-request` + `webmock`
  *   Must be 0.3.0
  *   Not a great solution
  *   Maybe do higher level integration testing
* Use `EventMachine::Channel` all over the place
  *   Stopping the reactor loop is the hardest part of testing!
  *   We can listen for certain events and we can stop
  *   Channel can have events pushed on to it, and register a callback for when a message is sent, callback emits message
* Don't put code inline in EM loops, just call class methods
  *   Then you can class methods separately
* Aman's testing strategy
  *   One
    *     Start reactor
    *     Assert a bunch of tests
    *     Stop the reactor
  *   Two
    *     Don't use the reactor at all
    *     Just directly test the callbacks
    *     If state machines are decoupled from the reactor, you can test them separately
    
**Divide between Ruby and EventMachine is terrible, Aman you should fix this!**  
  
  
### THREADS, FIBERS, EVENTMACHINE AND ACTORS IN RUBY
**Mike Perham**
[http://www.mikeperham.com](http://www.mikeperham.com)
[Talk Video](http://twitter.com/mperham/status/71255889788669952)

#### SMALLEST FASTEST SYSTEMS ARE EVENT BASED
* nginx
* memcached
* Node.js
  
#### ASYNCHRONICITY MAKES EVENTMACHINE HARD, USE FIBERS TO HELP!
* Fibers aren't standard Ruby :(
  
#### WHAT ABOUT THREADS?
* Some systems scale really well with threads
* 1.8 threads weren't parallel 
* 1.9 threads still suffer from global interpreter 
* jRuby are truly concurrent
* Rubinus are at same level as 1.9 but will be better in hydra
  *   get rid of global interper lock
  
#### ACTORS
* Get concurrency by passing messages
  
  

*...OOOpppsss, I left earlier to catch another session*
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  