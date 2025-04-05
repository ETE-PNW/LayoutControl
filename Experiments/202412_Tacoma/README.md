# Train Show at the Tacoma History Museum, 12/25
## Overview
This was the first test trying to use a signal and some train control. The setup was as follows:
* A [Viessmann 5213 digital switching decoder](https://viessmann-modell.com/en/electronic/electronics-digital/107motorola-digital-switching-decoder/5213)
 was assigned an MM address and controlled by the 3-rail CS2.
* A light-only signal from an unknown manufacturer was connected to one of the ports of the 5213. This port would connect either the red or the green lamp to +12V.
* Another port of the 5213 was assigned to turning part of the 2-rail track on Chris' modle on and off. This would be the stopping section.
* For feedback, a [Marklin 60883 "L88"](https://www.marklin.com/products/details/article/60883) module was connected to the CS2. Among other things, this provides 16 logical inputs that show up on the CS2 as s88 devices. The L88 requires its own power supply.
* Two of these ports were connected to presence detectors. One of these was positioned right after the signal (to turn it to red), and the other on the other 2-side track on the module (to turn the signal back to green). Find more detail of the presence detectors 
[here](Components/PresenceDetector). The Presence detectors need their own 5 V power supply.
* One additional port on the L88 was connected to a set of two buttons in a Marklin control console. One would set the signal to red, the other one to green, basically constituting an override for the signal operation.

## Software configuration
After the L88 is configured into the CS2 as an s88 device, the four logic inputs can be observed as inputs on the device. Two memories were configured which would operate the signal in response to input events from these inputs. 

## Learnings
* It is a good idea to draw a layout page on the CS2, which shows all the sensors and memories. This helps greatly with debugging.
* The reliability of this solution was very much a mixed bag. Sometimes it would run without any issues for hours, sometimes the signal would get "stuck" for no obvious reason. To get out of the "stuck" state, sometimes it was helpful to reboot the CS2, but more often it wasn't.
* The likely cause of this "being stuck" is that there is a known problem with the CS2, which is as follows: When an input event triggers a macro to change the state of device X _while a change of status is already ongoing_, the internal state machine would hang forever. This can be recognized by a yellow circle that is visible on the memory in question. This issue is not very well documented in the CS2 documentation.
* This problem occurs because of the way the signal is set up - this is not a real block system, where there would always be an empty block between trains. In our scenario, trains follow each other closely, which can lead to "competing" sequences of events. The fact that our presence detectors deliver sequences of events (while looking through the gaps beetween train cars), doesn't help with this at all.

### Raw notes:
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
