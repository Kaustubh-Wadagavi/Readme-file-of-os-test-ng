### OS-API-Tests: A TestNG based testing framework for OpenSpecimen.

### Description

This repository is used to test the OpenSpecimen app. It runs daily on the build server. For every module of OpenSpecimen, different directories are present in the resources of the test suite. Also, this contains different scripts. Each suite directory contains four files as follows:

|**File Name**       |           **Description**
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------
| 1. config.json     |           It contains the server URL, Users, and DB JSON objects. (Check the "config.json Properties Table" for more information)
| 2. data.csv        |           This file contains the test cases.
| 3. os_fresh.zip    |           The zip file contains the $os-fresh.sql file. In this file, the extra table's schema and test data available.
| 4. suite.xml       |           This file contains the paths of required files to run the suite. (Check the "suite.xml Properties Table" for more information)

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
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------
| 1. server url          |   OpenSpecimen's instance URL. (Which the framework would be testing)
| 2. users               |   OpenSpecimen user's login id and passwords. (This is used to authenticate when calling APIs)
| 3. db1                 |   Build server's MySQL configurations.(Note: Don't change these configurations)
| 4. db                  |   Local MySQL configurations. (Create same name database, password, and database user in local)

### suite.xml Properties Table

|**Property Name**   |  **Description**
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------
| 1. schemaDump      |   Path to schema dump(schema.sql) file.(Check the how to create the schema.sql and os-tables.csv files for more info)
| 2. dataDump        |   Path to os-fresh.zip(extra-tables schema and data dump) file of specific suite. (Check how to create the os_fresh.zip)
| 3. configFile      |   Path to config.json file. (For more information check the confi.json properties table)
| 4. testFile        |   Path to test data file. (data.csv)

### How to create the schema.sql and os-tables.csv 

1. Before running the below script make sure the OpenSpecimen clean server is up.
2. Open the Create-clean-and-tables-csv.sh file. Configure the database properties and file paths.
3. Run using the below command:
        ./Create-clean-schema-and-tables-csv.sh
        
**Note**

A. The above script creates the schema.sql file and os-tables.csv file from latest build.
B. Make sure after running the script schema.sql file moved to $os-api-tests/src/test/resources directory. (This is the schemaDump file. It is common schema file which is used for all suites commonly)

### How to create the os_fresh.zip file

1. After creating the test data using user interface in the OpenSpecimen.
2. Open the Create-extra-tables-schema-and-data-dump.sh file and configure the database properties and file paths and names.
3. Run using the following command: ./Create-extra-tables-schema-and-data-dump.sh

**Note**

1. The above script creates the TC-Specific-Dump zip file(It contain the whole dump of specific suites) and os_fresh.zip file.
2. After creating both zips. Move the Tc-Specific-Dump zip file to $os-api-tests/Tc-Specific-Dumps folder and move os_fresh.zip file to specific suites)
3. The os_fresh.zip file contains the os_fresh.sql. This file contains the OpenSpecimen extra tables schema and test data.

