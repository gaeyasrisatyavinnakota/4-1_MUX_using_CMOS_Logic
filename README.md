# 4:1 MUX using CMOS Logic
The purpose of this Hackathon is to implement the proposed design in 28 nm PDK (Process Design Kit) using CMOS technology. After doing the literature survey the [Initial report](https://github.com/gaeyasrisatyavinnakota/4to1_MUX_using_CMOS_Logic/blob/main/GAEYA%20SRI%20SATYA%20VINNAKOTA_INITIAL%20REPORT_ACBDH.pdf) was submitted. The design was implemanted and this is the final Report Submission for successful completion of 4:1 MUX using CMOS Logic design and simulation, for [Cloud Based Analog IC Design Hackathon](https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/)
## Table of Contents
1. [Abstract](#abstract)
2. [Implemented Circuit details](#implemented-circuit-details)
3. 
## Abstract
This report describes the design and Implementation of 4:1 Multiplexer using CMOS logic using the Cloud-based [Synopsys](https://www.synopsys.com/) [Custom Compiler](https://www.synopsys.com/implementation-and-signoff/custom-design-platform/custom-compiler.html) tool and the [Primewave](https://www.synopsys.com/implementation-and-signoff/ams-simulation/primewave.html) tool at the 28nm CMOS technology node. Multiplexer circuit selects 1 output data line from multiple input data lines with the help of input select lines. This design discussed in the report uses 4 input data lines and 2 input select lines to get the 1 output data line.

## Implemented Circuit Details
A Multiplexer circuit, shortly called MUX, is used to select a data line as output from multiple input data lines by using input select lines. To get an output data line from N input data lines that is N:1 MUX, we require log<sub>2</sub><sup>N</sup> select lines.
The representation of 4:1 MUX is as shown below 
<figure>
<p align="center"><img src="https://github.com/gaeyasrisatyavinnakota/4to1_MUX_using_CMOS_Logic/blob/main/Images/mux_symbol.png" width="300" height ="300"></p>
<figcaption><p align = "center">4:1 MUX Representation</p></figcaption>
</figure>

The truth table of the 4:1 MUX is as shown,

| S<sub>0</sub> | S<sub>1</sub> | Out |
|    :----:   |    :----:   |    :----:   |
|0|0|D|
|0|1|C|
|1|0|B|
|1|1|A|

The reference circuit is as shown below
<figure>
<p align="center"><img src="https://github.com/gaeyasrisatyavinnakota/4to1_MUX_using_CMOS_Logic/blob/main/Images/cir_img.png" width="600" height ="500"></p>
<figcaption><p align = "center">Reference Circuit</p></figcaption>
</figure>

## Schematic Netlist

The final Netlist is as follows:
```
*  Generated for: PrimeSim
*  Design library name: cir_lib_1
*  Design cell name: cir_cell_1_tb
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Tue Mar  1 14:38:15 2022

.global gnd! vdd!
********************************************************************************
* Library          : cir_lib_1
* Cell             : cir_cell_1
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt cir_cell_1 a b c d s1 s1_bar s2 s2_bar out vt_bulk_n_gnd! vt_bulk_p_vdd!
xm8 out s2_bar net27 vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm7 net27 s1_bar d vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm6 net19 s1_bar c vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm5 out s2_bar net18 vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm3 out s2 net19 vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm2 net18 s1 b vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm1 out s2 net56 vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm0 net56 s1 a vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm17 net54 s2_bar out vt_bulk_p_vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm16 a s1_bar net54 vt_bulk_p_vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm15 net48 s2 out vt_bulk_p_vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm14 b s1_bar net48 vt_bulk_p_vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm13 net42 s2_bar out vt_bulk_p_vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm11 c s1 net42 vt_bulk_p_vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm10 d s1 net31 vt_bulk_p_vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm9 net31 s2 out vt_bulk_p_vdd! p105 w=0.1u l=0.03u nf=1 m=1
.ends cir_cell_1

********************************************************************************
* Library          : cir_lib_1
* Cell             : cir_cell_1_tb
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xi0 a_in b_in c_in d_in s1_select_in s1_bar s2_select_in s2_bar output gnd! vdd!
+  cir_cell_1
v23 b_in gnd! dc=0 pulse ( 0.8 0 0 0.001 0.001 2 4 )
v22 a_in gnd! dc=0 pulse ( 0.8 0 0 0.001 0.001 1 2 )
v24 c_in gnd! dc=0 pulse ( 0.8 0 0 0.001 0.001 4 8 )
v31 s2_select_in gnd! dc=0 pulse ( 0.8 0 0 0.001 0.001 2 4 )
v30 s2_bar gnd! dc=0 pulse ( 0 0.8 0 0.001 0.001 2 4 )
v29 s1_bar gnd! dc=0 pulse ( 0 0.8 0 0.001 0.001 1 2 )
v28 s1_select_in gnd! dc=0 pulse ( 0.8 0 0 0.001 0.001 1 2 )
v27 d_in gnd! dc=0 pulse ( 0.8 0 0 0.001 0.001 8 16 )
c33 output gnd! c=1p








.tran '0.1' '20' name=tran

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran v(a_in) v(b_in) v(c_in) v(d_in) v(s1_bar) v(s1_select_in) v(s2_bar)
+ v(s2_select_in) v(output)

.temp 25



.option primesim_output=wdf


.option parhier = LOCAL






.end
```
