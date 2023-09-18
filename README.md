# Physical Design
## Day 1
### Topic 1: Design Preparation Step
- Running `flow.tcl` and adding package and design

![Running flow.tcl](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day1/first_prep.png)

- `runs` folder

![runs](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day1/runs.png)

### Topic 2: Review files after design prep and run synthesis
- `tmp` folder inside `runs` folder

![runs_tmp](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day1/runs_folder_tmp.png)

- `merged.lef`

![merged_lef](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day1/merged_lef.png)

- `run_synthesis`

![Run Synthesis](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day1/run_synthesis.png)

### Topic 3: Steps to characterize synthesis results
- To calculate flop ratio:

![stats](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day1/run_synthesis_stats.png)
```
dfxtp_4 = 1613,
Number of cells = 18036,
Flop ratio = 8.94%
```
- Seeing results in `picorv32a.synthesis.v`

![synthesis results](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day1/synthesis_result_v.png)
 
- Seeing synthesis reports

![synthesis report](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day1/synthesis_result_report.png)

- This concludes day 1

## Day 2
### Topic 1: Steps to run floorplan using OpenLANE
- Generating floorplan

![run floorplan](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day2/run_floorplan.png)

### Topic 2: Review floorplan files and steps to view floorplan
- Reviewing in magic
`magic -T /usr/local/tools/OpenLane/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &`

![magic](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day2/magic.png)

### Topic 3: Review floorplan layout in Magic
- Zooming in

![zoom in](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day2/zoom_in.png)

![very zoomed in](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day2/very_zoomed_in.png)

![what](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day2/what.png)

### Topic 4: Congestion aware placement using RePlAce
- `picorv32a.placement.def.png`

![placement](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day2/picorv32a.placement.def.png)

- opening in `magic`

![magic placement](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day2/magic_placement.png)

- Zooming in

![magic placement zoom](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day2/magic_placement_zoom.png)

- This concludes day 2

## Day 3
### Topic 1: I/O Placer Revision
- Original output

![1](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/1.png)

- `floorplan.tcl`

![2](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/2.png)

- Modifying

![3](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/3.png)

- Final I/O structure

![4](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/4.png)

### Topic 2: VSD Std Cell Design
- `git clone`

![5](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/5.png)

- Copying `sky130A.tech`

![6](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/6.png)

- Running `magic -T sky130A.tech sky130_inv.mag`

![7](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/7.png)

### Topic 3: Sky130 basic layers layout and LEF
- CMOS layout

![7](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/7.png)

- `what` command 

![8](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/8.png)

### Topic 4: Create std cell layout and extract SPICE netlist

- Running commands to extract along with arasitic capacitances

![9](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/9.png)

- Result `sky130_inv.spice` and it's contents

![10](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/10.png)

![11](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/11.png)

### Topic 5: Create Final SPICE Deck

- Find min value of layout window

![12](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/12.png)

- Editing `sky130_inv.spice`

![13](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/13.png)

### Topic 6: Using Sky130 Models to characterise inverter
- Running file using `ngspice`

![14](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/14.png)

- `plot y vs time a` 

![15](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/15.png)

- Finding Rise time

![16](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/16.png)

```
2.25075 * 10^-09 - 2.184 * 10^ -09 = 0.006675 * 10^-09s
```

- Finding Propagation delay

![17](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/17.png)

```
2.21379 * 10^-09 - 2.15 * 10^-09 = 0.06379 * 10^-09s
```

### Topic 7: Downloading DRC tests
- Download via `wget` and extract it on `Desktop`
- Running the DRC tests in `magic` with `magic -d XR`

![18](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/18.png)

- Opening `met3.mag`

![19](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/19.png)

- Seeing error after entering `why`

![20](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/20.png)

- Making edits to `sky130A.tech`

![21](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/21.png)

- Reloading 

![22](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/22.png)

- Error fixed


### Topic 8: DRC as geometrical construct
- Opening `nwell.mag` and typing the following

![23](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/23.png)

- Result:

![24](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/24.png)

### Topic 9: Find Missing/Incorrect rules

- Violation of `nwell.4`

![25](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/25.png)

- We make the following changes:

![26](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/26.png)

- Reload using 
```
tech load sky130A.tech
drc check
drc style drc(full)
drc check
```

- Error still exists, we fix it by making a copy of it and adding an `nsubstratecontact` in it

![27](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day3/27.png)

- This wraps up Day 3

