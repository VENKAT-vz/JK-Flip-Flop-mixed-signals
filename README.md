# JK-Flip-Flop-mixed-signals
Flip flops are the electronic devices which consists of two stable states.The flip flops are the fundamental building<br />
blocks in digital electronics systems.These are sequential circuits since the output depends on both present input and <br />
past output.These circuits are basic memory storage elements.There are different kinds of flip flops,like SR flip flop,<br />
JK flip flop,D flip flop and T flip flop.The input and output to a JK flip flop are digital signals but the main aim <br />
here is to design and simulate JK flip flop using mixed signals i.e. by using both analog and digital signals.<br />  
### 2. Reference Circuit Diagram
![WhatsApp Image 2022-02-28 at 9 57 22 PM v1 (1)](https://user-images.githubusercontent.com/96101971/156883575-05f13deb-72bd-4dbc-8d24-830a7154bde6.jpg)
### 3. Reference Waveforms
![waveeee v1](https://user-images.githubusercontent.com/96101971/156883624-a2795472-1634-4b0c-93c5-4646202b8fd8.jpg)
### 4. Circuit Details
The JK flip flop was invented by Jack Kilby and hence the name JK flip flop.It is the most widely used flip flop.<br />
This flipflop is also called as universal flip flop.The sequential operation of JK flip flop is same as that of<br />
SR flip flop Except that the JK flip flop does not allow the invalid input state in which both the inputs are 0.<br />
<br />
The basic SR flip flop suffers from the following two problems:<br />
i)First, the condition S=R=0 must be avoided.<br />
ii)second,if the state of S or R changes its state while the input which is enabled is high, the correct latching<br />
action does not occur.<br />
<br />
Thus, to overcome these two drawbacks,JK flip flop was invented.<br />
The design of JK flip flop is same as that of SR flip flop but consists of a clock,two input AND gates are replaced <br />
by two 3-input NAND gates.Here J=S and K=R and with the third input of each NAND gate connected to the outputs at Q and Qbar.<br />
The cross-coupling of the SR flip-flop permits the previous invalid condition of S=R=1 to be used to produce the toggle action as the two inputs are now interlocked.<br />
<br />
At the input side of jk flip flop we use analog to digital converter(adc_bridge) and at the output side we use a digital to
analog converter(dac_bridge).In this way we can design JK flip flop in mixed signals.<br />
<br />
The truth table of JK flip flop is shown below:<br />
![truth table v1 (1)](https://user-images.githubusercontent.com/96101971/156883268-7974628a-3f9a-42a5-a20c-5a17a5532059.jpg)
<br />
### 5. Software Used
#### -eSim
eSim is an open source EDA tool for circuit design,analysis and PCB design.It is an integrated tool built using<br />
open source software such as KiCad and NgSpice.<br />
For more details on eSim Refer: https://esim.fossee.in/home
#### -NgSpice
It is an open source software for Spice simulation.<br />
For more details Refer: http://ngspice.sourceforge.net/docs.html
#### -Makerchip
Makerchip is a platform which provides free and instant access to the latest tools from your browser and from <br />
your desktop.<br />
For more details Refer :https://www.makerchip.com/
#### -Verilator
Verilator converts verilog HDL to C++ or system C.<br />
For more details on Veriltor Refer:https://www.veripool.org/verilator/
### 6. Implementation of the circuit
#### Circuit Diagram of JK flip flop in eSim
![Screenshot (13)](https://user-images.githubusercontent.com/96101971/156823161-6d7e32e5-9721-480c-b3aa-cfafcdb55cdb.png)
#### Verilog Code for JK flip flop
![Screenshot (16)](https://user-images.githubusercontent.com/96101971/156823861-df41f654-4a56-45bb-b9e9-54d8578f0ef7.png)
### 7. Makerchip
```\TLV_version 1d: tl-x.org
\SV
/* verilator lint_off UNUSED*/  /* verilator lint_off DECLFILENAME*/  /* verilator lint_off BLKSEQ*/  /* verilator lint_off WIDTH*/  /* verilator lint_off SELRANGE*/  /* verilator lint_off PINCONNECTEMPTY*/  /* verilator lint_off DEFPARAM*/  /* verilator lint_off IMPLICIT*/  /* verilator lint_off COMBDLY*/  /* verilator lint_off SYNCASYNCNET*/  /* verilator lint_off UNOPTFLAT */  /* verilator lint_off UNSIGNED*/  /* verilator lint_off CASEINCOMPLETE*/  /* verilator lint_off UNDRIVEN*/  /* verilator lint_off VARHIDDEN*/  /* verilator lint_off CASEX*/  /* verilator lint_off CASEOVERLAP*/  /* verilator lint_off PINMISSING*/  /* verilator lint_off LATCH*/  /* verilator lint_off BLKANDNBLK*/  /* verilator lint_off MULTIDRIVEN*/  /* verilator lint_off NULLPORT*/  /* verilator lint_off EOFNEWLINE*/  /* verilator lint_off WIDTHCONCAT*/  /* verilator lint_off ASSIGNDLY*/  /* verilator lint_off MODDUP*/  /* verilator lint_off STMTDLY*/  /* verilator lint_off LITENDIAN*/  /* verilator lint_off INITIALDLY*/  /* verilator lint_off TIMESCALEMOD*/  

//Your Verilog/System Verilog Code Starts Here:
module venkatesh_jk(j, k, clk, q, qb);
 input j, k, clk;
 output reg q, qb;
 initial
 begin
 q=1'b0;
 qb=1'b1;
 end
 
 always@(posedge clk)
  begin
 case({j,k})
2'd0:q=q;
2'd1:q=1'b0;
2'd2:q=1'b1;
2'd3:q=~q;
 endcase
qb=~q;
 end
 
 endmodule


//Top Module Code Starts here:
	module top(input logic clk, input logic reset, input logic [31:0] cyc_cnt, output logic passed, output logic failed);
		logic  j;//input
		logic  k;//input
		logic  q;//output
		logic  qb;//output
//The $random() can be replaced if user wants to assign values
		assign j = $random();
		assign k = $random();
		venkatesh_jk venkatesh_jk(.j(j), .k(k), .clk(clk), .q(q), .qb(qb));
	
\TLV
//Add \TLV here if desired                                     
\SV
endmodule
````
### 8. Makerchip Plots
![Screenshot (15)](https://user-images.githubusercontent.com/96101971/156872040-b5d4c26b-f2c3-40b5-91f5-f10f26fdb51b.png)
### 9. Netlists
![image](https://user-images.githubusercontent.com/96101971/156872197-2ca2ffd2-513b-40f4-9a8c-96ad9e804715.png)
### 10. NgSpice plots
![ckt waveforms](https://user-images.githubusercontent.com/96101971/156872325-1139187b-34a1-444e-b308-09af2fd1ecd6.png)
### 11. Steps to run generate NgVeri model
   1. Open eSim tool<br />
   2. Click on Makerchip and run NgVeri-Makerchip<br />
   3. Add top level verilog model file in Makerchip tab<br />
   4. Simulate the verilog code <br />
   5. Click on NgVeri tab <br />
   6. Add dependency files<br />
   7. Click on run Verilog to NgSpice Converter<br />
   8. Debug if any errors are there<br />
   9. Model is created successfully<br />
### 12. Steps to Run this Project
   1. Open a new terminal<br />
   2. Clone this project using the following command:<br />
   ```git clone 
   3. Change directory:<br />
   ```cd esim-workspace/venkatesh_jk```<br />
   4. Run ngspice:<br />
   ```ngspice venkatesh_jk.cir.out```<br /> 
   5. To run the project in eSim:<br /> 
      - Run eSim<br /> 
      - Load the project<br /> 
      - Open eeSchema<br /> 
### 13. Acknowlegdements
   *  FOSSEE, IIT Bombay
   *  Steve Hoover,Founder, Redwood EDA 
   *  Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd.
   *  Sumanto Kar,eSim Team,FOSSEE
### 14. References
   *  V. T. Phyne, Fundamentals of Digital Systems Design, NJ, Englewood Cliffs:Prentice-Hall, pp. 217-245, 1973.<br /> 
   *  J. Millman and C. C. Halkias, Integrated Electronics: Analog and Digital Circuits and Systems,<br /> 
        New York:McGraw-Hill, pp. 627-632, 1972.<br /> 
   *  https://www.javatpoint.com/jk-flip-flop-in-digital-electronics	

