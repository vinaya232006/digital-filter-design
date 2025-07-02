`timescale 1ns/1ps
module fir_filter_tb;
    reg clk = 0;
    reg rst;
    reg signed [7:0] x;
    wire signed [15:0] y;

    fir_filter uut (.clk(clk), .rst(rst), .x(x), .y(y));

    always #5 clk = ~clk;

    initial begin
        $dumpfile("fir_filter.vcd");
        $dumpvars(0, fir_filter_tb);

        rst = 1; x = 0;
        #10 rst = 0;

        // Apply step input
        x = 8'd1;
        repeat (20) begin
            #10;
        end

        x = 8'd0;
        repeat (10) #10;

        $finish;
    end
endmodule
