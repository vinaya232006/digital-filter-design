module fir_filter (
    input clk,
    input rst,
    input signed [7:0] x,   // 8-bit input
    output signed [15:0] y  // 16-bit output
);
    parameter N = 4;  // Number of taps

    // FIR coefficients (example: low-pass filter)
    reg signed [7:0] h[0:N-1] = '{8'd3, 8'd5, 8'd5, 8'd3};

    // Delay line
    reg signed [7:0] x_reg[0:N-1];

    integer i;
    always @(posedge clk or posedge rst) begin
        if (rst) begin
            for (i = 0; i < N; i = i + 1)
                x_reg[i] <= 0;
        end else begin
            for (i = N-1; i > 0; i = i - 1)
                x_reg[i] <= x_reg[i-1];
            x_reg[0] <= x;
        end
    end

    // Multiply and accumulate
    reg signed [15:0] acc;
    always @(*) begin
        acc = 0;
        for (i = 0; i < N; i = i + 1)
            acc = acc + x_reg[i] * h[i];
    end

    assign y = acc;
endmodule
