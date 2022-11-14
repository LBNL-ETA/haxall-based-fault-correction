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

This collection of Axon code and Folio records includes components needed to 
replicate some of the fault auto-correction algorithms presented at
https://doi.org/10.1016/j.buildenv.2022.108900
- Control hunting (PID loop tuning) - see folder `pid`
- Improve AHU static pressure setpoint reset - see folder `g36`
- Improve AHU supply air temperature setpoint reset - see folder `g36`
- Neutralize rogue zones in reset - included in `g36`

Axon and Folio are part of Haxall, an open source framework (https://haxall.io/),
however, some of the code in this package relies upon BACnet libraries and
functionalities that are only available in SkySpark (https://skyfoundry.com/product)
which requires obtaining a paid license.

Please refer to additional `README.md` files in each folder
