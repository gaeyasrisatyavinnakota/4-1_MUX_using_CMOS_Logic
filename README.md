# 4:1 MUX using CMOS Logic
The purpose of this Hackathon is to implement the proposed design in 28 nm PDK (Process Design Kit) using CMOS technology. After doing the literature survey the [Initial report](https://github.com/gaeyasrisatyavinnakota/4to1_MUX_using_CMOS_Logic/blob/main/GAEYA%20SRI%20SATYA%20VINNAKOTA_INITIAL%20REPORT_ACBDH.pdf) was submitted. The design was implemanted and this is the final Report Submission for successful completion of Design of 4:1 MUX using CMOS Logic and implemenatation along with simulation, for [Cloud Based Analog IC Design Hackathon](https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/)
## Table of Contents
1. [Abstract](#abstract)
2. [Details of the Circuit](#details-of-the-circuit)
3. [Working of the Circuit](#working-of-the-circuit)
4. [Implemented Design](#implemented-design)
5. [Output Waveforms](#output-waveforms)
6. [Schematic Netlist](#schematic-netlist)
7. [Challenges and Limitations](#challenges-and-limitations)
8. [References](#references)
9. [Acknowledgements](#acknowledgements)
10. [Author](#author)
## Abstract
This report describes the design and Implementation of 4:1 Multiplexer using CMOS logic using the Cloud-based [Synopsys](https://www.synopsys.com/) [Custom Compiler](https://www.synopsys.com/implementation-and-signoff/custom-design-platform/custom-compiler.html) tool and the [Primewave](https://www.synopsys.com/implementation-and-signoff/ams-simulation/primewave.html) tool at the 28nm CMOS technology node. Multiplexer circuit selects 1 output data line from multiple input data lines with the help of input select lines. This design discussed in the report uses 4 input data lines and 2 input select lines to get the 1 output data line.

## Details of the Circuit
A Multiplexer circuit, shortly called MUX, is used to select a data line as output from multiple input data lines by using input select lines. To get an output data line from N input data lines that is N:1 MUX, we require log<sub>2</sub><sup>N</sup> select lines.
The representation of 4:1 MUX is as shown below in Figure(1)
<figure>
<p align="center"><img src="https://github.com/gaeyasrisatyavinnakota/4to1_MUX_using_CMOS_Logic/blob/main/Images/mux_symbol.png" width="300" height ="300"></p>
<figcaption><p align = "center">Figure(1) 4:1 MUX Representation</p></figcaption>
</figure>

The truth table of the 4:1 MUX is as shown,

<table align="center">
  <tr>
    <th>S<sub>0</sub></th>
    <th>S<sub>1</sub></th>
    <th>Out</th>
  </tr>
  <tr>
    <td>0</td>
    <td>0</td>
    <td>D</td>
  </tr>
  <tr>
    <td>0</td>
    <td>1</td>
    <td>C</td>
  </tr>
   <tr>
    <td>1</td>
    <td>0</td>
    <td>B</td>
  </tr>
  <tr>
    <td>1</td>
    <td>1</td>
    <td>A</td>
  </tr>
</table>
<!---
| S<sub>0</sub> | S<sub>1</sub> | Out |
|    :----:   |    :----:   |    :----:   |
|0|0|D|
|0|1|C|
|1|0|B|
|1|1|A|
--->
The reference circuit is as shown below in Figure(2)
<figure>
<p align="center"><img src="https://github.com/gaeyasrisatyavinnakota/4to1_MUX_using_CMOS_Logic/blob/main/Images/cir_img.png" width="600" height ="500"></p>
<figcaption><p align = "center">Figure(2) Reference Circuit</p></figcaption>
</figure>

As per the reference circuit, the 4:1 MUX is designed using CMOS logic and both the Pull-up (made of the PMOS) and pull-down (made of the NMOS) networks pull the output to the input data lines, and the input select lines are given to the MOSFETs' gates.

## Working of the Circuit

- When both the select lines are logic 0, NMOS in the pull-down network and PMOS  in the pull-up network of D input line becomes shoert circuited and pull-up and pull-down networks of all other input lines becomes open circuit and the output becomes the D input line.
- When select lines 0 is logic 0 and select line 1 is logic 1, NMOS in the pull-down network and PMOS  in the pull-up network of C input line becomes shoert circuited and pull-up and pull-down networks of all other input lines becomes open circuit and the output becomes the C input line.
- When select lines 0 is logic 1 and select line 1 is logic 0, NMOS in the pull-down network and PMOS  in the pull-up network of B input line becomes shoert circuited and pull-up and pull-down networks of all other input lines becomes open circuit and the output becomes the B input line.
- When both the select lines are logic 1, NMOS in the pull-down network and PMOS  in the pull-up network of A input line becomes shoert circuited and pull-up and pull-down networks of all other input lines becomes open circuit and the output becomes the A input line.

## Implemented Design

By opening the lab instance then creating a  new folder and opening it in terminal we have to create a lib.def file and load the PDK into it. Then we have to access the server and launch the Synopsys custom compiler tool. After that by opening and creating a library and a new cell in it and a schematic view for it we have to implement the design and then Check and Save the design. 

The schematic of the implemented design is as shown below in Figure(3)
<figure>
<p align="center"><img src="https://github.com/gaeyasrisatyavinnakota/4to1_MUX_using_CMOS_Logic/blob/main/Images/Schematic%20of%20Design.png" width="700" height ="600"></p>
<figcaption><p align = "center">Figure(3) Implemented Circuit Schematic</p></figcaption>
</figure>

After that we have to create a symbol view for the above schematic view and then Check and Save it.  

The symbol of the implemented design is as shown below in Figure(4)
<figure>
<p align="center"><img src="https://github.com/gaeyasrisatyavinnakota/4to1_MUX_using_CMOS_Logic/blob/main/Images/cir_imp_sym.png" width="300" height ="400"></p>
<figcaption><p align = "center">Figure(4) Implemented Circuit Symbol</p></figcaption>
</figure>

After creating the symbol view create another cell in the library fro testbench and create the schematic view and then Check and Save it. 

The schematic of the testbench of the design is as shown below in Figure(5)
<figure>
<p align="center"><img src="https://github.com/gaeyasrisatyavinnakota/4to1_MUX_using_CMOS_Logic/blob/main/Images/tb_imp_sch.png" width="900" height ="700"></p>
<figcaption><p align = "center">Figure(5) Implemented Testbench Circuit Schematic</p></figcaption>
</figure>

## Output Waveforms

For simulation purpose we have to iniate the primewave tool and give model files, mode of analysis and select the parameters from the schematic to be observed under waveview. Then save the state and generate a Netlist and Run the simulation. 

The output waveforms obtained after the simulation are as shown below in Figure(6)
<figure>
<p align="center"><img src="https://github.com/gaeyasrisatyavinnakota/4to1_MUX_using_CMOS_Logic/blob/main/Images/op_waveform.png" width="1000" height ="300"></p>
<figcaption><p align = "center">Figure(5) Implemented Testbench Circuit Schematic</p></figcaption>
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
## Challenges and limitations
- The main challange is to have less rise time, fall time and propagation delay for the input.
- Another big challenge is to calculate the W/L ratio
- The same logic can be implemented using only 8 MOSFETs either NMOS or PMOS at same technology node but by using the CMOS we can have high propagation speed but the complexity of the design increases.

## References
[1]. [Multiplexer Wikipedia](https://en.wikipedia.org/wiki/Multiplexer)

[2]. [Combinational Circuits Electronics Tutorials](https://www.electronicstutorials.ws/combination/comb_2.html)

[3]. [CMOS Logic Electronics Turoials](https://www.electronics-tutorial.net/Digital-CMOSDesign/Pass-Transistor-Logic/4-1-multiplexer-using-CMOSlogic/)

## Acknowledgements
- [Synopsys](https://www.synopsys.com/)
- [IIT Hyderabad](https://iith.ac.in/)
- [Analog Cloud Based Hackathon](https://hackathoniith.in/)
- [VLSI System Design](https://www.vlsisystemdesign.com/)
- [Kunal Ghosh](https://www.linkedin.com/in/kunal-ghosh-vlsisystemdesign-com-28084836/)
- [Chinmaya Panda](https://ee.iith.ac.in/images/staff/panda.jpeg)
- [Sumanto Kar](https://www.linkedin.com/in/sumanto-kar-0424391a9/)
- [Sameer Durgoji](https://www.linkedin.com/in/sameer-s-durgoji-340b26180/)
## Author
[Gaeya Sri Satya Vinnakota](https://www.linkedin.com/in/vgss/), BTech III year, Electronics Engineering Department, [Sardar Vallabhbhai National Institute Of Technology](https://www.svnit.ac.in/)
