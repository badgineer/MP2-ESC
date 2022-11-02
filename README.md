# **MP2_ESC** 
Multi-Platform, Modular, Powerful ESC

![3D_PCB](gh_assets/3d_pcb_front.png)

## Design Goals
**Decent power** (18 FET, so 100-300A should be possible depeding of FET choice, Bus Bars, and cooling) \
**Relatively compact design**, fitting for ebikes / medium-large electric scooters, and cheap to order \
**Modular**, with easily replaceable modules (both bluepill and blackpill compatible hardware wise, 12V and 5V DC-DC stages are modules also) \
**Standard footprint parts**, so replacement parts can be found easily in case of original parts out of stock or out of production \
**Optimized for low cost** production by JLCPCB, including SMT assembly.  \
**Possibility to buy the SMD parts pre-soldered:** All SMDs are on the same side, in large stock at lcsc (at the time of writing), so the board can be ordered with SMDs pre-assembled by JLCPCB for a decent price.

## Compatibility with variaty of Open-Source VESC projects
VESC with [ STM32F405 pill ](https://github.com/davidmolony/F405_pill)  \
VESC with GD32F303CG pill (Netzpfuscher mod, note CG) \
EBICS with F103 Bluepill (Stancecoke) \
[SmartESC V3 (Casainho)](https://github.com/casainho/SmartESC_STM32_v3) \
[SmartESC V2 (Netzpfuscher/Koxx3)](https://github.com/Koxx3/SmartESC_STM32_v2) \
MESC with F401 Blackpill (MxlemmingFOC) \
STM32 Motor Control Workbench (F401, F103)

## PCB
![PCB](gh_assets/pcb.png)

## Required software
The tool to be used for this project is [KiCad](https://www.kicad.org/).

## Building Tips:

### **Bus Bars**
Bus bars are recommended for anything else than very low current. (extra copper wires/bars/plates soldered to the exposed copper strips of the PCB, or at very least a ton of solder on the exposed strips, but this last variant only for low phase currents)

### **Bulk electrolytic capacitors (XC.... )**
We recommend a total of 3000uF, which should be enough for most usecases. 
You need more capacitance the more battery current you plan to use, and the longer (and thinner) your battery wires are. So you can probably also get away with less if you have short thick battery wires.  
Choose voltage rating ~ 1.5x your max battery voltage for a long lifetime. For 48v nominal (54.6V max) battery voltage, 80V or more is recommended. Or just use the same rating as your FETs.  
The total capacitance of the electrolytic capacitors is more important than the exact combination of values. More smaller capacitors probably have a slight advantage of lower ESR, lower inductance, and redundancy in case one failures.

### **Bulk ceramic/MLC capacitors:  (XC.... )**
As much as possible. These need to compensate for the high frequency weakness of the electrolytic capacitors. Overrating voltage rating is recommended. 

### **Capacitors - the rest**
Values are consolidated for easy buying. Voltage rating is 25V or higher regardless if they are on the 12v, 5v, or 3v3 rail on the default design, however you can choose a smaller voltage rating for the 5v and 3v3 rails..  

### **Snubbers (RSx, CSx)**
These are RC snubbers. **They are here only for the footprints. Do not fit them (yet).** The real values (if necessary at all) will be computed after we build the controller and see what ringing we get. Purpose of the snubbers is to dampen that ringing. (if you choose different parts than the one we compute the snubbers for, you might need to compute the snubbers yourself). These components are not present in the pick-and-place or BOM files.

### **FETs**
The default FETs are available from lcsc at the time of writing. They are cheap and have good specs. (low Rds on, low Crss, 100v, etc). 
You can use a fet of your choosing, but please be aware that old Fets (such as the famous 4110 or 3077) have huge Crss, leading to a tiny Ciss/Crss ratio. This ratio needs to be bigger than roughly your max battery voltage, so you will need to compute and add the optional Cgs capacitors (OCx). Small Ciss/Crss results in ringing / parastic turn on (which leads to failure). 
That being said, it’s best to just use Fets with Ciss/Crss > ~100, nowadays they’re easy to find. See the spreadsheet with alternative parts. 

Attaching the FETs to a heatsink: the FETs need to be electrically isolated from the heatsink, but well connected thermally. The options for this are:
* Mica glass (“traditional option”, cheap, easy to find)
* Ceramics (saw this as a new option, never tried it)
* Polymer pads 
* Kapton Tape 

Unfortunately in focusing on making the board small we crammed the FETs very close together. This means some mica or ceramic pads will not fit - and it’s very hard to cut them afaik. So for this version we’re probably stuck with polymer / kapton. 

### **Testing**

* v0.1 build has been tested by mxlemming with MESC FOC firmware on F401CC black pill board, and by Netzpfuscher with his VESC port, in lab conditions. 

### **Known issues/limitations:**
* Pills have very few ADCs, so some sacrifices have been made (choice between analog brake and Motor Temp). 
* gate drivers are not as popular and readily available on lcsc as the other SMD parts
* Having the MCU on a separate board (the "pill" development boards) is a questionable ideea from PCB design point of view. In our testing it seemed to work, but we know it's not without drawbacks.


## FAQ

* **What’s with the many solder jumpers?**
We made a few things hardware configurable. 1) Vsense and Overvoltage Protection optimized for 80 / 100 / 150V power stage, Voltage for peripherals can be set to 5 or 3.3V, Motor Temp vs Brake signal compromise, and of course, changing the wiring to acommodate the bluepill or blackpill pinouts (which vary slightly)

* **Can you assemble it for me?**
You can get the SMD side pre-assembled at jlcpcb (at the time of design all parts were in stock for jlcpcb SMT service). So you’ll only need to solder the through-hole parts and the modules. Currently there is no plan on selling any assembled PCBs.

* **I want more power!!!**
This might not go well. So good luck, you’ll probably need it. Please don't blame us when it goes up in smoke. But do let us know how it goes. Disclamer aside, here are some basic suggestions:
   * Add thick bus bars to the board.
   * Add more/ bigger bulk caps!
   * Use appropriate wires (thick!) 
   * Overcurrent trips at 430A. If you want to come close to it / exceed it, either cut off  the overcurrent circuit by desoldering D4, D5, D6, or be creative with the shunts. But 150A for TO220 fets is a crazy ideea.

* **I want more voltage!!!!**
Realistic limit is 30s lipo for 150V rated components. For more than that the ESC will need serious redesign. 

* **Your part X is bad, I recommend Y!**
We tried to find cheap but decent parts for this controller. Cheap almost always implies a compromise in some other areas, so you might not like our pick :)
It should be fairly easy to switch to other parts on your own: we used mostly standard and popular footprints and packages
If you know better parts or have better solutions, please let us know on our ES thread. We like learning new things. 
....except if you’re going to suggest 3077 or 4110 mosfets. Those things are dinosaurs. They were the biggest baddest thing around during their time, but nowadays belong in a museum. Or on a t-shirt. Please stop recommending them. 

* **Where can I buy parts?**
Lcsc.com, mouser.com. Aliexpress if needed. 
I designed this with jlcpcb smt assembly in mind, so all SMDs were in stock at lcsc when I designed the PCB. Also most of the Through-hole parts. 

* **Why do the battery wires go in seemingly random places in the middle of the board?**
If you have the battery wires at the edge, then the full battery current will need to go through a portion of the battery “traces” of the PCB. I’ve placed them near the middle switch node, so with a tiny exception, the current through the traces is ⅓ of the battery current. 

* **This whole thing is amateur work!**
Yeah, totally true. We are mostly amateurs working on a generic ESC for free. If by this you refer to any specific mistake / set of mistakes, we would love to know about it! Post in the ES thread. Thanks!