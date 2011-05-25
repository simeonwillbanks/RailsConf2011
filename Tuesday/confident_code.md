Avdi Grimm (ShipRise LLC)

CONFIDENT CODE

Notes
  http://avdi.org/devblog/ for slides
  https://github.com/avdi/cowsay
  cowsay is simple unix util which transfers stdin to ascii art of cow
  SimpleDelegator Ruby Class
    Simple way to get decorators and delegation
  Try to eliminate conditionals for side concerns
  In software, lower complexity means fewer branches    
  
What is this talk about?
  Code Construction which is defined in Code Complete
    How to organize your methods!

Poor storytelling can be compared to poor code
  Tangents
  
Timid code
  Mix of input gathering, error handling, and biz logic jumbled together
  
Confident code
  Says exactly what it means without tangents 
  Consistent narrative structure like a well told story
  
The Narrative structure
  Good confident method will perform in this order
  1. Gather input
  2. Perform work
  3. Deliver Results
  4. Handling Failure
  
1. Gather Input
  Three strategies for dealing with uncertain input in a confident manner

2. Perform work
  Business logic of the method
  
3. Deliver Results

4. Handling Failure
  Put the expected first, and put the error handling at the end
    Handle errors from Biz Logic
  Use ruby idiom
    def foo; rescue; end;
    
    

  