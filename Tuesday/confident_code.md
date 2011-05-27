# Confident Code
## Avdi Grimm (ShipRise LLC)
[Slides](http://avdi.org/talks/confident-code-railsconf-2011/)  
[@avdi](http://twitter.com/avdi)

### WHAT IS THIS TALK ABOUT?
* Code Construction which is defined in Code Complete
  * How to organize your methods!
* Poor storytelling can be compared to poor code
  
### TIMID CODE
* Mix of input gathering, error handling, and biz logic jumbled together
  
### CONFIDENT CODE
* Says exactly what it means without tangents 
* Consistent narrative structure like a well told story
  
### THE NARRATIVE STRUCTURE
#### Good confident method will perform in this order
  1. Gather input
    * Three strategies for dealing with uncertain input in a confident manner  
      1. Coerce 
      2. Reject
      3. Ignore
  2. Perform work
    * Business logic of the method
  3. Deliver Results
  4. Handling Failure
    * Put the expected first, and put the error handling at the end
    * Only handle errors from Biz Logic
    * Use ruby idiom   
    `def foo; rescue; end;`
    
    
### NOTES
* https://github.com/avdi/cowsay
* cowsay is simple unix util which transfers stdin to ascii art of cow
* SimpleDelegator Ruby Class
  * Simple way to get decorators and delegation
* Try to eliminate conditionals for side concerns
* **In software, lower complexity means fewer branches**   


  