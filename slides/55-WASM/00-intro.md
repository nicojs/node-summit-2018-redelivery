# NodeJS and N-API

---
### Talk by
- Jay Phelps, ThisDOT
- Node Summit 2018 – WEBASSEMBLY DEMYSTIFIED: WHAT IT MEANS FOR NODE.JS 
- https://vimeo.com/287730898

---
### What is WASM
- efficient low level bytecode (for the web)
- fast to send over the internet, fast to compile and parse 
- streaming compilation in browsers
    - .wasm -> compile to machine code stream
    - compile is faster then downloading the code
<img src="./img/wasmstream.gif"/>

---
### Efficient
- Efficient, low level bytecode (instructions are bytes, binary thing)
- mostly not written by hand, but as a compile target
---
<!-- .slide: data-background="url('/img/demo.jpg')" data-background-size="cover" --> 
<!-- .slide: class="lab" -->
## Demo time!
The problem and the solution

---
### Current Status
- exited experimental March 14, 2018
- back ported to 6.x and 8.x

---
### How do i use N-API
- C based API built in NodeJS
    - `#include <node_api.h>`

Examples:  
https://github.com/nodejs/node/tree/master/test/addons-napi

---
<!-- .slide: data-background="url('/img/demo.jpg')" data-background-size="cover" --> 
<!-- .slide: class="lab" -->
## Demo time!
N-API Hello World

---
### What about NAN?
- C++ Addon technology
- Needed a new approach
- Nan is limited in isolation, still using underlying v8 types
- node-addon-api is successor for NAN
    
---
### What is node-addon-api?
- header only wrapper
    - inline only
    - Compiled into module
    - Depends only on exported N-API functions
- Delivered as npm module
- Provides a C++ object model
- Easy transition from NAN
- Makes writing addons more easy
- install addon node-addon-api
    - `#include <napi.h>`

Examples:
https://github.com/nodejs/node-addon-examples 

---
<!-- .slide: data-background="url('/img/demo.jpg')" data-background-size="cover" --> 
<!-- .slide: class="lab" -->
## Demo time!
Node-addon-api Hello World

---
### Advanced concepts
Object Wrap
- ties JS object lifetime to C++ object instance
Steps
- extend ObjectWrap
- define class
- return constructor
- create an instance/use from JS

Example: 
https://github.com/nodejs/node-addon-examples/tree/master/6_object_wrap/node-addon-api


---
### Advanced concepts
AsyncWorker
- Create an instance and call Queue method
- execute work in background thread
    - no N-api code in execute
    - set state on this
- OnOk and OnError called upon completion on main thread
    - return value from here


Example: 
https://github.com/nodejs/node-addon-examples/blob/4dc85d816e6a1ef641be416b5397e1813960b403/async_pi_estimate/node-addon-api/async.cc

---
### Conversion NAN to node-addon-api
- install node-addon-api
- tools folder has conversion.js
- 80% complete...
- changes code in place, so backup


---
### Call for action
- Get involved
    - documentation
    - testing
    - issue triage
    - porting modules




