# ZeroMQ-Framework

This is the implementation of *Paolo Denti*'s and *Justin DeWind*'s ZeroMQ Universal Framework for iOS devices.

* <http://paolodenti.blog.com/2012/07/24/zeromq-ios/>
* <http://spin.atomicobject.com/2011/12/13/building-a-universal-framework-for-ios/>

I haven't done anything all that exciting; I followed directions and solved a discrepancy.<br/>
All kudos go to the above authors.

Usage of the Framework is Paolo's Step 5, but I ***do*** have an errata!

## Paolo's Step 5) write a ios client using the brand new zeromq framework

* just create a normal ios project
* drag the ”zeromq-ios.framework” folder in the “Frameworks” group (check the copy checkbox)
* click on the project, build settings, add “-lstdc++” to “Other Linker Flags” (the C++ standard library is needed by zeromq)
* add the framework headers (just add “$(SRCROOT)/zeromq-ios.framework/Headers”) to the “Header Search Path”compiler directive
* just use normally zeromq in your application (the only note about  is that you should #include ”zmq.h” instead of #include <zmq.h>)

***NOTE:** The *C++ Standard Library* setting in the Xcode project determines the *Other Linker Flags" that you must include<br/>
If `libc++ (LLVM C++ standard library with C++11 support` is specified, then the flag must be `-lc++` instead of `-lstdc++`.
