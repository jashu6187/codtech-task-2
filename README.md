Name:OBULANAYAKULAGARI NAGA JASWANTH <br>
Company:CODTECH IT SOLUTIONS <br>
ID:CT6WDS130 <br>
Domain:VLSI <br>
Duration:JUNE 2024 to 17Th JULY 2024” <br>
Mentor:SRAVANI GOUNI <br>
Over view of the project <br>
code <br>
/**/Verilog FSM Design: <br>
module simple_fsm( <br>
    input clk, <br>
    input reset, <br>
    output reg state_out <br>
); <br>

// Define states <br>
parameter S0 = 2'b00; <br>
parameter S1 = 2'b01; <br>
parameter S2 = 2'b10; <br>

// State register <br>
reg [1:0] state; <br>

// State transition logic <br>
always @(posedge clk or posedge reset) begin <br>
    if (reset) begin <br>
        state <= S0; <br>
    end else begin <br>
        case(state) <br>
            S0: state <= S1; <br>
            S1: state <= S2; <br>
            S2: state <= S0; <br>
            default: state <= S0; <br>
        endcase <br>
    end <br>
end <br>

// Output logic <br>
always @(*) begin <br>
    case(state) <br>
        S0: state_out = 1'b0; <br>
        S1: state_out = 1'b1; <br>
        S2: state_out = 1'b0; <br>
        default: state_out = 1'b0; <br>
    endcase <br>
end <br>

endmodule <br>
/**/Test bench for FSM: <br>
module tb_simple_fsm; <br>

reg clk, reset; <br>
wire state_out; <br>

// Instantiate the FSM module <br>
simple_fsm fsm_inst( <br>
    .clk(clk), <br>
    .reset(reset), <br>
    .state_out(state_out) <br>
); <br>

// Clock generation <br>
always begin <br>
    #5 clk = ~clk; <br>
end <br>

// Reset generation <br>
initial begin <br>
    reset = 1'b1; <br>
    #10 reset = 1'b0; <br>
end <br>

// Stimulus generation <br>
initial begin <br>
    #20; <br>
    $display("State at time 20: %b", state_out); <br>
    
    #10; <br>
    $display("State at time 30: %b", state_out); <br>
    
    #10; <br>
    $display("State at time 40: %b", state_out); <br>
    
    $finish; <br>
end <br>

endmodule <br>
![]()
