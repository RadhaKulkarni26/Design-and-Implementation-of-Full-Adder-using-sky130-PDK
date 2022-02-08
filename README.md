# DESIGN AND IMPLEMENTATION OF FULL ADDER USING CMOS AND SKY130nm PDK

- The purpose of this project is to design a CMOS FULL ADDER using an Opensource EDA Tool called **eSim**, an Opensource Spice Simulator called **ngspice** and **Sky130 PDK**.
- To explore the project, you can git clone using the command:

## Table of Contents:

1. INTRODUCTION
2. INSTALLATION OF TOOLS
3. CIRCUIT DESIGN
   1. REFERENCE CIRCUIT DIAGRAM
   2. REFERENCE CIRCUIT WAVEFORM
5. IMPLEMENTATION
6. REFERENCE

### 1. INTRODUCTION
***
In this project, I am going to Design and Implement **FULL ADDER** using **CMOS** Technology and I will also implement it using sky130nm technology. Design and Implementation will be done using esim and ngspice software. Full Adder is the digital circuit which will add 3 inputs and give 2 outputs. 3 inputs are A, B, C and outputs are SUM, CARRY. Full Adder will do binary addition of A, B and C and will give the sum of 3 inputs at SUM output and carry bit at CARRY output.We can verify the output using Circuit Waveforms. This complete design and implementation is done using VLSI technology which has features such as high speed, low power, low cost, and small size.

### 2. INSTALLATION OF TOOLS
***
#### esim:
esim is an open-source EDA tool used for circuit design and simulation. Using esim we can draw circuit using Kicad, generate netlist and simulate using Ngspice.

For more information: <https://esim.fossee.in/home>

#### Ngspice:

ngspice is the open-source spice simulator for electric and electronic circuits. We can design circuits using JFET, MOSFET and passive elements like resistors, capacitors, etc.

For more information: <http://ngspice.sourceforge.net>

#### Sky130nm PDK:

The SkyWater Open Source PDK is a collaboration between Google and SkyWater Technology Foundry to provide a fully open source Process Design Kit and related resources, which can be used to create manufacturable designs at SkyWater’s facility. 

For more information: <https://www.layouteditor.org/schematiceditor/libraries/skywater>

The Download links for above software are:

#### esim: <https://esim.fossee.in/downloads>

#### Ngspice: <https://sourceforge.net/projects/ngspice/files/>

#### Sky130 pdk: <https://static.fossee.in/esim/installation-files/sky130_fd_pr.zip>

Follow these steps for Sky130 download and implementaion:

1. Download sky130 from this link mentioned above and unzip it.
1. Save the .cir.out file in the sky\_fd\_pr folder as .cir file.
1. Open with notepad and add the path .lib "models/sky130.lib.spice" tt at the top.
1. Replace with CMOSP, mos\_p with sky130\_fd\_pr\_pfet\_01v8 and CMOSN, mos\_n with  sky130\_fd\_pr\_nfet\_01v8.
1. To replace inductor, capacitor, resistor do it this way, for Ex: L1 out gnd 1m by x1 out gnd mid 0 sky130\_fd\_pr\_\_ind\_03\_90.

**Note**: For more details go to the cells folder in sky\_fd\_pr. 

Open the specific component folder which you want to use. 

Then open the test folder and check the SPICE file. 

The SPICE file is an example of implementation of that component. 

You will get to know how to use the component in your ckt.

6. Now Run the circuit with ngspice.

To Run the ckt using ngspice:

1. Right click on .cir file.
1. Click on Open With.
1. Browse for the ngspice.
1. If ngspice not present scroll down click on More Apps.
1. Go to the FOSSEE folder search for Ngspice and Run it.

### 3. CIRCUIT DESIGN
***
**Full Adder** is a digital circuit which will add 3 binary inputs and will give 2 outputs namely SUM and CARRY. The 3 inputs are **A**, **B** and **C** and outputs are **SUM** and **CARRY**. As we have 3 inputs we will have 8 input combinations.Using circuit design rules of CMOS we will design the circuit in such a way that addition of 3 inputs will occur at SUM output and carry bit will occur at CARRY output. While designing we have used total 28 Transistors. Full Adder using CMOS will be designed using 2 parts: PMOS (pull-up lattice) and NMOS (pull-down lattice). PMOS circuit is connected to supply voltage VDD and NMOS circuit is connected to ground GND. We will implement this circuit design using sky130nm technology. In the Circuit Waveform, we will verify the above implementation using clock pulse. In the output we will give different input combinations through clock pulse and verify the logic using output waveform.  

#### 3.1 REFERENCE CIRCUIT DIAGRAM
 ![REFERENCE CIRCUIT DIAGRAM](https://user-images.githubusercontent.com/70748543/153016545-9eca42e3-a254-4818-99a4-39dbcf2b68fb.JPG)

#### 3.2 REFERENCE CIRCUIT WAVEFORM
  ![REFERENCE CIRCUIT WAVEFORM](https://user-images.githubusercontent.com/70748543/153016656-df479e54-79e6-4a44-ba70-74592c8729ff.JPG)

### 4. IMPLEMENTATION
***
Now, we will design the complete circuit using our reference circuit diagram with PMOS logic above and NMOS logic below.
After connecting the complete we will get a circuit like below:
![Final_Circuit_Diagram](https://user-images.githubusercontent.com/70748543/152938780-5d35f5c6-ad03-450e-9fd5-9a3d242ffc69.JPG)


Label each and every component and port and check electrical rule checking and generate netlist file using spice and make changes in netlist to add sky130 models.
**The netlist generated initially is as shown below:**

* C:\SPB_Data\eSim-Workspace\Full_Adder\abc.cir

* EESchema Netlist Version 1.1 (Spice format) creation date: 2/8/2022 1:04:47 PM

* To exclude a component from the Spice Netlist add [Spice_Netlist_Enabled] user FIELD set to: N
* To reorder the component spice node sequence add [Spice_Node_Sequence] user FIELD and define sequence: 2,1,0

* Sheet Name: /
M1  /vdd /vin_a Net-_M1-Pad3_ /vdd mosfet_p		

M2  /vdd /vin_a Net-_M2-Pad3_ /vdd mosfet_p		

M3  /vdd /vin_b Net-_M2-Pad3_ /vdd mosfet_p		

M4  /vdd /vin_c Net-_M4-Pad3_ /vdd mosfet_p		

M5  /vdd /vin_a Net-_M4-Pad3_ /vdd mosfet_p		

M6  /vdd /vin_b Net-_M4-Pad3_ /vdd mosfet_p		

M7  Net-_M1-Pad3_ /vin_b Net-_M14-Pad2_ /vdd mosfet_p		

M8  Net-_M2-Pad3_ /vin_c Net-_M14-Pad2_ /vdd mosfet_p		

M9  Net-_M4-Pad3_ Net-_M14-Pad2_ Net-_M12-Pad3_ /vdd mosfet_p		

M10  /vdd /vin_a Net-_M10-Pad3_ /vdd mosfet_p		

M11  Net-_M10-Pad3_ /vin_b Net-_M11-Pad3_ /vdd mosfet_p		

M12  Net-_M11-Pad3_ /vin_c Net-_M12-Pad3_ /vdd mosfet_p		

M13  /vdd Net-_M12-Pad3_ /sum /vdd mosfet_p		

M28  /sum Net-_M12-Pad3_ GND GND mosfet_n		

M21  Net-_M14-Pad2_ /vin_b Net-_M15-Pad1_ GND mosfet_n		

M15  Net-_M15-Pad1_ /vin_a GND GND mosfet_n		

M16  Net-_M16-Pad1_ /vin_a GND GND mosfet_n		

M17  Net-_M16-Pad1_ /vin_a GND GND mosfet_n		

M18  Net-_M18-Pad1_ /vin_c GND GND mosfet_n		

M22  Net-_M14-Pad2_ /vin_c Net-_M16-Pad1_ GND mosfet_n		

M19  Net-_M18-Pad1_ /vin_a GND GND mosfet_n		

M23  Net-_M12-Pad3_ Net-_M14-Pad2_ Net-_M18-Pad1_ GND mosfet_n		

M20  Net-_M18-Pad1_ /vin_b GND GND mosfet_n		

M26  Net-_M12-Pad3_ /vin_c Net-_M25-Pad1_ GND mosfet_n		

M25  Net-_M25-Pad1_ /vin_b Net-_M24-Pad1_ GND mosfet_n		

M24  Net-_M24-Pad1_ /vin_a GND GND mosfet_n		

M27  /carry Net-_M14-Pad2_ GND GND mosfet_n		

M14  /vdd Net-_M14-Pad2_ /carry /vdd mosfet_p		

U1  /vdd /vin_a /vin_b /vin_c /sum /carry PORT		

.end

**The netlist after making sky130 models syntax changes is as shown below:**

* c:\spb_data\esim-workspace\full_adder\full_adder.cir

.lib "sky130_fd_pr/models/sky130.lib.spice" tt


xM1  vdd vin_a Net-_M1-Pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM7  Net-_M1-Pad3_ vin_b Net-_M14-Pad2_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM2  vdd vin_a Net-_M2-Pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM3  vdd vin_b Net-_M2-Pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM8  Net-_M2-Pad3_ vin_c Net-_M14-Pad2_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM4  vdd vin_c Net-_M4-Pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM5  vdd vin_a Net-_M4-Pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM6  vdd vin_b Net-_M4-Pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM9  Net-_M4-Pad3_ Net-_M14-Pad2_ Net-_M12-Pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM21  Net-_M14-Pad2_ vin_b Net-_M15-Pad1_ GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM15  Net-_M15-Pad1_ vin_a GND GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM22  Net-_M14-Pad2_ vin_c Net-_M16-Pad1_ GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM16  Net-_M16-Pad1_ vin_a GND GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM17  Net-_M16-Pad1_ vin_b GND GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM23  Net-_M12-Pad3_ Net-_M14-Pad2_ Net-_M18-Pad1_ GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM18  Net-_M18-Pad1_ vin_c GND GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM19  Net-_M18-Pad1_ vin_a GND GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM20  Net-_M18-Pad1_ vin_b GND GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM10  vdd vin_a Net-_M10-Pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM11  Net-_M10-Pad3_ vin_b Net-_M11-Pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM12  Net-_M11-Pad3_ vin_c Net-_M12-Pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM26  Net-_M12-Pad3_ vin_c Net-_M25-Pad1_ GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM25  Net-_M25-Pad1_ vin_b Net-_M24-Pad1_ GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM24  Net-_M24-Pad1_ vin_a GND GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM13  vdd Net-_M12-Pad3_ sum vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5		

xM28  sum Net-_M12-Pad3_ GND GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

xM14  vdd Net-_M14-Pad2_ carry vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5			

xM27  carry Net-_M14-Pad2_ GND GND sky130_fd_pr__nfet_01v8 w=0.42 l=0.5		

Vdd vdd 0 3.3

Vd0 vin_a 0 pulse(0 2.2 0us 0s 0s 20us 40us)

Vd1 vin_b 0 pulse(0 2.2 5us 0s 0s 20us 40us)

Vd2 vin_c 0 pulse(0 2.2 15us 0s 0s 20us 40us)

.tran 0.1us 60us

.control

run

plot V(carry) V(sum) +4 V(vin_c) +8  V(vin_b) +12 V(vin_a)+15

.endc

.end

**Note**: sky130\_fr\_pd file for sky130 model must be present on the same file as .cir.out.

**Truth Table for 2:1 mux using CMOS is as shown below**:

![TRUTH TABLE](https://user-images.githubusercontent.com/70748543/153016747-748084fa-245e-4885-a1bd-6e74ccbbd64d.JPG)

Now, run the .cir.out file using ngspice and we will get the circuit waveforms as follows:
![Final_Circuit_Waveform](https://user-images.githubusercontent.com/70748543/152938841-1d850fcf-14c9-4f08-96b1-8ddc50119328.JPG)

From the above waveform we can verify the truth table for Full Adder using CMOS. 

### 5. REFERENCES:
***
[1]N. Zhuang and H. Wu, "A new design of the CMOS full adder," IEEE Journal of Solid-State Circuits, vol. 27, No. 5, pp. 840-844, May 1992.

[2]N. H. E. Weste and K. Eshraghian, "Principles of CMOS VLSI design," Addison Wesley, 1993.
