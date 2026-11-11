# FIFO (First In First Out)

## 1. What is FIFO?

FIFO stands for **First In First Out**.

It is a data storage method in which the first data entered is the first data removed.

FIFO works like a queue of people waiting for a ticket.

- The first person entering the queue gets the ticket first.
- The second person gets the ticket second.
- The third person gets the ticket third.

Similarly, in FIFO, data is read in the same order in which it is written.

### Why is FIFO used?

- To store data temporarily.
- To transfer data between different modules.
- To maintain the order of data.
- To handle differences in data processing speeds.
- To prevent data loss when properly designed with sufficient storage and flow control.

## 2. Types of FIFO

There are two main types of FIFO:

1. Synchronous FIFO
2. Asynchronous FIFO

## 3. Synchronous FIFO

A Synchronous FIFO uses a **single clock signal** for both read and write operations.

Both operations work using the same clock.

### How does it work?

- Data is written into memory using the common clock.
- The write pointer moves to the next memory location after writing.
- Data is read from memory using the same clock.
- The read pointer moves to the next memory location after reading.
- FULL and EMPTY flags indicate the FIFO status.

### Example

Consider a FIFO with a clock frequency of 50 MHz.

Both read and write operations use the same 50 MHz clock.

### Main Features

- Uses only one clock.
- Read and write operations belong to the same clock domain.
- Simple architecture.
- No clock-domain synchronization is needed between the read and write sides.

### Applications

- FPGA designs.
- Digital signal processing.
- Data buffering.
- Communication between modules using the same clock.

## 4. Asynchronous FIFO

An Asynchronous FIFO uses **two independent clock signals** for read and write operations.

One clock is used for writing, and another clock is used for reading.

Both clocks can have different frequencies and phases.

### How does it work?

- Data is written into memory using the write clock.
- The write pointer moves after a successful write.
- Data is read from memory using the read clock.
- The read pointer moves after a successful read.
- Synchronization logic is used to transfer pointer information between the two clock domains.
- FULL and EMPTY flags indicate the FIFO status.

### Example

Consider two systems:

- Write clock = 100 MHz.
- Read clock = 50 MHz.

The first system writes data using 100 MHz, while the second system reads data using 50 MHz.

The asynchronous FIFO temporarily stores the data and allows both systems to operate independently.

### Main Features

- Uses two independent clocks.
- Supports different clock frequencies.
- Read and write operations belong to different clock domains.
- Uses Gray code for pointer synchronization.
- Uses synchronizer circuits to reduce metastability propagation.
- More complex than synchronous FIFO.

### Applications

- FPGA designs.
- ADC and DAC interfacing.
- Data communication between different clock domains.
- Network communication.
- Image and video processing.

## 5. Difference Between Synchronous and Asynchronous FIFO

| Synchronous FIFO | Asynchronous FIFO |
|---|---|
| Uses one clock. | Uses two independent clocks. |
| Same clock domain. | Different clock domains. |
| Read and write operations use the same clock. | Read and write operations use separate clocks. |
| Simple design. | Comparatively complex design. |
| No CDC synchronization needed between the sides. | Requires pointer synchronization. |
| Binary pointers are commonly used. | Binary and Gray code pointers are used. |

## 6. Conclusion

FIFO is an important data storage structure used in digital systems.

It follows the First In First Out principle, where the first data written is the first data read.

FIFO is mainly classified into Synchronous FIFO and Asynchronous FIFO.

Synchronous FIFO uses a single clock for both read and write operations, whereas Asynchronous FIFO uses two independent clocks.

Both types are widely used in FPGA, VLSI, communication and digital system designs.
