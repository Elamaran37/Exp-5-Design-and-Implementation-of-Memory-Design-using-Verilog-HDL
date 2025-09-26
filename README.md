<img width="1919" height="1077" alt="image" src="https://github.com/user-attachments/assets/46fcad64-e26e-44cd-a07f-4e90066bf44c" /># Exp-5-Design-and-Simulate the-Memory-Design-using-Verilog-HDL
#Aim
To design and simulate a RAM,ROM,FIFO using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 environment.
Apparatus Required
Vivado 2023.1
Procedure
1. Launch Vivado 2023.1
Open Vivado and create a new project.
2. Design the Verilog Code
Write the Verilog code for the RAM,ROM,FIFO
3. Create the Testbench
Write a testbench to simulate the memory behavior. The testbench should apply various and monitor the corresponding output.
4. Create the Verilog Files
Create both the design module and the testbench in the Vivado project.
5. Run Simulation
Run the behavioral simulation to verify the output.
6. Observe the Waveforms
Analyze the output waveforms in the simulation window, and verify that the correct read and write operation.
7. Save and Document Results
Capture screenshots of the waveform and save the simulation logs. These will be included in the lab report.

# Code
# RAM
# Code
```
module Ram_Memory(input clk,rst,en,input [7:0] datain,input [9:0] address,output reg [7:0] dataout);
reg [7:0] Ram_Memory[1023:0];
always @(posedge clk)
begin
if(rst)
begin
dataout <= 8'd0;
end
else if(en)
begin
Ram_Memory[address]<=datain;
end
else
begin
dataout<=Ram_Memory[address];
end
end
endmodule
```
# Test bench
```
module Ram_Memory_tb;
reg clk_t,rst_t,en_t;
reg [7:0] datain_t;
reg [9:0] address_t;
wire [7:0] dataout_t;
Ram_Memory dut(.clk(clk_t),.rst(rst_t),.en(en_t),.datain(datain_t),.address(address_t),.dataout(dataout_t));
initial
begin
clk_t=1'b0;
rst_t=1'b1;
#100
rst_t=1'b0;
en_t=1'b1;
address_t=10'd85;
datain_t=8'd12;
#100
address_t=$random;
datain_t=$random;
#100
en_t=1'b0;
address_t=$random;
#100
address_t=10'd85;
end
always #10 clk_t=~clk_t;
endmodule
```
# Output Waveform
![Uploading image.png…]()

# ROM
# CODE
```
module memory_1kb(input clk,rst,en,input [7:0] datain,input [9:0] address,output reg [7:0] dataout);
reg [7:0] memory_1kb[1023:0];
always @(posedge clk)
begin
if(rst)
begin
dataout <= 8'd0;
end
else if(en)
begin
memory_1kb[address] <= datain;
end
else
begin
dataout <= memory_1kb[address];
end
end 
endmodule
```

# Testbench
```
module memory_1kb_tb;
reg clk_t,rst_t,en_t;
reg [7:0] datain_t;
reg [9:0] address_t;
wire [7:0] dataout_t;
memory_1kb dut(.clk(clk_t),.rst(rst_t),.datain(datain_t),.address(address_t),.dataout(dataout_t),.en(en_t));
initial
begin
clk_t=1'b0;
rst_t=1'b1;
#100
rst_t=1'b0;
en_t=1'b1;
address_t=10'd985;
datain_t=8'd37;
#100
address_t=10'd1000;
datain_t=8'd55;
#1000
en_t=1'b0;
address_t=10'd985;
#100
address_t=10'd1000;
end
always #10 clk_t=~clk_t;
endmodule
```
# Output Waveform
<img width="1919" height="1067" alt="image" src="https://github.com/user-attachments/assets/8977ea39-85ad-4146-bc42-8aa3b1f154f5" />


 # FIFO
 // write verilog code for FIFO
 
 // Test bench

// output Waveform



# Conclusion
The RAM, ROM, FIFO memory with read and write operations was designed and successfully simulated using Verilog HDL. The testbench verified both the write and read functionalities by simulating the memory operations and observing the output waveforms. The experiment demonstrates how to implement memory operations in Verilog, effectively modeling both the reading and writing processes.
 
 

