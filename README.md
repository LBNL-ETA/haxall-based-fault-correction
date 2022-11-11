## Haxall-based (Axon) fault auto-correction package for building HVAC system 

## Copyright

Haxall-based (Axon) fault auto-correction package for building HVAC
system (Haxall-based Fault Correction) Copyright (c) 2022, The
Regents of the University of California, through Lawrence Berkeley
National Laboratory (subject to receipt of any required approvals
from the U.S. Dept. of Energy) and kW Engineering. All rights reserved.

If you have questions about your rights to use or distribute this software,
please contact Berkeley Lab's Intellectual Property Office at
IPO@lbl.gov.

NOTICE.  This Software was developed under funding from the U.S. Department
of Energy and the U.S. Government consequently retains certain rights.  As
such, the U.S. Government has been granted for itself and others acting on
its behalf a paid-up, nonexclusive, irrevocable, worldwide license in the
Software to reproduce, distribute copies to the public, prepare derivative 
works, and perform publicly and display publicly, and to permit others to do so.

## License

This repository is under the following [license](https://github.com/LBNL-ETA/haxall-based-fault-correction/blob/main/License.txt).

## Introduction

This collection of Axon code and Folio records includes all the components needed to 
replicate the active control hunting fault auto-correction algorithm presented here:
https://doi.org/10.1016/j.buildenv.2022.108900

Axon and Folio are part of Haxall, an open source framework (https://haxall.io/),
however, some of the code in this package relies upon BACnet libraries and
functionalities that are only available in SkySpark (https://skyfoundry.com/product)
which requires obtaining a paid license.

This framework for active auto-correction of hunting faults was written for and
tested with the Automated Logic and Johnson Controls building management systems,
using BACnet. The calculation of PI control loop parameters is specific to the
implementation of the PID algorithm in each control system, and needs to be
modified accordingly.

This framework was written for reheat valve control loops, and works best with
those that use discharge air temperature sensors as the process variable. 

Components:
- Functions (`func`) are provided in individual text files that contain the source of
  each function. Function records, including the `func` and `dis` tags, must be
  created manually.
- Views (`view`) are provided in individual trio files that contain the entire `view`
  record, including the `src` and all other view record tags. They can be loaded
  and committed to Folio as new records.
- Templates (`template`) are provided in individual trio files that contain the entire
  `template` record, including the `tags` and all other template record tags. They
  can be loaded and committed to Folio as new records.

Tagging requirements for auto-correction (pushing PI parameters to BMS):
```
- equip, pidConfig, controlVariableRef - "Heating PID Loop"
--- integral, gain OR time, sp, bacnetPoint, writable - "Integral Gain"
--- proportional, gain OR band, sp, bacnetPoint, writable - "Proportional Gain"
```

Tagging requirements for automated open-loop testing:
```
- airTerminalUnit, hotWaterPlantRef, equip
--- heat, valve, cmd, bacnetPoint, writable - "Reheat Valve Command"
--- discharge, temp, sensor - "Discharge Air Temperature"
--- air, flow, sensor - "Supply Airflow", testing requires some airflow

- hotWaterPlant, equip
--- flow, sensor - "HHW Flow", testing requires some HHW flow
```
