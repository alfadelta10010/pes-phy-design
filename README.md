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
![run floorplan]()

### Topic 2: Review floorplan files and steps to view floorplan
- Reviewing in magic
`magic -T /usr/local/tools/OpenLane/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &`

![magic]()

### Topic 3: Review floorplan layout in Magic
- Zooming in
![zoom in]()

![zoomed in]()

![very zoomed in]()

![what]()

### Topic 4: Congestion aware placement using RePlAce
- `picorv32a.placement.def.png`
![placement]()

- opening in `magic`
![magic placement]()

- Zooming in
![magic placement]()
