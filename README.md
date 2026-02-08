# Four_bit_ripple_carry_counter_using_asynchronus_reset

`timescale 1ns / 1ps


module Four_bit_ripple_carry_counter(input clk,rst,output [3:0]q);
t_ff d0(clk,rst,q[0]);
t_ff d1(q[0],rst,q[1]);
t_ff d2(q[1],rst,q[2]);
t_ff d3(q[2],rst,q[3]);
endmodule

////********** The module of the T flip flop *************////////////

module t_ff(input clk,rst,output q);
wire din,q1;
d_ff d0(.clk(clk),.rst(rst),.din(din),.q(q));
not(din,q);
endmodule


///////****** D flip flop module **********////////

module d_ff(input clk,rst,din,output reg q);
always@(negedge clk or posedge rst)
begin
if(rst)
q=1'b0;
else
q=din;
end
endmodule
