### OS-API-Tests: A TestNG based testing framework for OpenSpecimen.

### Description

This repository is used to test the OpenSpecimen app. It runs daily on the build server. For every module of OpenSpecimen, different directories are present in the resources of the test suite. Also, this contains different scripts. Each suite directory contains four files as follows:

|**File Name**       |           **Description**
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------
| config.json        |           It contains the server URL, Users, and DB JSON objects. (Check the "config.json Properties Table" for more information about 
|                    |           properties and their description)
| data.csv           |           This file contains the test cases.
| os_fresh.zip       |           The zip file contains the $os-fresh.sql file. In this file, the extra table's schema and test data available.
| suite.xml          |           This file contains the paths of required files to run the suite. 

### How to setup source-code?

      1. git clone https://bitbucket.org/krishagni/os-api-tests/
      2. gradle clean
      3. Import the directory into IDE as a Gradle Existing Project
      
