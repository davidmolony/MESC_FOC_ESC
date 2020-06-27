# MESC_FOC_ESC
MESC, Molony ESC, STM32F303 based FOC+BLDC ready, HALL, Encoder, Sensorless, single sides, 2 layer, ~90A @48V


This ESC is intended as a cost optimised alternative to the VESC, by utilising:

Standalone, industry standard footprint gate drivers

Standard D2PAK or H2PAK FETs

Cheap (~2.5$) STM32F303CB microcontroller

Board dimensions 100mmx50mm, so that it can be panelised and manufactured by JLCPCB, or two boards can be combined into one 100mm2 JLCPCB

It is not cross compatible with VESC software, and does not intend to be. VESC has run away with itself in terms of cost, firmware abstraction... in the opinion of this project's author.


# Layout:  
Layout optimised to minimise current loop path, and keep the board completely single sided assembly.

For thermal management, the FETs have vias underneath the drains, which can be interfaced with a heatsink on the PCB underside, using silicone pad/thermal paste & insulator.

# MCU uses:
Timer1 on PA8,9,10 (high) and PB13,14,15 for PWM generation.

Onboard opamps for current sensing and paralelled comparators input on pins PA1,7, PB0.

Phase voltages can be measured on PA3,4,5, or alternatively, digitally read to detect ZC .

Main voltage can be read on PA0.

# Interfaces:
External Interfaces include Hall/Encoder, I2C, PWM in, UART, USB FS.

Hall sensors on Timer4 PB6,7,8, alternatively Encoder can be run on Tim4 PB6,7

Timer3 channel 1 for standard RC PWM input.

USART3 Tx Rx on PB10,11.
USB on PA11,12, with 1k5 pullup to signal FS mode. Canbe used for reflashing (hypothetically).

I2C1 on PA15(SCL) and PB9(SDA), with a plug for a standard SSD1306 breakout. Alternatively, inertial sensor board could be plugged on breakout wire.


Expected BoM cost:  
0.4USD board  
6x2USD FETs  
2.5USD MCU  
3x1USD gate drives  
1USD SMPS converter  
0.4USD inductor  
??? connector cost (dependent on what's fitted, wire in...)  
0.3USD linear reg  
~3USD caps (dependent on how many you want to solder on, which is dependent on distance to battery, desire to comply with EMC, headroom above FET voltage... etc.)  
0.6USD shunts and other resistors  
0.3USD Optional TVS diode, primarily to protect SMPS, which is only rated to 65V  
Total: ~23-24USD  

