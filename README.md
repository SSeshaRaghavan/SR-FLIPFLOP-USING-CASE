# SR-FLIPFLOP-USING-CASE

**AIM:**

To implement  SR flipflop using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

SR Flip-Flop SR flip-flop operates with only positive clock transitions or negative clock transitions. Whereas, SR latch operates with enable signal. The circuit diagram of SR flip-flop is shown in the following figure.

![image](https://github.com/naavaneetha/SR-FLIPFLOP-USING-CASE/assets/154305477/0f710028-ad52-4d3e-9276-8714cf023a25)

 
This circuit has two inputs S & R and two outputs Qtt & Qtt’. The operation of SR flipflop is similar to SR Latch. But, this flip-flop affects the outputs only when positive transition of the clock signal is applied instead of active enable. The following table shows the state table of SR flip-flop.

![image](https://github.com/naavaneetha/SR-FLIPFLOP-USING-CASE/assets/154305477/dabfc4f4-87e3-4cbc-9472-f89ee1b5ed30)

 
Here, Qtt & Qt+1t+1 are present state & next state respectively. So, SR flip-flop can be used for one of these three functions such as Hold, Reset & Set based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of SR flip-flop. Present Inputs Present State Next State

![image](https://github.com/naavaneetha/SR-FLIPFLOP-USING-CASE/assets/154305477/dd90d16c-aec5-4290-a586-e2346b1e9eb5)

 
By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. The three variable K-Map for next state, Qt+1t+1 is shown in the following figure.

![image](https://github.com/naavaneetha/SR-FLIPFLOP-USING-CASE/assets/154305477/473efad6-d70b-4ca7-aeb7-898bbfca319f)

 
The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is Q(t+1)=S+R′Q(t)Q(t+1)=S+R′Q(t)

**Procedure**

/* write all the steps invloved */

**PROGRAM**

/* Program for flipflops and verify its truth table in quartus using Verilog programming. Developed by: RegisterNumber:
*/
module SR_FlipFlop(
    input S,
    input R,
    input clk,
    output reg Q,
    output reg Qn
);

    always @(posedge clk) begin
        case ({S, R})
            2'b00: begin
                Q <= Q;
                Qn <= Qn;
            end
            2'b01: begin
                Q <= 0;
                Qn <= 1;
            end
            2'b10: begin
                Q <= 1;
                Qn <= 0;
            end
            2'b11: begin
                Q <= 1'bx;
                Qn <= 1'bx;
            end
        endcase
    end

endmodule

module SR_FlipFlop_tb;
    reg S;
    reg R;
    reg clk;
    wire Q;
    wire Qn;

    SR_FlipFlop uut (
        .S(S),
        .R(R),
        .clk(clk),
        .Q(Q),
        .Qn(Qn)
    );

    initial begin
        clk = 0;
        forever #5 clk = ~clk;
    end

    initial begin
        $monitor("Time=%0t | S=%b, R=%b, Q=%b, Qn=%b", $time, S, R, Q, Qn);

        S = 0; R = 0; #10;
        S = 0; R = 1; #10;
        S = 1; R = 0; #10;
        S = 1; R = 1; #10;

        $finish;
    end

endmodule

**RTL LOGIC FOR FLIPFLOPS**
![image](https://github.com/user-attachments/assets/e62172c7-714b-462d-9224-8f4ff7e8728b)

**TIMING DIGRAMS FOR FLIP FLOPS**
![image](https://github.com/user-attachments/assets/ae8f6059-0a80-4af6-b515-b73bb251c3b7)

**RESULTS**

Implement SR Flip Flop using verilog and validating their functionality using their functional tables is verified successfully
