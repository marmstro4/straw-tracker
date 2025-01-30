#simulations

In response to the failure of the ROOT minuet2 minimiser to produce adequately understandable and consistent results a separate python program called "radialfit.py" was written. It is available https://github.com/marmstro4/variableaxiscylinderfit along with some example cylinders to fit.

It works by calculating the residual distance from the surface of a series of cylinders defined by (x,y,z,r,L,mod) to a line representing a charged particle track defined by (x0,y0,z0,ux,uy,uz). 

Here x,y,z is the centroid of each cylinder, r is the radius, L is the length and mod is the module number (1...4) defining if the cylinder orientated along the x or y axis.

x0,y0,z0 is the origin of the line, ux,uy,uz is the unit vector for the line direction.

The scipy.optimize.minimize function varies the line parameters in consideration of the response of the residual.

When isotropic trajectories are generated uniformly throughout the target middle (+/- 2mm,+/- 2mm, +/- 75mm) one obtains a z vertex resolution of 500(6)um for a straw tube array offset along z by one straw with straws spaced 2mm along z 1mm along x and y. Below is a histogram showing this.

![[Pasted image 20250108112214.png]]

If I vary the spacing and offsetting:

| config                                  | resolution [um] |
| --------------------------------------- | --------------- |
| 2mm z spacing 1mm xy spacing z offset   | 495(7)          |
| 2mm z spacing 1mm xy spacing xy offset  | 482(6)          |
| 2mm z spacing 1mm xy spacing no offset  | 484(6)          |
| 2mm z spacing 1mm xy spacing zxy offset | 485(5)          |
| no offset                               | 575(8)          |
| z offset                                | 571(8)          |
| xy offset                               | 559(7)          |
| zxy offset                              | 574(7)          |
| 1mm z spacing 1mm xy spacing z offset   | 517(7)          |

According to the [[Geometrical simulations]] the "2mm z spacing 1mm xy spacing z offset" option has an average length integrated resolution of 77.6%. The "1mm z spacing 1mm xy spacing z offset" option has an average length interated resolution of 73.5%.

Therefore probably best to go for the 2mm z spacing option.


Previously the default (SLSQP) python minimiser was used. Here various options were investigated

| engine      | resolution | # counts in 1sigma | comments                            |
| ----------- | ---------- | ------------------ | ----------------------------------- |
| SLSQP       | 500        | 2613               | Guassian, small tailes              |
| BFGS        | 364        | 1194               | Guassian, large tailes              |
| Powell      | 308        | 3199               | Perfect Guassian, slow              |
| Nelder-Mead | 291.5      | 3242               | Slightly offcentre, slow            |
| CG          | 235        | 2164               | Slightly offcentre high vertex tail |
| L-BFGS-B    | 543        | 2500               | Gaussian, small tails               |
| COBYLA      | 677        | 2200               | Gaussian, large tails               |
Here Powell and Nelder-Mead achieve near twice better resolutions than the SLSQP. No missing counts being poorly reconstructed and therefore lost. Both ran at ~20-30 proton events per second. Powell's shape was near perfectly gaussian while the mean was shifted in Nelder-Mead.

With the more understandable shape Powell was selected.

The detection efficiency and resolution were also investigated as a function of the number of possible layers and the size of the straws. Here efficiency in 3 sigma is simply a check for how many events with 3 hits were reconstructed in the peak rather than lost. This is effectively the loss in the reconstruction stage and is on the order of a few percent.

| layers | resolution [um] | geometric efficiency [%] | efficiency in 3 sigma [%]<br> |
| ------ | --------------- | ------------------------ | ----------------------------- |
| 2      | 370             | 24.9                     | 23.6                          |
| 3      | 356             | 67.8                     | 65.8                          |
| 4      | 325             | 73.1                     | 71.1                          |
| 5      | 322             | 73.8                     | 71.9                          |
| 6      | 332             | 73.4                     | 71.4                          |
| 7      | 320             | 73.1                     | 70.8                          |
| 8      | 317             | 73.4                     | 71.7                          |
Contrary to intuitions it is still possible to reconstruct with 2 layers. This is because particles scatter in 3D and there's still 100 straws in this configuration.

This table shows there is not a significant decline in efficiency and resolution with only four layers. Geometries including numbers of layers other than 5 and the number of rows that optimize the geometric coverage [[Mechanics|were then studied for different possible radii]].

The detection efficiency and resolution were again studied for these newly identified options:

| straw radius [mm] | layers | rows | resolution [um] | geometric efficiency [%] | efficiency in 3 sigma [%] |
| ----------------- | ------ | ---- | --------------- | ------------------------ | ------------------------- |
| 3                 | 3      | 34   | 482             | 71.0                     | 69.6                      |
| 4                 | 4      | 24   | 431             | 75.9                     | 73.6                      |
| 5                 | 4      | 18   | 461             | 71.0                     | 69.9                      |
| 5                 | 5      | 16   | 344<br>         | 64.8                     | 64.5                      |
| 6                 | 3      | 16   | 469             | 67.3                     | 65.7                      |
