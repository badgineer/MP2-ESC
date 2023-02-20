# Documentation for MP2

**The documentation that we have here attempts to help people at many different skill levels to better understand the MP2, as as other Electronic Speed Controllers (ESCs). What is important is that the MP2 is not a commercial ESC. It is not possible to contstruct, test and run MP2 without a basic understanding in electronics, circuit construction, C-programming and the general principles behind BrushLess DC (BLDC) motors. We have a partial collection of materials to help, and we're also going to assume when it comes to something like running an oscilloscope you can search the web to educate yourself. Good luck.**

The following are some resources that we strongly encourage you to read and understand before proceeding:
## Appnotes ##

A couple of appnotes that walk through BLDC operation [[LINK](https://www.monolithicpower.com/media/document/Brushless_DC_Motor_Fundamentals.pdf), [LINK](https://www.monolithicpower.com/media/document/Brushless_DC_Motor_Fundamentals.pdf), and [LINK](https://www.st.com/resource/en/application_note/cd00020086-sensorless-bldc-motor-control-and-bemf-sampling-methods-with--st7mc-stmicroelectronics.pdf)]. In addition to explaining a lot of the general principles of BLDC operation, these texts will help you start to get familiar with a lot of important terms involved with motors. 

## Youtube videos

* An in depth introduction to ebike motors and controllers [[LINK](https://www.youtube.com/watch?v=c96n0Ma2rLY)]
* A deeper dive by into motor considerations from the same presenter [[LINK](https://www.youtube.com/watch?v=dxJe_gygRGU)]
* How PWM signals are generated to create sinusoidal commutation [[LINK](https://www.youtube.com/watch?v=-By_vt27Xhs)]
* (I'd be curious to know if the MESC uses the state space vector approach here: [[LINK](https://youtu.be/-By_vt27Xhs?t=164)]
* A very nice series relating motor behavior important math principles [[LINK](https://www.youtube.com/watch?v=EHYEQM1sA3o)]

## MP2 Operations

Readers are also strongly encouraged to read documentation [[for the MP2](https://davidmolony.github.io/MESC_Firmware/)]. 

And our own David Molony has created several instructional videos for the MP2
* [STUB] Be sure to have a look at this flow diagram depicting fast and hyper loops, and these two videos
* [LINK](https://youtu.be/D8OxaPtngFE) Description.
* [LINK](https://youtube.com/shorts/5mvyW02K6BA) Description.
* [LINK](https://youtube.com/shorts/p_EUAOHa-1w) Description.
* [LINK](https://youtu.be/9agJsvzlajI) Description.
* [LINK](https://youtube.com/shorts/ht_xRyyBOWQ) Description.

## Flashing, MP2 assembly, and construction
* MESC Firmware on the MP2 -- getting started with STM32CubeIDE [[LINK](FIRMWARE_INTRO.md)]
* Gathering motor parameters [[LINK](MOTOR_PARAM.md)]
* Pin mappings between MP2 and the F405 pill [[LINK](MP2_F405PILL_PINOUTS.md)]
* MP2 assembly, testing and firmware [[LINK](PCB_ASSEMBLY_TESTING.md)]
* MP2 bus bar methods [[LINK](HIGHER_AMP_ASSEMBLY.md)]
* Some (bad) examples of connecting the MP2 to a motor [[LINK](QS165_MP2_WIRING.md)]
* Gallery of enclosures [[LINK](ENCLOSURE_GALLERY.md)]
