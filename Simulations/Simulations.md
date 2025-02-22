#simulations

Goals:
To contribute to the design of the straw tracker array by getting a handle on requirements and options.

To this end [[Garfield++]] simulations were produced by one of Heather's undergraduates to simulate the drift cells and [[Michael's Garfield simulations]]|determine the optimal drift cell design parameters.
]]
From this it was concluded that a series of[[Geometrical simulations| purely geometrical simulations]] were required to decide where to put the newly designed drift cells

The reconstruction algorithm used in these simulates was based on the ROOT minuet2 minimiser. This produced strange results so a [[track reconstruction|track reconstruction algorithm ]]was written in python.






| Efficiency/channels [%/#] | 1      | 2      | 3      | 4      |
| ------------------------- | ------ | ------ | ------ | ------ |
| 4 rows                    | 0.3/76 | 80/152 | 82/228 | 82/304 |
| 5 rows                    | 0.3/96 | 84/192 | 86/288 | 86/384 |
