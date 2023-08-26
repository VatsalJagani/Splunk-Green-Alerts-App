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



## Usage
* TODO



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
------------
* Vatsal Jagani


## Support & License
* Support - https://github.com/VatsalJagani/Splunk-Green-Alerts-App
* License Agreement - https://d38o4gzaohghws.cloudfront.net/static/misc/eula.html
