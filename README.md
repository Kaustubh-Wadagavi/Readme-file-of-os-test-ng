### OS-API-Tests: A TestNG based testing framework for OpenSpecimen.

### Description

This repository is used to test the OpenSpecimen app. It runs daily on the build server. For every module of OpenSpecimen, different directories are present in the resources of the test suite. Also, this contains different scripts. Each suite directory contains four files as follows:

|**File Name**       |           **Description**
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------
| config.json        |           It contains the server URL, Users, and DB JSON objects. (Check the "config.json Properties Table" for more information about 
|                    |           properties and their description)
| data.csv           |           This file contains the test cases.
| os_fresh.zip       |           The zip file contains the $os-fresh.sql file. In this file, the extra table's schema and test data available.
| suite.xml          |           This file contains the paths of required files to run the suite. 

### How to setup source-code?

      1. git clone https://bitbucket.org/krishagni/os-api-tests/
      2. gradle clean
      3. Import the directory into IDE as a Gradle Existing Project
      
### How to run?

1. Change directory to where the project is cloned on local. (cd $os-api-tests)
2. Make sure to fill the "$os-api-tests/src/test/resources/<$specific-directory>/config.json" file with appropriate values for every suite.(Check the "config.json Properties Table" for more information about properties and their description)
3. gradle clean
4. gradle test

**Note:**   The Gradle output report is generated in $os-api-tests/test-output/index.html 

### config.json Properties Table

|**Property Name**       |  **Description**
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------| 1. server url          |   OpenSpecimen's instance URL. (Which the framework would be testing)
| 2. users               |   OpenSpecimen user's login id and passwords. (This is used to authenticate when calling APIs)
| 3. db1                 |   Build server's MySQL configurations.(Note: Don't change these configurations)
| 4. db                  |   Local MySQL configurations. (Create same name database, password, and database user in local)
