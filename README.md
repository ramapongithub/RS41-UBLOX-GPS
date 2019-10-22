# RS41-UBLOX-GPS
How to use a Vaisala RS-41 radiosonde Ublox GPS as an standalone GPS receiver.

GPS-Modules are cheap today. But you also can get them for free, they are falling from the sky.
Every day dozens of radiosondes start. The modern ones, like Graw DFM-09 or Vaisala RS-41, have an GPSR integrated.
This GPSRs can be reused.  An instruction, how to use the GPRS from an Graw DFM-09 is online. (http://happysat.nl/DFM-09/DFM09.html)

Here we will do the same for an Vaisala RS-41.

First you need the radiosonde.
Don't have one? Look at https://radiosondy.info/index.php where they are coming down.

Next step: Disassemble the radiosonde.

If you are down to the PCB and interested in more informations, have a look at bazjos repository at https://github.com/bazjo/RS41_Hardware. 

On his website (https://sondehunt.de/rs41-gps-maus) he has also a solution to use the RS41 as an GPS receiver without destroying the pcb, simply by reprogramming it. An easy way, but has one disadvantage: power consumption.
All parts on the board draw power, even if you don't use them. And you can't shut them down.

We will go the other way, the brutal way of cutting.

The GPRS occupies only this part of the PCB on the front side, 
![Front](https://github.com/ramapongithub/RS41-UBLOX-GPS/blob/master/pictures/front1part.jpg)
and the same part on the rear side.
![Rear](https://github.com/ramapongithub/RS41-UBLOX-GPS/blob/master/pictures/rear2part.jpg)

So, what to do?

1. Cut the board at the marked lines.
![Cutted](https://github.com/ramapongithub/RS41-UBLOX-GPS/blob/master/pictures/rear_cut.jpg)
    The parts on the upper right corner of the cutted piece can be removed.
    
2. Solder wires to the marked points.
![Connection](https://github.com/ramapongithub/RS41-UBLOX-GPS/blob/master/pictures/front_connection.jpg)
    Wether you use the +5V or +3V power connection depends on your application, we will come back to this later.
    GND can be connected practicly everywhere on the board, this is only a suggestion.
    The actual realisation depends on your soldering skills. The connections are pretty small.
    
# Power supply

For 3.3V applications use the +3V connection to power the GPS with 3.3V.

For 5.0V aplications you can use the +5V. But there are some caveats. The voltage regulator will drop the supply voltage for the chip to 3.0V, not 3.3V. If you only receive data from the UBlox, this should not be a problem. An 5V MCU should detect 3.0V as high. For sending data to the UBlox the signal must be stepped down to 3.0V.
