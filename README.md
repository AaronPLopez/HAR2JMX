# HAR2JMX
## Version 0.0.14.2
### Date: 2023/12/08

-------------------------------

#### Description 
HAR2JMX is a utility for taking an HTTP Archive (HAR) file as input and transforming it into a Java Management Extensions (JMX) file for use in Apache JMeter. HAR2JMX also takes advantage of "transactional markers" in the recorded HAR file and automatically groups sets of requests into a transaction with JMeter. A sample HAR file is included with HAR2JMX which demonstrates the use of "transactional markers". Currently, HAR2JMX is only a command-line only utility. The tool is made available in the .NET 5.0 portable runtime for Windows (win-x64), Linux (linux-x64) and macOS (osx-x64).

### Download Latest Release
- [HAR2JMX win-x64 Download](../../raw/main/binaries/latest/win-x64/har2jmx_win-x64.zip)
- [HAR2JMX osx-x64 Download](../../raw/main/binaries/latest/osx-x64/har2jmx_osx-x64.zip)
- [HAR2JMX linux-x64 Download](../../raw/main/binaries/latest/linux-x64/har2jmx_linux-x64.zip)
  
### Download Latest Release

### CHANGELOG (most recent)
Build 0.0.14.2 (Prerelease)
1. Fixed an issue where the parser, when variablizing the ArcGIS components in the Test Plan, might skip the portal webadaptor instance name (e.g. "portal" in "/portal/home")
2. Fixed an issue where the parser, when variablizing the ArcGIS components in the Test Plan, would treat "portal/sharing" as the name of the portal webadaptor instance instead of just "portal"
