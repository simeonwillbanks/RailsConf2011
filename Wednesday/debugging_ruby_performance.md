Rails Performance Tools
Aman Gupta (GitHub)

http://speakerdeck.com/u/tmm1/p/debugging-ruby-performance

@tmm1

NOTES
  None of these tools require recompiling
  Tools make debugging easer!
    When app has performance problems, use these tools to understand what is going on
  You have to gather data in order to make sense of a problem
  More data you get, the more insight you get

Rails Performance Tools For
  Linux 
  C
  Networks
  Memory Usage
    How will app scale
    
Twelve Tools!
Get sense of each tool, so you can use the tool for specific problem later

1. LSOF
  Good way to start because snapshot in time
  List open files from process ID (pid)
  Outputs ton of information on process
    File descriptor table
      1,2,3 standard in and outs
      
2. TCPDUMP
  Dump traffic on a network
  Once you know which connections are open, you can get more info on connection
  Boils down to expressions such ask getting all HTTP requests coming thru port 80
  Write data to dumpfile (prod, staging, etc) and load file into Wireshark locally
  
3. STRACE
  Useful for kernal level code
  Has summary and trace mode
  Trace system calls (calls in the kernal)
    Functions which are defined in the kernal
    OS is defined into user and kernal space
    Ruby is executed in user space
    When ruby executes system call, its executed in kernal space
  First argument to read/write is a file descriptor
  strace ruby requires very low overhead, so can be done in production
  Ruby 1.8 emulates threads using green threading library
    Ever ten milliseconds, switch threads
  
4. LTRACE  
  Useful for C level code
  Has summary and trace mode

5. RBTRACE
  Trace ruby methods inspired by strace
  require 'rbtrace'
    Does nothing by default
    Must call from command line and give pid
  Can give it method selectors which will show method calls in real time
  Has built-in tracers for all kinds of libraries like activerecord, eventmachine
    Will trace commonly used functions in each library
    
6. PERFTOOLS
  Googles performance tool
  Huge set, but we will talk about CPU profiling
  Coolest thing is call graph output
    Really intuitive way to understand where you application is spending time
  Sampling profiler so you can decide what the size of overhead you'll incur

7. PERFTOOLS.RB  
  perftools for ruby code
  Wrapper around perftools which makes it Ruby aware
  Sleep kernal knows to leave alone
  Fib is CPU intensive
  Run profiler in two different modes
    CPU
    Real Time
      Takes walk clock time into account
      Will see that sleep is most expensive
  See what is CPU intensive?
    Template rendering or PDF writing
  See what is I/O or sleep intensive?
    Slow DB or web service
  Once you find a hotspot
    Micro-optimization is worth it
  
8. RACK-PERFTOOLS
  Insert into rack app
  Can request url, add parameter, respond with call graph instead of source
  Make sure all requests go to single process in unicorn
  Kinda iffy because not secure but not intensive
  
9. GDB
  GNU debugger
  Super useful for figuring out Ruby Segfaults
  Two ways to use it:
    1. Attach to a running process via pid
    2. Coredump
      Dump out memory contents whenever an error occurs
      Load this into GDB
      
10. GDB.RB
  Makes GDB Ruby aware
  eval
    load in ruby 
  get lists of objects
  dive into objects
  threads
  classes
    dump out all classes by classname
    
11. MEMPROF
  Ruby has many issues around memory and objects and gc
  Memprof.track
    Summarizes all objects which are created for passed block
  Memprof.dump
    Instead of summary, it gives you details via json which details about object
  Memprof.dumpall
    Simpler to dump but tons and tons of json (10MBS or more)
    Use CouchDB to parse
    memprof.com has GUI for large json files
      
12. HOTSPOTS
  Related to Memprof
  Middleware for every single request
    Dumps out statistics for each request like mem, SQL, objects
  Graphical view into all this data!
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  