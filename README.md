# DESIGN AND IMPLEMENTATION OF FULL ADDER USING CMOS AND SKY130nm PDK

- The purpose of this project is to design a CMOS FULL ADDER using an Opensource EDA Tool called eSim, an Opensource Spice Simulator called ngspice and Sky130 PDK.
- To explore the project, you can git clone using the command:

## Table of Contents:

1. INTRODUCTION
2. INSTALLATION OF TOOLS
3. CIRCUIT DESIGN
   3.1 REFERENCE CIRCUIT DIAGRAM
   3.2 REFERENCE CIRCUIT WAVEFORM
5. IMPLEMENTATION
6. REFERENCE

### 1. INTRODUCTION
***
In this project, I am going to Design and Implement 2:1 Mux using CMOS Technology and I will also implement it using sky130nm technology. Design and Implementation will be done using esim and ngspice software. MUX is a data selector which will give single output from several data inputs. Here we have implemented 2 input MUX which will give single output based on select line input. We can verify the output using Circuit Waveforms. This complete design and implementation is done using VLSI technology which has features such as high speed, low power, low cost, and small size.

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

Note: For more details go to the cells folder in sky\_fd\_pr. 

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
Multiplexer (MUX) is a data selector which will send single input data at the output based on select line input. Here we have implemented a 2:1 MUX which has 2 inputs (A and B), 1 output (Y) and 1 select line (S). Output Y will be A or B based on 0 or 1 input at the select line (S). If the select line is “0” output Y will be A and if the select line is “1” then output Y will be B. 2:1 MUX using CMOS will be designed using 2 parts: PMOS (pull-up lattice) and NMOS (pull-down lattice). PMOS circuit is connected to supply voltage VDD and NMOS circuit is connected to ground GND. The equation for output Y will be Y=ASbar + BS. According to circuit design rules, ASbar and BS will be connected in parallel in PMOS lattice and it will be connected in series in NMOS lattice. We know that the output of CMOS is always inverted so we have to connect the CMOS inverter circuit at the output. We will implement this circuit design using sky130nm technology. In the Circuit Waveform, we will verify the above implementation using clock pulse. Output Y will have the same clock pulse sequence as A when S will be “0” and it will have the same clock pulse sequence as B when S will be “1”.

#### 3.1 REFERENCE CIRCUIT DIAGRAM
   ![Circuit Diagram](https://user-images.githubusercontent.com/70748543/152833395-2d779dae-919e-42cd-81ac-cc3ae9fc8605.jpeg)


#### 3.2 REFERENCE CIRCUIT WAVEFORM
  ![WAVEFORM](https://user-images.githubusercontent.com/70748543/152833636-cecae839-963c-4a8b-b394-7ff5b986865a.jpeg)
  

### 4. IMPLEMENTATION
***
Now, we will design the complete circuit using our reference circuit diagram with PMOS logic above and NMOS logic below.
After connecting the complete we will get a circuit like below:
![Final_Circuit_Diagram](https://user-images.githubusercontent.com/70748543/152843684-22f57b96-daed-460d-8f5f-b8d0b6491dd8.JPG)


Label each and every component and port and check electrical rule checking and generate netlist file using spice and make changes in netlist to add sky130 models.
**The netlist generated initially is as shown below:**

\* C:\SPB\_Data\eSim-Workspace\Multiplexer\multiplexer.cir

\* EESchema Netlist Version 1.1 (Spice format) creation date: 2/7/2022 9:25:01 PM

\* To exclude a component from the Spice Netlist add [Spice\_Netlist\_Enabled] user FIELD set to: N

\* To reorder the component spice node sequence add [Spice\_Node\_Sequence] user FIELD and define sequence: 2,1,0

\* Sheet Name: /

M2  Net-\_M2-Pad1\_ /vin\_1 /vdd /vdd mosfet\_p		

M3  Net-\_M2-Pad1\_ Net-\_M1-Pad1\_ /vdd /vdd mosfet\_p		

M4  Net-\_M2-Pad1\_ /vin\_2 Net-\_M12-Pad2\_ /vdd mosfet\_p		

M5  Net-\_M2-Pad1\_ /select Net-\_M12-Pad2\_ /vdd mosfet\_p		

M8  Net-\_M12-Pad2\_ /vin\_1 Net-\_M10-Pad1\_ GND mosfet\_n		

M9  Net-\_M12-Pad2\_ /vin\_2 Net-\_M11-Pad1\_ GND mosfet\_n		

M10  Net-\_M10-Pad1\_ Net-\_M1-Pad1\_ GND GND mosfet\_n		

M11  Net-\_M11-Pad1\_ /select GND GND mosfet\_n		

M1  Net-\_M1-Pad1\_ /select /vdd /vdd mosfet\_p		

M7  Net-\_M1-Pad1\_ /select GND GND mosfet\_n		

M6  /vout Net-\_M12-Pad2\_ /vdd /vdd mosfet\_p		

M12  /vout Net-\_M12-Pad2\_ GND GND mosfet\_n		

U1  /vdd /select /vin\_1 /vin\_2 /vout PORT		

.end

**The netlist after making sky130 models syntax changes is as shown below:**

\* c:\spb\_data\esim-workspace\multiplexer\multiplexer.cir

.lib "sky130\_fd\_pr/models/sky130.lib.spice" tt

xM1  Net-\_M1-Pad1\_ select vdd vdd sky130\_fd\_pr\_\_pfet\_01v8		

xM7  Net-\_M1-Pad1\_ select GND GND sky130\_fd\_pr\_\_nfet\_01v8		

xM6  vout Net-\_M12-Pad2\_ vdd vdd sky130\_fd\_pr\_\_pfet\_01v8		

xM12  vout Net-\_M12-Pad2\_ GND GND sky130\_fd\_pr\_\_nfet\_01v8		

xM2  Net-\_M2-Pad1\_ vin\_1 vdd vdd sky130\_fd\_pr\_\_pfet\_01v8		

xM4  Net-\_M12-Pad2\_ vin\_2 Net-\_M2-Pad1\_ vdd sky130\_fd\_pr\_\_pfet\_01v8		

xM3  Net-\_M2-Pad1\_ Net-\_M1-Pad1\_ vdd vdd sky130\_fd\_pr\_\_pfet\_01v8		

xM5  Net-\_M12-Pad2\_ select Net-\_M2-Pad1\_ vdd sky130\_fd\_pr\_\_pfet\_01v8		

xM8  Net-\_M12-Pad2\_ vin\_1 Net-\_M10-Pad1\_ GND sky130\_fd\_pr\_\_nfet\_01v8		

xM10  Net-\_M10-Pad1\_ Net-\_M1-Pad1\_ GND GND sky130\_fd\_pr\_\_nfet\_01v8		

xM9  Net-\_M12-Pad2\_ vin\_2 Net-\_M11-Pad1\_ GND sky130\_fd\_pr\_\_nfet\_01v8		

xM11  Net-\_M11-Pad1\_ select GND GND sky130\_fd\_pr\_\_nfet\_01v8	

Vdd vdd 0 3	

Vin\_1 vin\_1 0 pulse(0 3 0s 0s 0s 5us 10us)

Vin\_2 vin\_2 0 pulse(0 3 0s 0s 0s 2.5us 5us) 

Vd0 select 0 pulse(3 0 0s 0s 0s 10us 20us) 

.tran 0.1us 40us

.control

run

plot  V(select) +  5 V(vin\_2) + 10 V(vin\_1) + 15 V(vout) 

.endc

.end


**Note**: sky130\_fr\_pd file for sky130 model must be present on the same file as .cir.out.

**Truth Table for 2:1 mux using CMOS is as shown below**:

![TRUTH TABLE](https://user-images.githubusercontent.com/70748543/152843883-17ad3869-bf8c-4f6b-9e43-decdc8881021.jpeg)

Now, run the .cir.out file using ngspice and we will get the circuit waveforms as follows:

From the above waveform we can verify the truth table for 2:1 mux using CMOS. 

### 5. REFERENCES:
***
[1] D. S. D. R. A. Rose V Anugraha. Design and performance analysis of 2:1 multiplexer using multiple logic families at 180nmtechnology.https://ieeexplore.ieee.org/abstract/document/8256918. 

[2] S. J. Anjum Aara. Design and implementation of cmos and cnt based 2:1 multiplexer at 32nm technology. www.irjet.net.
