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

### **Bugs Identified by the Fuzzer**

Our fuzzer is capable of finding:

* Buffer overflows (with/without stack canary)  
* Format strings via memory leaks, and  
* Integer/arithmetic errors

#### Multi-Threading

The implementation of multi-threading for the fuzzer has significantly reduced the time taken to detect vulnerabilities compared to using a single thread. We use 4 threads that initially start with the example input with each then randomly choosing their mutation method. If we don’t detect a crash/vulnerability we base further rounds on the payload which gave the most coverage previously.

These rounds are based on an 8-second timeout such that we assume if a vulnerability is not detected we’re likely exploring an incorrect branch without a vulnerability so we reset the payload and start again. To this end, if after 60 seconds no vulnerability has been found it is automatically skipped and the next binary in the queue is fuzzed.
