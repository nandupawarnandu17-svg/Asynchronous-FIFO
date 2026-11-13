How It Works

The Asynchronous FIFO transfers data between two independent clock domains using separate write and read clocks. When the write enable signal ("wr_en") is HIGH and the FIFO is not full, input data is stored in memory, and the write pointer is incremented. Similarly, when the read enable signal ("rd_en") is HIGH and the FIFO is not empty, data is retrieved from memory, and the read pointer is incremented. Binary pointers are converted into Gray code to reduce clock-domain crossing issues. Two-stage synchronizers transfer the Gray-code pointers between the write and read clock domains. The synchronized pointers are compared to detect FULL and EMPTY conditions, preventing overflow and underflow.

How to Test

The design is tested using a Verilog testbench with two independent clocks: a 10 ns write clock and a 14 ns read clock. First, the reset operation is checked to ensure that FULL = 0 and EMPTY = 1. Next, 16 data values (10 to 25) are written into the FIFO, and the FULL condition is verified. Then, all 16 values are read and compared with the expected data in the same order. Finally, the EMPTY condition is checked after all data has been read. If all tests pass without any data mismatch, the simulation displays ALL TESTS PASSED.



