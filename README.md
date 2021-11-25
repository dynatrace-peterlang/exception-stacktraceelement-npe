# Reproducer for BUG report to IBM Semeru JDK 11

IBM Semeru Runtime 11.0.13 throws an unexpected NullPointerException 
if calling `StackTraceElement.hashCode`. 

see https://github.com/eclipse-openj9/openj9/issues/13941

Simply run this demo app with `gradlew run` using a IBM Semeru Runtime 11.0.13.


```
PS C:\xxx> java -version
openjdk version "11.0.13" 2021-10-19
IBM Semeru Runtime Open Edition 11.0.13.0 (build 11.0.13+8)
Eclipse OpenJ9 VM 11.0.13.0 (build openj9-0.29.0, JRE 11 Windows 10 amd64-64-Bit Compressed References 20211022_218 (JIT enabled, AOT enabled)
OpenJ9   - e1e72c497
OMR      - 299b6a2d2
JCL      - 2d83aa3b76 based on jdk-11.0.13+8)
PS C:\xxx> .\gradlew run

> Task :app:run
java.vm.name:    "Eclipse OpenJ9 VM"
java.vm.vendor:  "Eclipse OpenJ9"
java.vm.version: "openj9-0.29.0"
java.version:    "11.0.13"
java.vendor:     "International Business Machines Corporation"

Unexpected NPE thrown in StackTraceElement.hashCode
java.lang.NullPointerException
        at java.base/java.lang.StackTraceElement.hashCode(StackTraceElement.java:278)
        at java.base/java.util.HashMap.hash(HashMap.java:340)
        at java.base/java.util.HashMap.get(HashMap.java:553)
        at com.dynatrace.App.main(App.java:32)

BUILD SUCCESSFUL in 2s
2 actionable tasks: 1 executed, 1 up-to-date
```
