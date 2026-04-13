# HAR2JMX
## Version 0.2.0.0
### Date: 2026/04/13

-------------------------------

#### Description 
HAR2JMX is a utility for taking an HTTP Archive (HAR) file as input and transforming it into a Java Management Extensions (JMX) file for use in Apache JMeter. HAR2JMX also takes advantage of "transactional markers" in the recorded HAR file and automatically groups sets of requests into a transaction with JMeter. A sample HAR file is included with HAR2JMX which demonstrates the use of "transactional markers". Currently, HAR2JMX is only a command-line only utility. The tool is made available in the .NET 5.0 portable runtime for Windows (win-x64), Linux (linux-x64) and macOS (osx-x64).

### Download Latest Release
- [HAR2JMX Download](../../raw/refs/heads/main/binaries/latest/har2jmx_v0.2.0.0.zip)

### Usage
    HAR2JMX
    Version: 0.2.0.0

    Usage:
    har2jmx.CLI.exe -i "C:\folder\myworkflow.har"

    Universal Options...
    -i   ==> [String] The full file system path to the HAR file (required); generated JMX file is derived from HAR file
    -o   ==> [String] The output type to convert HAR file to (default is JMX, other options are CSV or TSV)
    -v   ==> [Boolean] Create variables from server, port, instance, service and token request values (default is false...for JMX output only)
    -c   ==> [Boolean] Append an incrementing numerical number after each request (default is true...for JMX output only)
    -shm   ==> [Boolean] Add a single, simplified HTTP Header Manager element to the Test Plan, instead of per request (default is false...for JMX output only)
    -udv   ==> [Boolean] Add a dedicated User Defined Variable element to the Test Plan, instead of using the Test Plan section (default is false...for JMX output only)
    -ps   ==> [Boolean] Toggle the Generate Parent Sample per transaction (default is true...for JMX output only)
    -h2   ==> [Boolean] Generate transactions and request samplers using bzm HTTP2 instead of HTTP1.1 (default is false...for JMX output only)

### CHANGELOG (most recent)
Build 0.2.0.0 (Prerelease)
1. Added the ability to convert the HAR traffic to bzm HTTP2 Transaction Controllers and HTTP2 Samplers via the "-h2 true" switch; by default, Transaction Controllers and HTTP Samplers will be 1.1; this option will require Apache JMeter to at least have the bzm-http2 2.0.6 plugin
2. Add the ability for HAR2JMX to variablize historicMoment, sessionId, gdbVersion and gdbGuid variables
3. Expanded the simplified HTTP Header Manager element to include zstd (Zstandard compression algorithm) in the Accept-Encoding header;  gzip, deflate, br, zstd are now the requested options
4. Added the "tsv" option to the -o parameter for writing the output as a tab seperated value file
5. For tab seperated value outputs, a Layer and Geometry column have been added; this is to assist ArcGIS based request signatures:
   The rows for the Layer column will be populated with the "layer number" if the request is an ArcGIS feature service layer query; 
   The rows for the Geometry column will be populated if a request contains a "geometry" key in either the GET QueryStrings parameters or the POST PostParams parameters (a geometry key/value pair is often found with ArcGIS feature service layer query requests); the geometry value is typically in json format
6. For CSV and TSV outputs, the RequestCount column has been renamed to RequestCounter, to improve clarity
7. Moved HAR2JMX to .NET10

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
