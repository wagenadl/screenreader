# Introduction

In visual neuroscience, a common challenge is to synchronize neural recordings with displayed video imagery. Because contemporary video cards perform extensive buffering, it is rarely straightforward to control with millisecond precision when an image appears on the screen. Accordingly, it is difficult to infer the timing between visual stimuli and neuronal responses. A surprisingly low-tech solution is to present, as part of the video stream, a small flashing white/black square in the corner of the screen. The onset and offset times of these flashes can be detected with great precision with a photodiode or phototransistor, which can be taped to the screen with black tape so as to hide it from the subject.

# Circuit diagram

Such circuits have appeared in the literature many times. The one presented here stands out for its simplicity and reliability. 

<img alt="Circuit diagram" src="https://github.com/citneuro/screenreader/blob/main/PhotoNPNAmplifier-11.png" width="800">

The reliability is due to the use of an adaptive threshold (implemented by R2 and C1) that automatically tracks the lighting conditions of your screen. Thanks to an internal [Schmitt trigger](https://en.wikipedia.org/wiki/Schmitt_trigger) (implemented by R3 and R4), the system is insensitive to minor lighting variations (as could, for instance, occur due to bleed-through of light from other parts of the visual display). 

# Ordering parts

The system uses only off-the-shelf components. A [parts list](https://github.com/citneuro/screenreader/blob/main/PhotoNPNAmplifier-11.csv) is provided that includes Digikey part numbers, but those parts can also be obtained from many other vendors, and the choice of opamp is not critical. I like to connect the phototransistor to the board by way of a long cable and a plug + jack, but this is optional. 

# Building instructions

If you are making just one, you can lay out the circuit on a breadboard. However, it is much easier to order a printed circuit board using the provided [Gerber files](https://github.com/citneuro/screenreader/blob/main/PhotoNPNAmplifier-11.zip). When connecting the phototransistor, be sure to pay attention to which leg goes where (see circuit diagram). I like to put the board inside a little enclosure and use the BNC connector (J1) to hold the board to the front panel.

<img alt="PCB layout" src="https://github.com/citneuro/screenreader/blob/main/PhotoNPNAmplifier-11-pcb.png" width="600">

You can also put multiple boards in one enclosure and power them all from a single source. (The provided PCB design has convenient holes for making the power connections.)

# Usage

Either tape the phototransistor directly to your screen, or stick it through a 3-mm hole in a piece of black acrylic (plexiglass) for added stability. The device can be powered by any 5V source, including a USB power brick or port on your PC. (It uses very little power: about 1 mA.) The output from the device is zero volts when the phototransistor detects darkness, or (just under) 5 volts when it detects light. This output can be connected directly to analog or digital input ports of most data acquisition systems.

# Making changes

If you want to make changes to the design, you can edit the circuit diagram (PhotoNPNAmplifier-11.cschem) and PCB layout (PhotoNPNAmplifier-11.cpcb) using my software [CSchem](https://github.com/wagenadl/cschem/), which is available for Linux and Windows.
