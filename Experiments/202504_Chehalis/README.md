# Train show in Chehalis, April 2025

## Signals
* A signal setup similar to the Tacoma experiments was installed, consisting of a CANVOUT, a 5V bistable relais triggered by one of the outputs. This relais would switch both the lightbulbs of the signal to 12V, as well as the track power. Presence detection was provided by two of IR gates from Adafruit. The gates were still oriented 90 degrees to the direction of the track. There were no problems with collisions between trains and the gates, as the geometry was shrunk from the previous attempt.
* There were problems with pushers: They could not make it past the signal, because the passing cars at the front of the train would switch the signal to red, and stop the train. It wwas necessary to disable the stopping track to get things to work. As a potential fix, Magnus proposed to of put the presence detector further back. Another option could be to trigger the transistion to red by the end of the train, rather than the front. I seem to remember that we reached the same conclusion when we ran with a CS2-controlled signal in Tacoma.
* In light of the previous point, each stopping track needs an easy (switched) override for each of the three loops, for cases where there has been an oversight. This override could contain of physical switches, or a high-reliablity electronic control.
* The matter of running right-handed or left-handed was discussed several times, without a firm conclusion. We may be in analysis paralysis.

## Turnout control
* Installed a CANSOL module to control two of the turnouts on the station module. This only happened on Sunday, so there was not a lot of time for experimentation. It appeared to work reliably. 

## CBUS
* Reliability of the CBUS nodes was good, no hangs or crashes.
* It is not clear whether 5V relais or 12 V relais are the better option. This depends on what other things outputs are connected to, as the whole bank lives off of one supply voltage.
* There is some head scratching needed whether a full setup of signals (assuming 3 block signals with Hp0/Hp1) and 2 entry signals with Hp0/Hp1/Hp2 as the worst case). Currently, even a simple block signal uses two output bits, which is not efficient. 
* There were problems with the bus terminations on both ends of the layout. 
    * The one on the mountain end was put in at Monroe, in a haste, and it never really connected. 
    * On the village end, the cable pulled out of the ferrule that was attached to the WAGO connector (first time this happened).
* An easily accessible CBUS debug port on the podium would be very nice.

## Other items discussed
* Discussions: Jan proposed to put a crossover from the inner to the outer loop, and back. After some discussion we concluded that it is not a great idea: There is not a lot of added value in terms of operational interest, but a lot of potential for problems and accidents. Maybe a spur would be more useful.
* How do we attach signal masts to Precision Board, so that it fails in a controlled manner? I.e. you want the thing that breaks to be cheap and easy to replace. Bonus points for having a storage position, where the signal could be mechanically fixed during transport.

## Next steps
* Try to drive each Block signal from a single bit, using bistable relais. Similarly, two bits should be sufficient for 3-aspect entry signal. This should allow to control all the signals and presence detectors using a single CANVOUT node.
* Conclude the direction of travel discussion.