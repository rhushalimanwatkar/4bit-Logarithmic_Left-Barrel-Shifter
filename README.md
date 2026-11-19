
# 4-bit Logarithmic Left Barrel Shifter


## 📌 Overview

A **4-bit Logarithmic Left Barrel Shifter** is a combinational digital circuit that shifts binary data to the left by a specified number of bit positions in a single operation.

This project implements a 4-bit logical left barrel shifter using **Verilog HDL** and **2:1 Multiplexers (MUX)**. The shifting operation is controlled by a 2-bit control signal (`ShiftAmt`), allowing the input data to be shifted by 0, 1, 2, or 3 positions.

Unlike conventional shifters that perform shifting through multiple sequential operations, a barrel shifter performs the required shift using a network of multiplexers in a single combinational operation.

The design follows a **logarithmic architecture** consisting of two stages of multiplexers. Each stage performs shifting by a power-of-two number of positions, making the design efficient in terms of logic depth.

The design is simulated and functionally verified using **ModelSim**.


## ⚙️ Features

- 4-bit logical left barrel shifter.
- Logarithmic two-stage architecture.
- Implemented using 2:1 multiplexers.
- Supports shifting by 0, 1, 2, and 3 positions.
- Combinational logic design.
- Zero filling at vacant bit positions.
- Functional verification using ModelSim.


## 🏗️ Architecture and Working Principle

The barrel shifter consists of two stages, with each stage containing four 2:1 multiplexers.


### Stage 1: Shift by 0 or 1 Bit

- Controlled by `ShiftAmt[0]`.
- If `ShiftAmt[0] = 0`, the input data passes without shifting.
- If `ShiftAmt[0] = 1`, the input data shifts left by one position.
- The intermediate result is stored in a 4-bit wire named `stage1`.


### Stage 2: Shift by 0 or 2 Bits

- Controlled by `ShiftAmt[1]`.
- If `ShiftAmt[1] = 0`, the intermediate data passes without additional shifting.
- If `ShiftAmt[1] = 1`, the intermediate data shifts left by two positions.
- The final shifted result is available at `Dout`.

By combining both stages, the circuit supports all four possible shift amounts.


### Logarithmic Architecture

The number of stages required for an N-bit logarithmic barrel shifter is:

\[
Stages = log_2(N)
\]

For a 4-bit barrel shifter:

\[
Stages = log_2(4) = 2
\]

Therefore, the design requires:
- 2 shifting stages.
- 4 multiplexers per stage.
- 8 total 2:1 multiplexers.


## 🔢 Input and Output Signals

| Signal | Width | Description |
|---|---|---|
| `Din` | 4-bit | Input binary data |
| `ShiftAmt` | 2-bit | Controls the shift amount |
| `stage1` | 4-bit | Intermediate data between stages |
| `Dout` | 4-bit | Final shifted output |


## 📊 Truth Table

For an example input of `Din = 1011`:

| ShiftAmt | Operation | Dout |
|---|---|---|
| 00 | No shift | 1011 |
| 01 | Left shift by 1 | 0110 |
| 10 | Left shift by 2 | 1100 |
| 11 | Left shift by 3 | 1000 |

**Note:** Zeros are inserted into the least significant bit positions during logical left shifting.


## 🔌 MUX Implementation

The 2:1 multiplexer is implemented using basic logic gates:
- NOT gate
- AND gates
- OR gate

The Boolean expression for the multiplexer is:

\[
Y = A(~S) + BS
\]

Where:
- `A` and `B` are the data inputs.
- `S` is the select input.
- `Y` is the output.


## 🛠️ Tools and Technologies

- **Hardware Description Language:** Verilog HDL
- **Simulation Tool:** ModelSim
- **Design Type:** Combinational Logic Circuit
- **Implementation:** Gate-level modeling and structural modeling


## 📁 Project Structure

```text
4bit-Logarithmic-Left-Barrel-Shifter/
│
├── mux2_1.v
│
├── barrel_shifter_4bit.v
│
├── tb_barrel_shifter_4bit.v
│
└── README.md
```


## ▶️ Simulation and Verification

The design is verified using a Verilog testbench in ModelSim.


### Simulation Steps

1. Write the 2:1 MUX module.
2. Implement the 4-bit logarithmic left barrel shifter.
3. Create a testbench to apply different input patterns and shift amounts.
4. Compile all Verilog files in ModelSim.
5. Run the simulation.
6. Observe the waveform and verify the output against the expected truth table.

The testbench checks all four possible shift operations to ensure the correct functionality of the design.


## 🎯 Learning Outcomes

Through this project, I gained practical experience in:

- Understanding logarithmic barrel shifter architecture.
- Designing 2:1 multiplexers using basic logic gates.
- Implementing combinational circuits using Verilog HDL.
- Understanding multi-stage multiplexer-based designs.
- Writing Verilog testbenches.
- Functional verification and waveform analysis using ModelSim.

<img width="1920" height="1020" alt="4-bit_Logarithmic_Barrel_Shifter" src="https://github.com/user-attachments/assets/6201447d-1916-442e-84aa-82b5fcc4bb01" />

