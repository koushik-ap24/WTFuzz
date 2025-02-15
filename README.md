# WTFuzz
Mutation Based Binary Fuzzer

#### Fuzzer capabilities

WTFuzz currently supports the following file types:

* Plaintext  
* JSON  
* CSV  
* JPEG  
* XML

Once the binary crashes, the program output and error messages are fed to the result generator, which summarises the program behaviour for the user via stdout and writes the successful payload to the appropriate text file for analysis. The summary provides the crash type, detected vulnerability, crash cause, and payload size.

The fuzzer also supports multithreading via 4 threads.

### **Bugs Identified by the Fuzzer**

Our fuzzer is capable of finding:

* Buffer overflows (with/without stack canary)  
* Format strings via memory leaks, and  
* Integer/arithmetic errors
