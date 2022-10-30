# **MP2_ESC** 
Multi-Platform, Modular, Powerful ESC

![3D_PCB](gh_assets/3d_pcb_front.png)

## Design Goals
**Decent power** (18 FET, so 100-300A should be possible depeding of FET choice, Bus Bars, and cooling) \
**Relatively compact design**, fitting for ebikes / medium-large electric scooters, and cheap to order \
**Modular**, with easily replaceable modules (both bluepill and blackpill compatible hardware wise, 12V and 5V DC-DC stages are modules also) \
**Standard footprint parts**, so replacement parts can be found easily in case of original parts out of stock or out of production \
**Optimized for low cost** production by JLCPCB, including SMT assembly.  \

## Compatibility with variaty of Open-Source VESC projects
[VESC with STM32F405 pill (davidmolony)](https://github.com/davidmolony/F405_pill)  \
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