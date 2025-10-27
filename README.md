# AXI_PROTOCOL  
# OVERVIEW  
This module implements an AXI4-compatible slave interface supporting configurable data and address widths with burst read/write support. It handles AXI4's five independent channels—write address (AW), write data (W), write response (B), read address (AR), and read data (R)—with proper handshake, burst processing, and pipelining. It is widely used in SoC designs for high-performance, high-frequency communication between master and slave components.

# KEY FEATURES  
•	**Parameterizable Interface Widths:**  
  Supports flexible DATA_WIDTH, ADDR_WIDTH, and STRB_WIDTH for varying application needs.  
•	**Burst Support:**  
    Implements burst transfers for read and write, handling lengths up to 256 beats, with proper address increment per burst type.  
•	**State Machines for Read/Write:**  
    Write FSM manages address acceptance, burst data writing, and response phases.  
  	Read FSM handles read address acceptance and multi-beat data transfer.  
•	**Memory Array:**  
    Implements a block RAM style memory with size based on address width parameters for data storage and retrieval.  
•	**Protocol Handshaking:**  
    Uses AXI signals VALID and READY for each channel to synchronize transfers, ensuring proper flow control.  
•	**Write Response Generation:**  
    Produces bvalid/bready handshaking with bid and bresp signaling write completion and errors if detected.  
•	**Read Data Pipeline Option:**  
    Supports optional pipelining for read data channel for timing optimizations.  
•	**Byte-Enable Writes:**  
    Uses WSTRB to enable partial byte writes within each data word.  
•	**Error Checking:**  
    Ensures data width alignment and power-of-two restrictions on burst lengths.  
# OPERATION SUMMARY  
•	**Write Channel:**  
On AWVALID & AWREADY, captures write address and burst parameters.  
	On WVALID & WREADY, writes data to memory with byte strobes.  
	After final write (indicated by WLAST), responds with BVALID and BID.  
•	**Read Channel:**  
	On ARVALID & ARREADY, captures read address and burst parameters.  
	Issues read data beats on RDATA with RVALID.  
	Sets RLAST on last beat of burst.  
•	Flow Control:  
Properly holds AWREADY, WREADY, ARREADY, RVALID, and BVALID signals based on internal FSM state and external channel readiness.

# BURST TYPES 
AXI4 supports burst transfers with these types:  
•	FIXED: Same address for all beats.  
•	INCR: Incrementing address.  
Each burst is defined by:  
•	AxLEN: Number of beats (1–256)  
•	AxSIZE: Size of each beat (bytes)  
•	AxBURST: Burst type  
 # OPERATION FLOW  
 <img width="600" height="1000" alt="image" src="https://github.com/user-attachments/assets/a4dd399f-151b-48b3-8039-0655794a3418" />  

 # WAVEFORMS  
 ## TEST_CASE-1  
 ![WhatsApp Image 2025-10-26 at 4 45 13 PM](https://github.com/user-attachments/assets/ece4b950-84fc-489c-bdcd-d7ea0a1d6157)  
 ## TEST_CASE-2  
 ![WhatsApp Image 2025-10-26 at 4 45 19 PM](https://github.com/user-attachments/assets/f5b86892-1766-421f-a94a-2b5a390b2e85)  
 ## TEST_CASE-3  
 ![WhatsApp Image 2025-10-26 at 4 45 26 PM](https://github.com/user-attachments/assets/fb275a50-5935-4145-8483-b3661da84c4c)  
 ## TEST_CASE-4
 ![WhatsApp Image 2025-10-26 at 4 45 31 PM](https://github.com/user-attachments/assets/fc5c5850-8e08-4b9f-aa47-7b927b448b17)




 



