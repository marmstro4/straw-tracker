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