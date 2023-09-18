# Physical Design

:warning: Note: After Day 2, I switched to the VM Image provided by VSD


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


## Day 4
### Topic 1: Convert Grid Info to Track Info

- Taking a look at the `tracks.info` file

![1](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/1.png)

- The 'tracks.info' file is used during the routing stage.
- Routes are the metal traces.
- 1st value indicates the offset and 2nd value indicates the pitch along provided direction

![2](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/2.png)


- Now we converge the grid definition in the layout to track definition, by typing the following command
```grid 0.46um 0.34um 0.23um 0.17um```

- The result is as follows.

![3](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/3.png)


### Topic 2: Convert Magic Layout to Standard Cell LEF
- To make our own .mag file, we type
```
save sky130_vsdinv.mag
```
- To make the .lef file we type
```
lef write
```

- Type ```cat sky130_vsdinv.lef```.

![4](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/4.png)

### Topic 3: Include New Cell in Synthesis
- We copy the .lef file that we created to the 'src' folder of picorv32a folder
```bash 
cp sky130_vsdinv.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/deigns/picorv32a/src
cp sky130_fd_sc_hd__* /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/deigns/picorv32a/src
```
- Modifying the 'config.tcl' 

![5](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/5.png)

- Open the OpenLANE interactive window and run the following:
```
package require openlane 0.9
prep -design picorv32a -tag 16-09_19-58 -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs 
run_synthesis
```
- Result of ```run_synthesis```

![6](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/6.png)
![7](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/7.png)

- To run floorplan and placement we type
```
init_floorplan
run_placement
```
- Now to view the design we type the command
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
- The following output is generated
![8](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/8.png)

- Zoom in to find `sky130_vsdinv`
![9](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/9.png)


### Topic 4: Configure OpenSTA for Post-Synth Timing Analysis

- Create 'pre_sta.conf' in openlane directory with the following:
```configuration
set_cmd_units -time n -capacitance pF -current mA -voltage V -resistance kOhm -distance um
read_liberty -max /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/sky130/sky130_fd_sc_hd__slow.lib
read_liberty -min /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/sky130/sky130_fd_sc_hd__fast.lib
read_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/18-09_04-29/results/synthesis/picorv32a.synthesis.v
link_design picorv32a
read_sdc /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/my_base.sdc
report_checks -path_delay min_max -fields {slew trans net cap input_pin}
report_tns
report_wns
```
- Create `my_base.sdc` in `openlane/designs/picorv32a/src/` with the following contents
```
set ::env(CLOCK_PORT) clk
set ::env(CLOCK_PERIOD) 12.000

set ::env(SYNTH_DRIVING_CELL) sky130_fd_sc_hd__inv_8
set ::env(SYNTH_DRIVING_CELL_PIN) Y
set ::env(SYNTH_CAP_LOAD) 17.65
set ::env(SYNTH_MAX_FANOUT) 4

create_clock [get_ports $::env(CLOCK_PORT)]  -name $::env(CLOCK_PORT)  -periof $::env(CLOCK_PERIOD)
set IO_PCT 0.2
set input_delay_value [expr $::env(CLOCK_PERIOD) * $IO_PCT]
set output_delay_value [expr $::env(CLOCK_PERIOD) * $IO_PCT]
puts "\[INFO\]: Setting output delay to $output_delay_value"
puts "\[INFO\]: Setting input delay to $input_delay_value"

set_max_fanout $::env(SYNTH_MAX_FANOUT) [current_design]

set clk_indx [lsearch [all_inputs] [get_port $::env(CLOCK_PORT)]]
#set rst_indx [lsearch [all_inputs] [get_port resetn]]
set all_inputs_wo_clk [lreplace [all_inputs] $clk_indx $clk_indx]  
#all_inputs_wo_clk_rst [lreplace $all_inputs_wo_clk $rst_indx $rst_indx] 
set all_inputs_wo_clk_rst $all_inputs_wo_clk 

#correct resetn
set_input_delay $input_deleat_value -clock [get_clocks $::env(CLOCK_PORT)] $all_inputs_wo_clk_rst
set_output_delay $output_delay_value  -clock [get_clocks $::env(CLOCK_PORT)] [all_outputs]

#TODO set this as parameter
set_drivinf_cell -lib_cell $::env(SYNTH_DRIVING_CELL) -pin $::env(SYNTH_DRIVING_CELL_PIN) [all_inputs]
set cap_load [expr $::env(SYNTH_CAP_LOAD) / 1000.0]
puts "\[INFO\]: Setting load to: $cap_load"
set_load $cap_load [all_outputs]
```

- To run the timing analysis:
```
sta pre_sta.conf
```

- The result is displayed, and we can see there is a slack violation

![10](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/10.png)

- Setting MAX_FANOUT value to 4 with `set ::env(SYNTH_MAX_FANOUT) 4` fixes the issue.

### Topic 5: Run CTS
- To run CTS we type:
```
run_cts
```
- A new verilog file is created
![11](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/11.png)

### Topic 6: Timing Analysis using OpenSTA
- Run ```openroad```

![12](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/12.png)

- Read the .lef file using the command
```
read_lef /openLANE_flow/designs/picorv32a/runs/18-09_04-29/tmp/merged.lef
```
- Then we read the .def file.
```
read_def /openLANE_flow/designs/picorv32a/runs/18-09_04-29/results/cts/picorv32a.cts.def
```
- We then execute the following when the 
```
write_db pico_cts.db
read_db pico_cts.db
read_verilog /openLANE_flow/designs/picorv32a/runs/18-09_04-29/results/synthesis/picorv32a.synthesis_cts.v
read_liberty -max $::env(LIB_SLOWEST)
read_liberty -max $::env(LIB_FASTEST)
```
- We read the .src file.
```
read_sdc /openLANE_flow/designs/picorv32a/src/sky130/my_base.sdc
```
![13](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/13.png)

- We set the clock
```
set_propagated_clock [all_clocks]
```
- Checking the report
```
report_checks -path_delay min_max -format full_clock_expanded -digits 4
```
- The following results are displayed
![14](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/14.png)
![15](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/15.png)


- To improve result accuracy, we run the simulation again. The following results are displayed

![16](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/16.png)
![17](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/17.png)

- To see the hold and setup time
```
report clock_skew -hold
report clock_skew -setup
```
![18](https://github.com/alfadelta10010/pes-phy-design/blob/master/assets/day4/18.png)

- That concludes day 4

## Day 5
### Topic 1: Build Power Distribution Network
