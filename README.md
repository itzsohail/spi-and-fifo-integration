# spi-and-fifo-integration
# SPI-FIFO Integration in Verilog

A Verilog HDL project integrating an 8-byte synchronous FIFO with an SPI Mode 0 master. The FIFO buffers multiple data bytes and automatically sends them through SPI without requiring software intervention between transfers.

## Features

- 8-entry FIFO
- 8-bit data width
- SPI Mode 0 operation
- MSB-first transmission
- 50 MHz system clock
- 2 MHz SPI clock
- Automatic FIFO-to-SPI transfer control
- Controller FSM for transfer sequencing
- Icarus Verilog simulation support
- GTKWave waveform generation

## Project Architecture

```text
                 +------------------+
 data_in ------> |                  |
 wr_en --------> |   FIFO Control   |
                 |                  |
                 +--------+---------+
                          |
                          v
                 +------------------+
                 |    FIFO Memory   |
                 |     8 x 8-bit    |
                 +--------+---------+
                          |
                          v
                 +------------------+
                 |  Controller FSM  |
                 +--------+---------+
                          |
                          v
                 +------------------+
                 |    SPI Master    |
                 |   SPI Mode 0     |
                 +------------------+
                    |  |  |
                   MOSI SCLK CS
