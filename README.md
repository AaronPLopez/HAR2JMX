# HAR2JMX
## Version 0.1.0.0
### Date: 2025/01/22

-------------------------------

#### Description 
HAR2JMX is a utility for taking an HTTP Archive (HAR) file as input and transforming it into a Java Management Extensions (JMX) file for use in Apache JMeter. HAR2JMX also takes advantage of "transactional markers" in the recorded HAR file and automatically groups sets of requests into a transaction with JMeter. A sample HAR file is included with HAR2JMX which demonstrates the use of "transactional markers". Currently, HAR2JMX is only a command-line only utility. The tool is made available in the .NET 5.0 portable runtime for Windows (win-x64), Linux (linux-x64) and macOS (osx-x64).

### Download Latest Release
- [HAR2JMX Download](../../raw/refs/heads/main/binaries/latest/har2jmx_v0.1.0.0.zip)
  
### Download Latest Release

### CHANGELOG (most recent)
Build 0.1.0.0 (Prerelease)
1. Added the ability to convert the HAR file to an output of type CSV (comma separated values)
   Information on the HAR specification Timing properties can be found here: http://www.softwareishard.com/blog/har-12-spec/#timings
   The CSV output includes the Timing property values as columns for each request
2. Fixed an issue with JMX conversion where the Name in the HTTP Request element would be empty if the Path contained the value of "/server/rest/services"
3. JMX files created by HAR2JMX now list the JMeter version as 5.6.3 (this listing is mainly cosmetic)

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
    
Build 0.0.14.2 (Prerelease)
1. Fixed an issue where the parser, when variablizing the ArcGIS components in the Test Plan, might skip the portal webadaptor instance name (e.g. "portal" in "/portal/home")
2. Fixed an issue where the parser, when variablizing the ArcGIS components in the Test Plan, would treat "portal/sharing" as the name of the portal webadaptor instance instead of just "portal"
