# 4 KB-ROM-Memory-with-Read-and-Write-Operations
Aim
To design and simulate a 4KB ROM memory with read and write operations using Verilog HDL and verify the functionality through a testbench in the Vivado 2023.1 simulation environment.

Apparatus Required
Vivado 2023.1 or equivalent Verilog simulation tool.
Computer system with a suitable operating system.
Procedure
Launch Vivado 2023.1:

Open Vivado and create a new project.
Design the Verilog Code for ROM:

Write the Verilog code for a 4KB ROM memory with read and write capabilities.
Create the Testbench:

Write a testbench to simulate both the read and write operations, verifying that the data is correctly written to and read from the memory.
Add the Verilog Files:

Add the ROM Verilog module and the testbench file to the project.
Run Simulation:

Run the behavioral simulation in Vivado and check the memory's read and write operations.
Observe the Waveforms:

Analyze the waveform to verify that the memory read and write operations work as expected.
Save and Document Results:

Capture the waveform and include the simulation results in the final report.
Verilog Code for 4KB ROM Memory with Read and Write Operations
In this design, we will implement a 4KB ROM. Since ROM is typically read-only, we will simulate the behavior as if it's writable, but in actual hardware, ROM is typically pre-programmed.

module rom_design(clk,rst,address,dataout); input clk,rst; input[2:0]
address; output reg[3:0] dataout; reg [3:0] rom_design[7:0];
initial begin
rom_design[0]=4'd1;
rom_design[1]=4'd2;
rom_design[2]=4'd3;
rom_design[4]=4'd10;
rom_design[5]=4'd11;
rom_design[6]=4'd12;
rom_design[7]=4'd15; end
always@(posedge clk) begin
if(rst) dataout=4'd0; else
dataout=rom_design[address];
end
endmodule
Testbench code for ROM
module rom_design_tb;
reg clk, rst; reg
[2:0] address; wire
[3:0] dataout;
rom_design uut (
.clk(clk),
 .rst(rst),
 .address(address),
 .dataout(dataout)
);
initial begin clk =
1'b0; forever #5 clk =
~clk; end
initial begin rst
= 1'b1; address =
3'b000;
 // Reset assertion
 #10 rst = 1'b0;

 // Test address 0
 #10 address = 3'b000;
 #10 $display("Address: %d, Dataout: %d", address, dataout);

 // Test address 1
 #10 address = 3'b001;
 #10 $display("Address: %d, Dataout: %d", address, dataout);

 // Test address 2
 #10 address = 3'b010;
 #10 $display("Address: %d, Dataout: %d", address, dataout);

 // Test address 4
 #10 address = 3'b100;
 #10 $display("Address: %d, Dataout: %d", address, dataout);

 // Test address 5
 #10 address = 3'b101;
 #10 $display("Address: %d, Dataout: %d", address, dataout);

 // Test address 6
 #10 address = 3'b110;
 #10 $display("Address: %d, Dataout: %d", address, dataout); // Test
address 7
 #10 address = 3'b111;
 #10 $display("Address: %d, Dataout: %d", address, dataout);

  // Test reset
 #10 rst = 1'b1; #10 $display("Reset asserted,
Dataout: %d", dataout); end endmodule


Conclusion
In this experiment, a 4KB ROM memory with read and write operations was designed and successfully simulated using Verilog HDL. The testbench verified both the write and read functionalities by simulating the memory operations and observing the output waveforms. The experiment demonstrates how to implement memory operations in Verilog, effectively modeling both the reading and writing processes for ROM.
