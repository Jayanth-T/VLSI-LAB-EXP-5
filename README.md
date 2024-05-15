# 5.SIMULATION AND IMPLEMENTATION OF FINITE STATE MACHINE.

# AIM: 
To simulate and synthesis finite state machine using VIVADO 2023.1

# APPARATUS REQUIRED:
VIVADO 2023.1

# PROCEDURE:
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design 

# Logic Diagram :
![301745520-34ec5d63-2b3b-4511-81ef-99f4572d5869](https://github.com/Jayanth-T/VLSI-LAB-EXP-5/assets/106177371/1585aef0-303d-4fa8-8a86-177769add36d)


# FSM (FINITE STATE MACHINE)
VERILOG CODE:
~~~
module Sequence_Detector_Moore(clock,reset,sequence_in,detector_out);
input clock, reset, sequence_in; 
output reg detector_out; 
parameter  S0=2'b00,S1=2'b01,S2=2'b10,S3=2'b11;
reg [1:0] current_state, next_state; 
always @(posedge clock, posedge reset)
begin
 if(reset==1) 
 current_state <= S0;
 else
 current_state <= next_state; 
end 
always @(current_state,sequence_in)
begin
 case(current_state) 
 	S0:begin
		if(sequence_in==1)
   			next_state = S1;
  		else
   			next_state = S0;
 	   end
 	S1:begin
  		if(sequence_in==0)
   			next_state = S2;
  		else
   			next_state = S1;
 	   end
  S2:begin
  	if(sequence_in==0)
   		next_state = S0;
 	 else
   		next_state = S3;
    end 
  S3:begin
  	if(sequence_in==0)
   		next_state = S0;
  	else
   		next_state = S1;
     end
	default:next_state = S0;
endcase
end
always @(current_state)
begin 
 case(current_state) 
 	S0:   detector_out = 0;
 	S1:   detector_out = 0;
 	S2:  detector_out = 0;
 	S3:  detector_out = 1;
 	default:  detector_out = 0;
 endcase
end 
endmodule
always @(current_state)
begin 
 case(current_state) 
 	S0:   detector_out = 0;
 	S1:   detector_out = 0;
 	S2:  detector_out = 0;
 	S3:  detector_out = 1;
 	default:  detector_out = 0;
 endcase
end 
endmodule
~~~

# OUTPUT:
<img width="605" alt="329918276-ddfca205-9386-4892-ad8a-e8c9b7558791" src="https://github.com/Jayanth-T/VLSI-LAB-EXP-5/assets/106177371/745b0e72-3224-4b0f-9c13-8040005e6ada">
<img width="962" alt="329918342-979ae2e5-06c8-43e8-8557-856a22194944" src="https://github.com/Jayanth-T/VLSI-LAB-EXP-5/assets/106177371/f04992ce-7b6a-4017-8e69-431acfcfc00f">



# RESULT:

THUS the finite state machine is simulated using VIVADO 2023.1 and the output is verified successfully.
