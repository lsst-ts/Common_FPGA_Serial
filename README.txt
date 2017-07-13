Usage for each serial port:
1. Generate a target-scoped FIFO (or host to target) for Tx data. Specify a data type of U64.
2. Generate a target-scoped FIFO (or target to host) for Rx data. Specify a data type of U64.

Note:
- Only the LSB of the U64 is used. The main reason a U64 FIFO is used and not a U8 FIFO is for simplisity. It takes a lot more effort to code transfering a timestamp onto the FIFO than it does to ignore the extra bytes. The overhead, timewise, is small (a U8 takes 0.05ms, a U64 takes 0.055ms). This may change should it be required but for now the benefit outweighs the cost.
- This allows for serial ports to be used in a single cycle timed loop.