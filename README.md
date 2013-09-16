# ZeroMQ-Framework

This is the implementation of *Paolo Denti*'s and *Justin DeWind*'s ZeroMQ Universal Framework for iOS devices.

* <http://paolodenti.blog.com/2012/07/24/zeromq-ios/>
* <http://spin.atomicobject.com/2011/12/13/building-a-universal-framework-for-ios/>

I haven't done anything all that exciting; I followed directions and solved a discrepancy.<br/>
All kudos go to the above authors.

Compiled with: Xcode 4.6.3, for MacOSX 10.8 and zeromq-3.2.3 source files.

Usage of the Framework is Paolo's Step 5, but I ***do*** have an errata!

## Write a iOS client using the new øMQ framework

* just create a normal ios project
* drag the `ZeroMQ-iOS.framework` folder in the `Frameworks` group (check the copy checkbox)
* click on the project, build settings, add `-lstdc++` to “Other Linker Flags” (the C++ standard library is needed by zeromq)
* add the framework headers (just add `$(SRCROOT)/zeromq-ios.framework/Headers`) to the “Header Search Path” compiler directive
* just use normally zeromq in your application (the only note about is that you should `#include ”zmq.h”` instead of `#include <zmq.h>`)

***NOTE:** The “C++ Standard Library” setting in the Xcode project determines the “Other Linker Flags” that you must include. If `libc++ (LLVM C++ standard library with C++11 support` is specified, then the flag must be `-lc++` instead of `-lstdc++`.

## Recompilation

From Justin's blog: files that need to be public in the framework should be added in the: Build Phase for the target Aggregate: ZeroMQ-iOS: Copy Files.
Justin also warns (which I encountered), *"Ensure that the header files are copied into place* [at compile time] *(XCode is known to mess this up on occasion)"*.
