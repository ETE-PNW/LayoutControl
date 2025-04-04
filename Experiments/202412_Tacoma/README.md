# Train Show at the Tacoma History Museum, 12/25
## Overview
Signal connected to CS2, using Viessmann DCC control box and CS2. Control button and presence detectors connected via L88.

## System configuration

## Learnings

### Raw notes:
* "Gelber punkt"
* 3-rail CS2 is a poor choice for control, as it frequently gets shut off, or interrupted through shorts
* Should use spare pair for digital. This would also allow us to run analog on the outer loop
* Analog/digital switching for CS2 is critical, to allow transfer of signal control
* Need to try resistor to keep track slightly powered
* Original IR gates are too wide
* 18 W is not enough for running 2 trains.
* Maybe a dedicated CS1 might be an option?
* We should allow for 12 ft. as the maximum length for a train. 
* There is lots of benefits in running more than one train, even with the flaky manual control
* When the 3-rail CS2 shuts down (e.g. because of a derailment/overload), the 2-rail signaling becomes non-functional, leading to accidents there. This is a terrible idea. We should either have a dedicated block controller, or at least use the 2-rail CS2, which doesn't get used nearly as much.
* Current detectors work fine on DC and DCC. Presumably also on AC. Might this be all we need? Should every module be outfitted with 6 of them?
* I would like to have semi up-to-date status information on the groups.io wiki, or on some other shared space.

[TODO] Add proper description and notes
