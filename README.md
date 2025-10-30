# 32-BIT_ALU Simulation and Synthesis

## Aim:
Write a Verilog code for a 32-bit ALU supporting four logical and four arithmetic operations. Use case statements in behavioural modelling.
To verify functionality using the Test Bench, synthesize and analyse area and Power reports of a 32 Bit ALU design 

## Tool Required:
Functional Simulation: Incisive Simulator (ncvlog, nclaunch, ncsim)

Synthesise using Genus

## Design Information and Block Diagram:
The ALU will take in two 32-bit values and a control line. An Arithmetic unit does the following tasks like addition, subtraction, multiplication and logical operations. As the input is given in 32-bit, we get a 32-bit output. The arithmetic will show only one output at a time, so a selector is necessary to select one of the operators.

<img width="668" height="344" alt="image" src="https://github.com/user-attachments/assets/1195efe3-e2dd-443c-8bf0-be1579c06533" />

#### Fig 1: Block Diagram of 32 Bit ALU
<img width="1920" height="1080" alt="Screenshot (39)" src="https://github.com/user-attachments/assets/178cee78-482c-4e25-92ee-f9c96d607870" />


## Creating a Workspace:

Create a folder in your name (Note: Give folder name without any space) and create a new sub-Directory name it as Exp3 or alu_32bit for the Design and open a terminal from the Sub-Directory.

## Creating Source Codes
In the Terminal window, type gedit <filename>.v (ex: gedit alu_32bit.v)

A Blank Document opens up into which the following source code can be typed.

(Note: File name should be with HDL Extension)

#### a)	To verify the Functionality using the Test Bench

## Source Code – Using Case Statement :

(Include program here)

Use the Save option or Ctrl+S to save the code, or click on the save option from the top-right corner and close the text file.

## Creating a Test Bench:

Similarly, create your test bench using gedit <filename_tb>.v to open a new blank document (alu_32bit_tb_case).

## Test Bench :

(Include test bench program here)

Use the Save option or Ctrl+S to save the code, or click on the save option from the top-right corner and close the text file.

## Functional Simulation:

Invoke the cadence environment by typing the commands below

tcsh (Invokes C-Shell)

source /cadence/install/cshrc (mention the path of the tools)

(The path of cshrc could vary depending on the installation destination)

After this, you can see the window like below

#### Fig 2: Invoke the Cadence Environment
<img width="1920" height="1080" alt="Screenshot (40)" src="https://github.com/user-attachments/assets/6f9747ce-8287-4b44-905a-24d2476c50e6" />

To Launch the Simulation tool

•linux:/> nclaunch -new& // “-new” option is used for invoking NCVERILOG for the first time for any design

or

•linux:/> nclaunch& // On subsequent calls to NCVERILOG

It will invoke the nclaunch window for functional simulation. We can compile, elaborate and simulate it using Multiple Steps.

#### Fig 3: Setting Multi-step simulation
<img width="1920" height="1080" alt="Screenshot (41)" src="https://github.com/user-attachments/assets/9c6f86e2-f2e7-4abc-9dea-2ddfbfeba9a7" />


Select Multiple Step and then select “Create cds.lib File” as shown in the figure below

Click the .cds.lib file and save the file by clicking on the Save option

#### Fig 4:cds.lib file Creation
<img width="1920" height="1080" alt="Screenshot (42)" src="https://github.com/user-attachments/assets/be16db6c-4af4-4562-adc0-e22c6b085866" />

Save .lib file and select the correct option for cds.lib file format based on the HDL Language and Libraries used.

Select “Don’t include any libraries (verilog design)” from “New cds.lib file” and click on “OK” as in the figure below.

We are simulating a verilog design without using any libraries

Click “OK” in the “nclaunch: Open Design Directory” window, as shown in the figure below
 
#### Fig 5: Selection of Don’t include any libraries
<img width="1920" height="1080" alt="Screenshot (43)" src="https://github.com/user-attachments/assets/7d675009-1cb6-4d73-b46c-e54551474a65" />

An ‘NCLaunch window’ appears as shown in the figure below

Left side, you can see the HDL files. The right side of the window has Worklib and snapshots directories listed.

Worklib is the directory where all the compiled codes are stored, while Snapshot will have the output of elaboration, which in turn goes for simulation.

To perform the function simulation, the following three steps are involved: Compilation, Elaboration and Simulation.

#### Fig 6: Nclaunch Window
<img width="1920" height="1080" alt="Screenshot (44)" src="https://github.com/user-attachments/assets/4e44d393-477f-4653-9caf-d7cd7d20226b" />


### Step 1: Compilation:
– Process to check the correct Verilog language syntax and usage

Inputs: Supplied are Verilog design and test bench codes

Outputs: Compiled database created in mapped library if successful, generates report else error reported in log file

#### Steps for compilation:
1.	Create work/library directory (most of the latest simulation tools creates automatically)
   
2.	Map the work to library created (most of the latest simulation tools creates automatically)
   
3.	Run the compile command with compile options

i.e Cadence IES command for compile: ncverilog +access+rwc -compile filename.v

Left side select the file and in Tools: launch verilog compiler with current selection will get enable. Click it to compile the code
Worklib is the directory where all the compiled codes are stored while Snapshot will have output of elaboration which in turn goes for simulation

#### Fig 7: Compiled database in WorkLib
<img width="1920" height="1080" alt="Screenshot (46)" src="https://github.com/user-attachments/assets/c7537bc5-105d-4f94-9b68-c97993373e3c" />

After compilation, it will come under worklib. You can see on the right side window

select the test bench and compile it. It will come under Worklib. Under Worklib, you can see the module and test bench.

The cds.lib file is an ASCII text file. It defines which libraries are accessible and where they are located. It contains statements that map logical library names to their physical directory paths. For this Design, you will define a library called “worklib”

### Step 2: Elaboration:
To check the port connections in a hierarchical design

Inputs: Top-level design/test bench Verilog codes

Outputs: Elaborate database updated in the mapped library if successful, generates a report, else error reported in the log file

#### Steps for elaboration
– Run the elaboration command with elaborate options

1.It builds the module hierarchy

2. Binds modules to module instances
   
3.Computes parameter values

4. Checks for hierarchical name conflicts
   
5.It also establishes net connectivity and prepares all of this for simulation

After elaboration, the file will come under snapshot. Select the test bench and simulate it.

#### Fig 8: Elaboration Launch Option

### Step 3: Simulation:
– Simulate with the given test vectors over a period of time to observe the output behaviour.

Inputs: Compiled and Elaborated top-level module name

Outputs: Simulation log file, waveforms for debugging

Simulations allow dumping design and test bench signals into a waveform

Steps for simulation – Run the simulation command with simulator options

#### Fig 9: Design Browser window for simulation
<img width="1920" height="1080" alt="Screenshot (48)" src="https://github.com/user-attachments/assets/584592e5-cd66-4dda-88a9-d595c2b7fe6a" />


#### Fig 10: Simulation Waveform Window
<img width="1920" height="1080" alt="Screenshot (49)" src="https://github.com/user-attachments/assets/134c349b-cdaa-4ec7-b01e-645ca0eb40ba" />


Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

### Performing Synthesis
The Liberty files are present in the library path,

• The Available technology nodes are 180nm,90nm and 45nm.

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist. Or use source run.tcl command in the terminal window to view the netlist, and a log file will be created in the working folder.

#### Fig 11: Synthesis RTL Schematic 
<img width="1920" height="1080" alt="Screenshot (50)" src="https://github.com/user-attachments/assets/cd81691c-7e58-472a-bc0c-5dea6f237902" />


#### Fig 12: Area report
<img width="1920" height="1080" alt="Screenshot (51)" src="https://github.com/user-attachments/assets/74107bbd-e467-4467-a2a3-290b3dfda2bf" />

#### Fig 13: Power Report
<img width="1920" height="1080" alt="Screenshot (52)" src="https://github.com/user-attachments/assets/7ecfefe1-e41a-4234-8b55-36d662f7623e" />


## Result
The functionality of the 32-bit ALU was successfully verified using a test bench and simulated with the nclaunch tool. Additionally, the generic netlist of the 32-bit ALU was generated, and the corresponding area and power reports were analyzed and tabulated using Cadence Genus.
