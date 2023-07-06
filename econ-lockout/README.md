## Introduction
This collection of Axon code and Folio records includes all the components needed to replicate the active control hunting fault auto-correction algorithm presented here: https://doi.org/10.1016/j.buildenv.2022.108900

Axon and Folio are part of Haxall, an open source framework (https://haxall.io/),
however, some of the code in this package relies upon BACnet libraries and
functionalities that are only available in SkySpark (https://skyfoundry.com/product) which requires obtaining a paid license.


This framework adjusts the economizer outside air temperature lockout setpoint for an air handling unit (AHU), if the setpoint is accessible via BACnet. 
  

Components:
- Functions (`func`) are provided in individual text files that contain the source of each function. Function records, including the `func` and `dis` tags, must be created manually.
- Views (`view`) are provided in individual trio files that contain the entire `view` record, including the `src` and all other view record tags. They can be loaded and committed to Folio as new records.
- Files (`file`) are provided containing reference data for the provided functions. Files can be manually added to the `proj/projName/io` directory or uploaded via the Haxall or Skyspark UI.

  

This framework identifies the ASHRAE Climate Region in which the AHU resides by extracting the zip code from the AHU's `siteRef->geoAddr` and performing a lookup from the file `FIPS_v4.csv`. This file was created by combining the following data sources:
1. Climate Zone and FIPS data from https://gist.github.com/philngo/d3e251040569dba67942  
2. FIPS and Zip Code data from https://www.kaggle.com/datasets/danofer/zipcodes-county-fips-crosswalk 
3. Economizer Lockout Setpoints per ASHRAE 90.1 from https://tayloreng.egnyte.com/dl/mN0c9t4WSO/ASHRAE_Journal_-_Economizer_High_Limit_Devices_and_Why_Enthalpy_Economizers_Dont_Work.pdf
  


Tagging requirements for Economizer Lockout Setpoint:
```
outside, air, temp, disable, sp, equipRef->economizer, cur, bacnetConnRef, bacnetCur
```