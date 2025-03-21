#simulations

Building upon the work of [[Garfield++|Heather and Griffin]] a number of drift cell design parameters were investigated:

1.[[ Simulated gas-mixtures]]
2. [[Electrode voltage]]
3. [[Cell radius]]
4. [[Number of cell layers]]

The dependence on the energy of the[[ ejectile]] was also studied

[[Gas system|A variety of gas-mixtures are available ]] here mixtures of Helium/Argon-CO2/Methane

In order to get DOCA from the drift chambers (using which the trajectory can be reconstructed), one must convert from the charge vs time plot.

Questions arise regarding how to do this. The so called "D-T correlation". The brass tacks are available ![[note95-022.pdf|here]].
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

Plotting in black the real DOCA and in red the reconstructed DOCA. New alogorithm seems to do a nice job.

![[Pasted image 20241122142150.png]]


The average z is reconstructed with ~2-3 mm resolution:  (more statistics suggested 2.4mm... wait till have thousands) 

![[Pasted image 20241122155905.png]]

Ultimately however the resolution didn't improve very much as the GARFIELD drift cell properties (i.e [[Electrode voltage]],  [[Cell radius]], [[Simulated gas-mixtures]]).

It did however change significantly depending upon the [[Number of cell layers]] and the [[Cell radius]].

This suggests the properties of the cells themselves aren't so sensitive (so long as industry norms are adopted) and that the resolution is dominated by the arrangement of these cells.

A series of purely [[Geometrical simulations]] where therefore produced.

