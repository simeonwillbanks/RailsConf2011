Jim Weirich (EdgeCase LLC), Matt Yoho (EdgeCase)

@jimweirich
@mattyoho

NOTES
  Think of the entire system to think of holes
  Rails security mailing list, should subscribe
  

Security Lessons Learned From The Diaspora Launch
  http://www.kalzumeus.com/2010/09/22/security-lessons-learned-from-the-diaspora-launch/
  Read this article
  Patrick McKenize
  This is scary!
  
Rails does a good job of putting in right security measures by default

Problem with security
  Developers don't think about
  We don't spend time thinking about prohibiting actions
  We just think about providing features
  Hackers are crazy about figuring out ways around security
  
Breaches happen all the time!  
  Thoughtworks had malware on their website
    Took Uncle Bob's guys days to remove it
    
Reading homework
  http://guides.rubyonrails.org/security.html
  Abstract from larger OAuth paper
  
Basics of web application security
  Three pieces of app
    Browser
      In control of user and can send any request they desire
    Rails Server
      Can bypass this because above and beyond a web app talk
    Database
      User sneaks malicious info into DB
  Trust no one!!! Not one of these!

SQL Injection means hacker has total control of database
  UNION, DROP, CREATE, oh my
  Use prepared statements
  
Mass Assignment
  attr_accessible or attr_protected?
  Whitelisting or blacklisting?
  Whitelisting is always better!
  attr_accessible FTW
  Blacklist isn't convenience, its a security hole
  
Timing Attacks
  A Lesson In Timing Attack by Coda Hale
    http://codahale.com/a-lesson-in-timing-attacks/
  Based on statistical analysis
  Session key
    digest/md5 hash
    Want to guess this by passing in string with brute force
    Once we guess the first character of string, we see a change in response time
      This means we have the first character in the string
      With time, we can get the digest
  Don't use a comparison equality function
  Instead, use a cryptographically sound function that would not depend on the length of valid input
  
Detect social network authentication status
  Pull down image which is only visible by those logged into Facebook
  Send request and inspect response to see if the user is logged in
  
Cross site scripting
  document.write image into DOM with document.cookie
    Log bad URL to basic rails app on another server
  Problem arises from HTML inputted by user
  raw view helper is dangerous, do not use it
  Rails 3 uses h view helper which improves security by default
  If you want to provide markup
    Use a whitelist of html elements
    Don't try and correct malicious code, reject malicious tags
  Expect JavaScript in places you don't expect
  Use the Rails helper called Sanitize to whitelist 
  
Authentication != Authorization
  Authentication asks the question, "Who or what are you?"
  Authorization asks the question, "What are you allowed to do?" 
  Once a user is authenticated, don't assume they won't find there way to an action they aren't authorized to do
  Make sure a user is authorized to take an action, not just authenticated to your app
  Scope your searches to what is authorized!
  CanCan by Ryan Bates is a great authorization scheme
    https://github.com/ryanb/cancan
  
Cross Site Request Forgery
  Use image tag and logged in status to redirect to GET/POST destroy action
  Rails puts Authenticity Token into forms by default
  Hacker doesn't know Auth Token
  XSS still defeats Auth Token
  
Session Hacking
  Firesheep
  Require SSL!
    All requests must SSL for entire lifetime of session
  Secure Cookies!
    Cookie can only be transmitted over SSL or TLS
  New header field
    Strict-Transport-Security
      Tells browser that website won't work unless on SSL
      Can handle redirects instead of redirecting in app
  Rack::SSL
    Middleware which enforces SSL, Secure Cookies and redirection

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  