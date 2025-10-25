# AMBA-AXI-Protocol
This repository contains a fully verified AXI protocol implementation with a UVM-based verification environment. The design supports high-speed read and write transactions while maintaining protocol compliance and reliability.
Features:

AXI Master & Slave Interfaces: Handles standard read/write transactions with valid-ready handshaking.

Independent Multi-Channel Operation: Supports multiple channels working concurrently for parallel data transfers.

UVM Testbench: Includes driver, monitor, scoreboard, and functional coverage collection.

Assertions & Coverage: SystemVerilog assertions to ensure correctness and functional coverage for verification closure.
