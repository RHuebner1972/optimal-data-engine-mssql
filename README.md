# Optimal Data Engine (ODE) Build 20151020 #
Copyright 2015 OptimalBI - Licensed under the GNU GENERAL PUBLIC LICENSE Version 3.0 (GPL-3.0)

## The Approach: ##
Good architecture is modular, separating concerns across its components. This helps ensure each component does one job well, which in turn helps the components work together, delivering a valuable experience to users. Modular architecture is also easier to maintain.
A useful data warehouse does not attempt to take data directly from source systems to end-users in one hit, instead it uses modular components we call data layers. While these modular components have many specific names (eg “staging”, “foundation”, “presentation”) what ties them together is their layered nature: each one does a single job well, before passing data on to another layer.
Many of the ideological battles of the past (eg Inmon vs Kimball) were founded on an assumption that one methodology must rule them all. As soon as we think about a data warehouse in terms of layers, we are free to choose the optimal methodology for the job each layer is doing.

## What Optimal Data Engine (ODE) does: ##
Using the Data Vault methodology, ODE breaks each complex part of your data processing into layers to make it easier and faster to manage and implement. It's a true agile methodology for building a Data Warehouse. ODE breaks the complexity into layers - to find out more visit http://www.ode.ninja/data-layers/

## Requirements (All users): ##
* Access to a running Microsoft SQL Server (for example, Express Edition)
* SQL Server Management Studio installed on a computer which you can access
* Administrative rights to be able to create databases
* Visual Studio 2015 Community Edition installed on a computer which you can access. This can be downloaded from https://www.visualstudio.com/en-us/mt171547.aspx

## Download and build instructions: ##

### Pre-requisites ###

* Download a copy of the zip and extract to a temporary folder
* Create Database for ODE, default name is ODE_Config

### Scripted Install ###

* Open SQL Server Management studio and load ODV_Config_create.sql from the extracted zip file
* Within SQL Server Management Studio > Click Query Menu > SQLCMD Mode 
* Within the script optionally change the DatabaseName and DefaultFilePrefix in the code to the correct database name, default is 'ODE_Config'
* Click Execute from the toolbar, this should run with a result of 'Command Completely Successfully'
* Validate the script has executed correctly by checking the last populated table; log4.JournalControl - this should contain 13 records.

### Manual Install ###

* Connect SQL Server Management Studio to the SQL Server instance where you want to install ODE.
* Download the Optimal Data Engine code from GitHub, into a directory e.g. "C:\Git\OptimalDataEngine\"
* Using Visual Studio, create a SQL Server Database Project, for example "ODE_Config"
* In Visual Studio solution explorer right click on project, select 'Import' > 'Script' > 'Select File' > 'Multiple Files' > Browse > Browse to code location (e.g. "C:\Git\OptimalDataEngine\") and select folder > Click Finish
* Right click project > Properties > Database Settings > Miscellaneous Tab
* Tick Trustworthy
* Change 'Service broker options' to 'EnableBroker'
* Click OK
* If you already have a login on your SQL Server instance called 'SBLogin': Find SBLogin.sql in Solution Explorer under Security > SBLogin.sql, right-click it and 'Exclude from project'. 
* Right click Project > Add > Database Reference > System Database > Master > OK 
* Save project
* Right click Project > Build
* Right click Project > Publish
* Specify Database Name
* Click Edit for 'Target database connection' and enter the connection string for your SQL Server instance
* Click Publish
* Expand Scripts in Project Explorer > Click ScriptsIgnoredOnImport.sql > Copy this script into a new SQL Management Studio window and connect to your published database > Execute script

## Current functionality: ##
Details of the current functionality can be found here http://www.ode.ninja/category/features/

## Notes ##
* Untested on SQL Server editions prior to 2014
* This product is still in Beta and should not be deployed to a production environment without thorough testing by you to ensure no adverse effects on your environment

## Feedback, suggestions, bugs, contributions: ##
Please submit these to GitHub issue tracking or join us in developing by forking the project and then making a pull request!

## Find out more: ##
Visit http://www.ode.ninja/ - this is where we keep our guides and share our knowledge. To find out more about OptimalBI and the work we do visit http://www.optimalbi.com or check out our blogs at http://optimalbi.com/blog/tag/data-vault/ for all the latest on our Data Vault journey. If you want to get in touch, you can email us at hey@optimalbi.com

## Change log: ##
```
Build 20151020
	* Automated Install Script.
	* Added new schema (dv_config) which holds helper scripts to populate some configuration tables.

Build 20150928
	* Initial Build.

```
