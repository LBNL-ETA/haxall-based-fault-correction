## HVAC fault correction and optimal control: Haxall-based (Axon) reference code for SkySpark developers

## Introduction

In partnership with Berkeley Lab researchers, a network of partners have implemented and demonstrated strategies to enhance their smart building platforms with capabilities spanning fault correction, optimal sequences of operation, automated commissioning with root cause failure identification, and best practice demand flexibility. 
Berkeley Lab is funded by the Department of Energy to provide direct assistance to product and service providers who wish to integrate these open solutions into their offerings. So that we may best support and track these efforts, please register here to access the code.(https://transformingbuildingcontrols.lbl.gov/reference.php)   

The collection of Axon code and Folio records includes components needed to replicate solutions that were documented in several articles (specifications, field tests, PID loop tuning) and further tested in several subsequent field applications:

- Correct zone temperature setpoints to operational intent – in folder `zat-sp`
- Identify incorrectly programmed schedules compared to operational intent – in folder `ahu-schedule`
- Optimize economizer high-limit lockout temperature setpoint – in folder `econ-lockout`
- Implement best practice AHU static pressure setpoint reset - in folder `g36`
- Implement best practice AHU supply air temperature setpoint reset – in folder `g36`
- Identify and suppress rogue zones in reset strategies – in folder `g36`
- Correct control hunting (PID loop tuning) – in folder `pid`

Axon and Folio are part of Haxall, an open source framework (https://haxall.io/), however, some of the code in this package relies upon BACnet libraries and functionalities that are only available in SkySpark (https://skyfoundry.com/product) which requires obtaining a paid license.

Additional `README.md` files are provided in each folder.

## Copyright

Haxall-based (Axon) fault auto-correction package for building HVAC system (Haxall-based Fault Correction) Copyright (c) 2022, The Regents of the University of California, through Lawrence Berkeley National Laboratory (subject to receipt of any required approvals from the U.S. Dept. of Energy) and kW Engineering. All rights reserved.
If you have questions about your rights to use or distribute this software, please contact Berkeley Lab's Intellectual Property Office at IPO@lbl.gov.

NOTICE. This Software was developed under funding from the U.S. Department of Energy and the U.S. Government consequently retains certain rights. As such, the U.S. Government has been granted for itself and others acting on its behalf a paid-up, nonexclusive, irrevocable, worldwide license in the Software to reproduce, distribute copies to the public, prepare derivative works, and perform publicly and display publicly, and to permit others to do so.

## License

This repository is under the following [license](https://github.com/LBNL-ETA/haxall-based-fault-correction/blob/main/License.txt).
