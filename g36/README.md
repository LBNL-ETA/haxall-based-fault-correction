## Introduction

This collection of Axon code and Folio records includes components needed to 
replicate the improved setpoint reset algorithm presented here:
https://doi.org/10.1016/j.buildenv.2022.108900

Axon and Folio are part of Haxall, an open source framework (https://haxall.io/),
however, some of the code in this package relies upon BACnet libraries and
functionalities that are only available in SkySpark (https://skyfoundry.com/product)
which requires obtaining a paid license.

This framework can work for several AHU-level setpoints, if they are accessible
via BACnet:
- Cooling supply air temperature setpoint
- Heating supply air temperature setpoint
- Supply air pressure setpoint

Components:
- Functions (`func`) are provided in individual text files that contain the source of
  each function. Function records, including the `func` and `dis` tags, must be
  created manually.
- Templates (`template`) are provided in individual trio files that contain the entire
  `template` record, including the `tags` and all other template record tags. They
  can be loaded and committed to Folio as new records.

Requirements for writing the setpoint to the BAS:
- Setpoint identified in each `resetSetting` record must be BACnet-writable

Tagging requirements for request generation:
```
- airTerminalUnit, equip
--- cool, pid, cmd - "Cooling PID Output", used for AHU cooling SAT setpoint
--- heat, valve, cmd - "Reheat Valve Command", used for AHU heating SAT setpoint
--- damper, cmd - "Damper Command", used for AHU supply air pressure setpoint
```

Requirements for ignored request functionality:
Zone requests for higher or lower AHU SAT can be ignored dynamically based on
the recent results of sparkRules.
In order for a specific `sparkRule` to be taken into consideration at the
zone-space or equip level, it must be configured with the following tag(s):
```
- suppressClgReq
- suppressHtgReq
```
