#simulations

[[Michael's Garfield simulations|Having learned the design parameters of the straws themselves aren't so sensitive]] outside of size and positioning a series of geometrical simulations were performed.

 Isotropic lines were generated and the intersection of those lines with cylinders (taking the place of the straws) are solved for distances of closest approach to their radial centers.

Taking a uniform spread of +-10% for the DT correlation from signals to radii, the "uncorrected" radii are fitted with a straight line using the ROOT minuet2 minimizer.

The xy trajectory of the projectile through the target is known both incoming and outgoing therefore the cost function was weighted with this information.

Here is a straw tube array geometry where the straws are transverse to the target for maximum z sensitivity.


 (x,y) plane. 
![[Pasted image 20241205163822.png]] 

(y,z) plane
![[Pasted image 20241205172301.png]]

In the transverse box design there are four detector modules. These are simply rectangular stacks of detectors.

Writing the reconstruction algorithm one obtains a resolution of ~1.5mm. Here plotted is the reconstructed vertex in [mm] centered at 0. There are some weird periodic features however so not this needs to be improved. 

![[resolution.png]]


Changing the geometry leads to different resolutions

| Offset Type | Z resolution [mm] |
| ----------- | ----------------- |
| None        | 1.52              |
| Z           | 1.75              |
| XY          | 1.24              |
| Z & XY      | 1.62              |
It seems offsetting the straws in the xy axis improves the resolution.

There are still problems related to the reconstruction algorithm however. If I remove the DT correlation step and get perfect circles I get:

![[Pasted image 20241213134845.png]]

Here only the algorithm (minuet2 minimiser) if limiting the reconstruction. When the 10% DOCA variability is added: 

![[Pasted image 20241213135122.png]]


Playing with the initial conditions works suspiciously well: Here is x vs z with resolution on the vertical.

![[Pasted image 20241213153914.png]]

Taking the integral of the region around the main peak one finds that there are actually many events outside the good region.                                      

![[4.png]]

Here we have a zy plane view of the reconstruction of a black line with green hits with the blue line. Here it works very well. It seems the outside hits come from where the minuet2 minimizer algorithm finds a local minimum that passes close to the correct vertex but at the wrong angle (i.e the green and red lines). 

Need to replace the current minimizer with one less prone to initial conditions and local minima.

![[5 1.png]]

The influence of spacing the straws out and introducing offsets was also studied.

According to the [[Mechanics]] sketch we need to allow for interior terminating points and exterior electrics/gas boxes on the end of each module.

![[dimentions.png]]

Now updating the geometrical simulations with this in mind 

XY

![[reco_z.png]]

ZY

![[Pasted image 20250105184039.png]]

Varying the spacing of the straws and the dimensions they are offset along it was determined that a 2mm z axis spacing and a 1mm xy spacing with a z offset would result in an optimal combination of efficiency and hit multiplicity.

The detail of these studies are pasted in excel document ![[efficientcz.xlsx]] also availble online at https://docs.google.com/spreadsheets/d/1AbDyazIr0jRVy4KOvq615NBmyHs7rCd-7EA8Rkx203g/edit?usp=sharing

Interestingly, the gaps along the z axis actually help in terms of efficiency at the end regions. Over the course of 30 straws, 15 0.2mm gaps increases the effective length by 3cm (or 3 straws). The gaps do however lower efficiency over all as particles can fly throught the gaps.

A minimum of 1mm is required so the straws can be seperated. At 2mm gaps along the z axis the detection efficiency and number of hits integrated along the whole length of possible reaction verticies is maximised.

Furthermore, now with the new z reconstruction algorithm it was determined that only a z axis offset improves the the reconstruction resolution and not a xy offset. Introducing the z axis offset also marginally improves the efficiency and average number of hits.

Regarding hits... here is a plot of the z resolution for only multiplicity 3 hits. 

![[local_minima.png]]

Here we can see clearly defined local minima. These correspond to "crossing" trajectories that do come close to predicting the correct z vertex but do so with a completely incorrect crossing angle.

If we go to a multiplicity of 4 hits these minima dissapear.

![[4hits.png]]

This distribution is very strange. It's not Gaussian. It a series of multiple layers of bulges on top of each other with a Gaussian peak in the middle on top. ~200-500um resolution peak).

If I take the integral I find these proportions of events exist within these limits:

| limits [mm] | effective [%] | total [%] |
| ----------- | ------------- | --------- |
| 10          | 80            | 69        |
| 5           | 66            | 57        |
| 2.5         | 51            | 44        |
| 0.5         | 31            | 27        |

Here the effective efficiency is those out of those events that had more than 2 hits and the total with respect to all simulated events, even those that did not scatter into the detector.

As the multiplicity increases the proportion of events in the bulges closer and closer to the middle increases. The resolution of that excellent peak in the middle does not change. 

[[track reconstruction | As it stands the reconstruction algorithm needs to be improved]] and its results understood. For now it is at least sufficient to say that we should target an average of 4 hits.

A 2mm straw spacing along z with a 1mm spacing along xy and a z axis offset maximises efficiency and achieves a average hit number of 3.4. 

Adding one more layer of straws would best satisfy this benchmark provided funding is available. 

In these simulations protons are assumed to be emitted isotropically. Travelling at relativistic velocities along the z axis, a strong lorenz boost is anticipated for knocked out protons.

The positioning of straws must therefore be optimized for where protons are likely to be knocked out. Assuming protons are knocked out isotropically in the ion reference frame at ~200MeV, the relativistic velocity addition formula can be used to obtain the lorenz boost. Implementing this into the geometric simulations one obtains a forward conical shift in proton trajectories as shown below.

![[Pasted image 20250128144940.png]]

This suggests more straws are required downstream of the target. 

A few shifted array geometries were investigated.

1. r=4mm straws shifted with end gap
2. Same with the top layer in line shifted forwards in z so inline with layer below
3. r=5mm straws shifted with end gap
4. Same again with the top layer in line shifted forwards in z so inline with layer below
5. r=4mm straws shifted with end gap, but with 3 layers so longer

Option 1:

![[Pasted image 20250129153750.png]]

option 3:

![[Pasted image 20250129174210.png]]

Here are the results of these investigations:

| option | resolution [um] | Geometric efficiency [%] | 3sigma efficiency [%] |
| ------ | --------------- | ------------------------ | --------------------- |
| 1      | 442             | 67.7                     | 66.9                  |
| 2      | 437             | 69.5                     | 68.7                  |
| 3      | 448             | 71.8                     | 70.6                  |
| 4      | 451             | 71.6                     | 70.6                  |
| 5      | 436             | 70.67                    | 69.5                  |
It seems that although you can fit more straws into the overhang with 0.5mm straws, the reduced coverage at backward angles eliminates any gains compared to 5mm straws that can span the distance.

What if we went for 3 layers at 4mm? (Added to table as option 5). The efficiency is not much better or worse. Probably the simplest geometrically speaking. 

Many experiments will make use of a 5cm not 15cm target however. In this case the gains obtained in terms of efficiency in the end regions will be lesser. In these experiments it is of course better to have 4 layers, as there is better coverage in the mid region where in the smaller target more ions are emitted.

As a side note, when the lorenz boost was introduced reconstructed z vertex distribution becomes pointer, so much so that its no longer perfectly described by a Gaussian distribution.

![[Pasted image 20250129173116.png]]

Option 3, [[Pasted image 20250129174210.png|as seen above]], seems to be the best option. Consisting of 296 straws, achieving a 448um resolution and reconstructing 71% of all events into final peak. It is worth noting that the efficiency with the 5cm target is 77%.

It turns out the target cell is not actually centered in the vacuum chamber. It's shifted forward 22.74mm from the midpoint. Furthermore its actully only 144mm long and looks like this.

![[Pasted image 20250203150232.png]]

In this case option 3 obtains only 65.3% efficiency. Assuming the 5cm target is still centered, its resolution actually improves to 78%.