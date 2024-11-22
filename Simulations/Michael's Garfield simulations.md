Building upon the work of [[Garfield++|Heather and Griffin]] a number of drift cell design parameters were investigated:

1. Simulated gas-mixtures
2. Electrode voltage
3. [[Cell radius]]
4. Number of cell layers

[[Gas system|A variety of gas-mixtures are available ]] here mixtures of Helium/Argon-CO2/Methane

In order to get DOCA from the drift chambers (using which the trajectory can be reconstructed), one must convert from the charge vs time plot.

Questions arrise reguarding how to do this. The so called "D-T correlation". The brass tacks are available ![[note95-022.pdf|here]].
Here is an example plot of drift time vs charge collected from a Garfield simulation:

![[Pasted image 20241118103437.png]]
The question then is do we take the main bulge or d we take the whole thing including tails.

One approach is to look up the real DOCA, compare this to both widths and then attempt to predict the DOCA. 

This allows one to compare the residual in each case.

Here is a plot of the position of a hit (y (along x axis)) and the width one (x) receives. One obtains something quite different for full width (blue) electron bulge (black)

![[Pasted image 20241119144352.png]]


When I plot width time (y) vs distance of closest approach I obtain the following for the two methods:
![[Pasted image 20241119151720.png]]

Here I improve the fitting by making it an exponential: ![[Pasted image 20241119154159.png]]

Extreme data points seem to ruin fitting. Now excluded:
![[Pasted image 20241119164346.png]]

A function which calculates the average percentage DOCA residual across a range of energies and trajectories suggests ~10%.

Implementing methods for straw arrays and visualisation, paths through multiple tubes are possible.
![[Pasted image 20241121190043.png]]