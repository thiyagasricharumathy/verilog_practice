# Synchronous FIFO – Specification Sheet

## 1. Project Overview
A Synchronous FIFO (First In First Out) is a temporary data storage unit in which data is written and read using a common clock signal. The first data written is the first data read.

## 2. Design Specifications

| Parameter | Specification |
|---|---|
| FIFO Type | Synchronous FIFO |
| Data Width | 8 bits |
| FIFO Depth | 8 words |
| Total Storage Capacity | 64 bits |
| Clock | Single common clock |
| Reset | Synchronous active-high reset |
| Write Enable | `we` |
| Read Enable | `re` |
| Data Input | `data_in[7:0]` |
| Data Output | `data_out[7:0]` |
| Status Flags | `full`, `empty` |
| Read/Write Operation | Clock-edge triggered |
| HDL | Verilog HDL |
| Simulation Tool | Icarus Verilog |
| Waveform Viewer | GTKWave |

## 3. Input Ports

| Signal | Width | Description |
|---|---:|---|
| `clk` | 1 bit | Common clock signal |
| `rst` | 1 bit | Resets FIFO to its initial state |
| `we` | 1 bit | Enables write operation |
| `re` | 1 bit | Enables read operation |
| `data_in` | 8 bits | Data to be stored in FIFO |

## 4. Output Ports

| Signal | Width | Description |
|---|---:|---|
| `data_out` | 8 bits | Data read from FIFO |
| `full` | 1 bit | Indicates FIFO is full |
| `empty` | 1 bit | Indicates FIFO is empty |

## 5. Functional Specifications

- Data is written into FIFO when `we = 1` and FIFO is not full.
- Data is read from FIFO when `re = 1` and FIFO is not empty.
- Both read and write operations are synchronized to the same clock.
- The write pointer identifies the memory location for the next write.
- The read pointer identifies the memory location for the next read.
- The `full` flag indicates that all storage locations are occupied.
- The `empty` flag indicates that no data is available to read.
- FIFO follows the First In First Out principle.

## 6. Expected Operation

| Condition | Expected Behaviour |
|---|---|
| Reset | Clears pointers and sets FIFO to empty |
| Write (`we=1`) | Stores input data if FIFO is not full |
| Read (`re=1`) | Outputs stored data if FIFO is not empty |
| FIFO Full | Prevents further write operations |
| FIFO Empty | Prevents read operations |
| Simultaneous Read and Write | Performs both operations when permitted |

## 7. Verification

The design can be verified using a Verilog testbench.

**Test cases:**
1. Reset operation
2. Write data into FIFO
3. Read data from FIFO
4. Verify FIFO empty condition
5. Verify FIFO full condition
6. Perform simultaneous read and write
7. Check data order (FIFO behaviour)

## 8. Tools Used

- Verilog HDL
- Icarus Verilog
- GTKWave

## 9. Expected Result

The synchronous FIFO should store and retrieve data in the same order in which it was written, while correctly indicating its FULL and EMPTY status.
