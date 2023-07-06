## Introduction
This collection of Axon code and Folio records includes all the components needed to replicate the active control hunting fault auto-correction algorithm presented here: https://doi.org/10.1016/j.buildenv.2022.108900

Axon and Folio are part of Haxall, an open source framework (https://haxall.io/),
however, some of the code in this package relies upon BACnet libraries and
functionalities that are only available in SkySpark (https://skyfoundry.com/product) which requires obtaining a paid license.


This framework adjusts the economizer outside air temperature lockout setpoint for an air handling unit, if the setpoint is accessible via BACnet. 

Components:
- Functions (`func`) are provided in individual text files that contain the source of each function. Function records, including the `func` and `dis` tags, must be created manually.
- Views (`view`) are provided in individual trio files that contain the entire `view` record, including the `src` and all other view record tags. They can be loaded and committed to Folio as new records.
- Templates (`template`) are provided in individual trio files that contain the entire `template` record, including the `tags` and all other template record tags. They can be loaded and committed to Folio as new records.
- Files (`file`) are provided containing reference data for the provided functions. Files can be manually added to the `proj/io` directory or uploaded via the Haxall or Skyspark UI.


outside and air and temp and disable and sp and equipRef->economizer