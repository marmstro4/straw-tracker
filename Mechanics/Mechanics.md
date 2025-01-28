The straw-tracker will be situated inside the [[GRETA]] array surrounding the [[ExPRT-target]]

Here is an early sketch:

![[Expert_Diagram.png]]


Each straw module is intended to consist of straws terminating in a grounding plate and feeding into a gas tight box into which [[Electronics|electrical connections]] and [[Gas system|gas]] are fed. The grounding plate and box are intended to be connected along the length of the straws by four aluminium struts.

Here is an illustrated CAD drawing of where the aluminum struts would go:

![[module.png]]

Here's a CAD drawing of the in-out box:

![[box.png]]

While prototyping we 3D printed a pair of boxes. One temporarily serving as a terminating plate.

One of the issues with this design is ensuring the tubes (which are pressing up against each other) are seated in an air tight fashion. Additionally the tubes are intended to be electrically isolated so if the outer surface of the tubes are touching this could be problematic.

In addition the pillar design blocks much of the "working room" to feed the staws their electrical connections. Also the bottom of the box must be accessible so straws can be fed in and connections made in the first place. 

A screwable bottom must be added. This requires room be made for blocks of plastic at the corners to be screwed into.

Additionally the straws need space ~1cm in which to terminate and space for the eletric connections and gas to feed into (~4-5cm remaining available for 1cm straws).

Below is a diagram with realistic dimensions, now with straws spaced by 1mm.

![[dimentions.png]]

Here is a cad drawing of one of the four modules featuring plastic screwing points.

![[boxes.png]]

The target cell itself is 150mm long with an internal radius of 30mm. It is shown in red.

![[Pasted image 20250123185005.png]]

It is enclosed by a vacuum chamber of radius 63.5 and length 270mm. It is transparent in these images. It is also fed by a LH2 exchange arm shown in green.

![[Pasted image 20250123184939.png]]

Based on these dimensions inside the 150mm radius sphere the following combinations of layers and rows for particular radii maximise coverage around the cell. Too few rows and its not long enough. Too few layers its not tall enough.

| straw radius [mm] | layers | rows | straws |
| ----------------- | ------ | ---- | ------ |
| 2                 | 2      | 39   | 312    |
| 3                 | 3      | 26   | 312    |
| 4                 | 4      | 20   | 320    |
| 5                 | 4      | 20   | 288    |
| 5                 | 5      | 16   | 320    |
| 6                 | 3      | 13   | 156    |
Here is a comparison of the two 5mm options in the yz plane:

![[options.png]]