# MP2 Assembly and Testing


## MP2 PCB assembly
The following is not a step by step guide for finishing the MP2 but it still may be useful for people putting together their first PCB. 

Note: in this assembly we have not added any extra copper along the bus bars which is a common practice to increase the total amount of amperage used for these boards. Adding thicker bus bars will be the subject of another tutorial. 

There are MANY tutorials on how to solder and hopefully this is not your first rodeo. At a minimum you are going to need a high wattage soldering iron, decent quality solder, hopefully some flux remover and a multimeter to be able solder this board. 

Looking at the top side of the board, it tends to be easiest to solder in the shorter parts first (so they rest flat on the bench when getting soldered in. So a possible order is:
* JST connectors
* 12V to 5V DC-DC converter
* the larger 12V DC-DC converter
* 20 pin headers

When doing the 20 pin headers...

<img src="../gh_assets/PCB_ASSEMBLY01.png" title="header pin alignment">

Another suggestion:

<img src="../gh_assets/PCB_ASSEMBLY02.png" title="use flux remover">

The 12V-5V DC converter sits funny:

<img src="../gh_assets/PCB_ASSEMBLY03.png" title="DC-DC sits funny">

Heat shrink tubing is your friend!

<img src="../gh_assets/PCB_ASSEMBLY04.png" title="soldering Vbat and GND">

Use precision:

<img src="../gh_assets/PCB_ASSEMBLY05.png" title="watch out for components">
<img src="../gh_assets/PCB_ASSEMBLY06.png" title="watch out for solder bridges">

**NOTE:** These pics are included to talk about soldering issues, **BUT BE ADVISED** We strongly recommend users take advantage of the three holes on each phase to solder in larger wires and get improved current sharing with the MOSFETs. Take a look at [THIS FUTURE DOCUMENTATION] for higher amperage connections. 

<img src="../gh_assets/PCB_ASSEMBLY07.png" title="it aint pretty">

## MP2 continuity testing
Before you're finished with soldering be sure to do some important testing of your board. One set of tests involved using a continuity checker on your multimeter. This is a **short video** to help you get started:

[![MP2 continuity checking](https://img.youtube.com/vi/L9bziAqBU64/0.jpg)](https://www.youtube.com/watch?v=L9bziAqBU64)

Once your set up for testing run through the following tests:

<img src="../gh_assets/PCB_ASSEMBLY08.png" title="pcb continuity chart">

<img src="../gh_assets/PCB_ASSEMBLY09.png" title="VBat continuity check">

<img src="../gh_assets/PCB_ASSEMBLY10.png" title="GND continuity check">

<img src="../gh_assets/PCB_ASSEMBLY11.png" title="Phase wire continuity check">

## MP2 resistance testing
Since you have your multimeter out there are some other useful measurements to take. These tests can vary based on what type of meter you have. Also sometimes the readings will take a while to settle down to the final value.

<img src="../gh_assets/PCB_ASSEMBLY12.png" title="Phase wire resistance check1">

<img src="../gh_assets/PCB_ASSEMBLY13.png" title="Phase wire resistance check2">

<img src="../gh_assets/PCB_ASSEMBLY14.png" title="Ground to testpoint check">

<img src="../gh_assets/PCB_ASSEMBLY15.png" title="Ground to VBat check">

## MP2 powering up


## MP2 powering up

Hopefully you have experience powering up a PCB for the first time. 

Here a subset of things you can do when testing the MP2 for the first time.


* Remove the pill from the MP for this testing
* Connect your multimeter to GND
* Apply power to VBat
* Note that in some cases the DC-DC converter wont activate at <42 volts
* Test the points circled on the figure below

