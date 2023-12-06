# HAR2JMX
## Version 0.0.15.0
### Date: 2023/12/06

-------------------------------

#### Description 
HAR2JMX is a utility for taking an HTTP Archive (HAR) file as input and transforming it into a Java Management Extensions (JMX) file for use in Apache JMeter. HAR2JMX also takes advantage of "transactional markers" in the recorded HAR file and automatically groups sets of requests into a transaction with JMeter. A sample HAR file is included with HAR2JMX which demonstrates the use of "transactional markers". Currently, HAR2JMX is only a command-line only utility. The tool is made available in the .NET 5.0 portable runtime for Windows (win-x64), Linux (linux-x64) and macOS (osx-x64).

### Download Latest Release
- [HAR2JMX win-x64 Download](../../raw/main/binaries/latest/win-x64/har2jmx_win-x64.zip)
- [HAR2JMX osx-x64 Download](../../raw/main/binaries/latest/osx-x64/har2jmx_osx-x64.zip)
- [HAR2JMX osx-arm64 Download](../../raw/main/binaries/latest/osx-arm64/har2jmx_osx-arm64.zip)
- [HAR2JMX linux-x64 Download](../../raw/main/binaries/latest/linux-x64/har2jmx_linux-x64.zip)
  
### Download Latest Release

### CHANGELOG (most recent)
Build 0.0.15.0 (Prerelease)
1. Moved HAR2JMX to .NET8
2. Added an option (-shm true) to add a "simplified" HTTP Header Manager element to the Test Plan, instead of an HTTP Header Manager to every request; the simplified element is not variablized and contains pre-canned values; this element is added directly under the Test Plan element
3. Added improved support to better handle an "inserted transaction marker" into the har file
4. Moved the "View Results Tree" element from Thread Group to be directly under the Test Plan
5. Added a Response Assertion element that fails any request with the word "error" in its response; by default, this element is not enabled
6. Added an option (-udv true) to add a dedicated User Defined Variables element to the Test Plan, instead of putting detected variables in the Test Plan element
7. Added a HTTP Request Defaults element to the Test Plan
8. Several useful static variables the both "User Defined Variables" sections (whichever is enabled); these variables (e.g., ${testPlanName}, ${requestConnectTimeout}, ${requestResponseTimeout}) are referenced and utilized in the HTTP Request Defaults element
9. Added an option (-ps true) to toggle the "Generate Parent Sample" option per transaction; default is true
10. In addition to osx-x64, binaries are built for osx-arm64
