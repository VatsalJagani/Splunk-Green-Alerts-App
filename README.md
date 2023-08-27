# Splunk-Green-Alerts-App
Splunk App has utility to easily generate Green alert once after the issue is resolved. And also regenerate as long as issue is present.


## Download from Splunkbase
TODO


## Overview
The Green App is a Splunk App to provide utility to generate Green alert once after the issue is resolved. And also regenerate as long as issue is present.
Usually with Splunk alerts you create alert when there is issue with system which is very easy to do with Splunk but then you are requested to also create alert when that issue fixed, but you need to generate that only once after the issue is fixed. You could use this App in those scenario.

* Author - Vatsal Jagani
* Creates Index - False
* Compatible with:
    * OS: Platform Independent
    * Browser: Google Chrome, Mozilla Firefox, Safari



## What's inside the App

* No of Custom Commands: **1**
* No of Lookups - KVStore Collections: **2**



## Usage
The App has a command called `greenalert` which handles all the logic for generating the alert. By the nature its a streaming command for filtering. So it will filter the results for which it do not required to generate the alert.

### greenalert Command
Below is the details for the `greenalert` command.
* syntax = `greenalert (alertname)? (statusfield)? (groupbyfields)?`
* description = Generate alert when there is issue (Red alert) as well as also generates Green alert once after the issue has been fixed.

* alertname
    * syntax = `alertname=<string>`
    * description = The current alert name.
    * Is_Required: No
    * Default: If the alert name is not specified it can use the current alert name from the savedsearch being executed.
        * The parameter is required if the query is being executed from the search page directly.

* statusfield
    * syntax = `statusfield=<string>`
    * description = The status field name.
    * Is_Required: No
    * Default: `status`
        * If status field in your alert search result is other than status you could specify with this field.

* groupbyfields
    * syntax = `groupbyfields=<string>`
    * description = The group by field names to generate and think of alert per group. User can specify multiple fields comma separated.
    * Is_Required: No
    * Default: No group by fields.


#### Examples
* example1 = `| makeresults | eval system="Production-A", status="red" | append [| makeresults | eval system="Production-B", status="green"] | greenalert alertname="My Alert of System Down" statusfield="status" groupbyfields="system"`
    * comment1 = This Command generates the alert everytime the system is down and everytime the status is up again once after going down. User could generate alert specific to certain groups. For this example, if Production-A system is down you generate alert, but then when Production-A comes up again it generate alert once. And these alerts are tracked seperately to Production-B system.

* example2 = `| makeresults | eval status="red" | greenalert alertname="My Alert of System Down"`
    * comment2 = This Command generates the alert everytime the status is red and everytime the status is green but the last status was red.

* example3 = `| makeresults | eval status="red" | greenalert`
    * comment3 = The alertname option is not required as far as the alert is saved in the savedsearches.conf and not running the adhoc search.

* example4 = `| makeresults | eval system_up="red" | greenalert statusfield="system_up"`
    * comment4 = If the status field is different field name then you can specify with custom command option.

* example5 = `| makeresults | eval system="Production-A", status="red" | append [| makeresults | eval system="Production-B", status="green"] | greenalert groupbyfields="system"`
    * comment5 = User could generate alert specific to certain groups. For this example, if Production-A system is down you generate alert, but then when Production-A comes up again it generate alert once. And these alerts are tracked seperately to Production-B system.



## Installation & Configuration

### Topology and Setting Up Splunk Environment
* This App only needs to be installed on `Search Head` and there is no explicit configuration is required.
* For `Standalone` machine you need to install on that Splunk instance.

### Installation
* Install the App on the `Search Head` only.


### Dependencies
* There is no external Dependencies for this App.


### Configuration
* There is no explicit configuration is required for this App.

### Data Collection
* No data collection required for this App.


### Uninstall App
To uninstall the app, the users can follow the below steps:
* SSH or RDP to the Splunk instance
* Go to folder apps($SPLUNK_HOME/etc/apps).
* Remove the `green_alerts_app` folder from apps directory
* Restart Splunk



## Release Notes

#### Version 1.0.0 (Aug 2023)
* Created the first version of the App with custom command to achieve the 



## Open Source Components and Licenses
* Splunklib (Splunk SDK for Python)



## Contributors
* Vatsal Jagani


## Support & License
* Support - https://github.com/VatsalJagani/Splunk-Green-Alerts-App
* License Agreement - https://d38o4gzaohghws.cloudfront.net/static/misc/eula.html
