# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
### Procedure
1.Create a new project in Quartus|| Software.

2.Name the project as upc and downc for up and down counter.

3.Create a new verilog hdl file in the project file.

4.Within that file write the program for up and down counter

5.After that run the program and give the clock pulse value as 50 in timing diagram and run the program.

### PROGRAM 
```python
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: KULASEKARAPANDIAN K
RegisterNumber: 212222240052
UPCOUNTER:
module upc(clk,A);
input clk;
output reg[0:3]A;
always@(posedge clk)
begin
		A[0]=((((A[1])&(A[2]))&A[3])^A[0]);
		A[1]=(((A[2])&(A[3]))^A[1]);
		A[2]=((A[3])^A[2]);
		A[3]=1^A[3];
end
endmodule

DOWNCOUNTER:
module downc(clk,A);
input clk;
output reg[0:3]A;
always@(posedge clk)
begin
	A[0]=((((~A[1])&(~A[2]))&A[3])^A[0]);
	A[1]=(((~A[2])&(~A[3]))^A[1]);
	A[2]=((~A[3])^A[2]);
	A[3]=1^A[3];
end
endmodule
```






### RTL LOGIC UP COUNTER AND DOWN COUNTER  
![image](https://github.com/KSPandian7/Exp-7-Synchornous-counters-/assets/113496887/eba5d9b6-22da-4894-9b7a-4d4ee5a2c10a)


![image](https://github.com/KSPandian7/Exp-7-Synchornous-counters-/assets/113496887/8c875b54-3141-48a3-a4ae-5967e97d7af7)









### TIMING DIGRAMS FOR COUNTER  

![image](https://github.com/KSPandian7/Exp-7-Synchornous-counters-/assets/113496887/9a4fc379-2f1a-47b1-952c-40b01aa6c2ac)


![image](https://github.com/KSPandian7/Exp-7-Synchornous-counters-/assets/113496887/6ad64360-5b5d-4ace-9552-47123dc99f8f)




### TRUTH TABLE 

![image](https://github.com/KSPandian7/Exp-7-Synchornous-counters-/assets/113496887/6c3ae5d8-3f06-47ea-ab32-2160d37f2970)



![image](https://github.com/KSPandian7/Exp-7-Synchornous-counters-/assets/113496887/2e82cb54-3daf-456b-af4c-2aab499f2d76)




### RESULTS 
Thus The program for counters is successfully executed.


