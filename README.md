# MIPS_32_SINGLE_CYCLE

## INTRODUCTION :
- An instruction set architecture is an interface that defines the hardware operations which are available to software.

- In a basic single-cycle implementation all operations take the same amount of time—a single cycle.
- A multicycle implementation allows faster operations to take less time than slower ones, so overall performance can be increased.
- Finally, pipelining lets a processor overlap the execution of several instructions, potentially leading to big performance gains.

### In order to understand these figures it is necessary to understand five things.
- How the clock is used.
- How the ALU is used.
- Instruction activities for the different types of instructions.
- The roles of the control signals.
- Datapath and Controlpath.

## Clocking :
There are two kinds of logic circuitry: combinational logic and state elements. State elements retain information for the duration of a CPU cycle. During the clock cycle combinational logic generates new values for the state elements. These values are not captured by the state elements until the end of a cycle.

#### Combinational logic
- The output of combinational logic follows inputs after a few gate delays.
- Data selection, such as selecting a general purpose register or selecting a particular memory address for a read, is combinational logic.

#### State Elements
- State elements include the following.
   - memory.
   - general purpose registers (direct program access).
   - internal registers such as the program counter.
 
- The output of edge triggered state elements changes only after a clock transition. State elements can be designed to respond either to 0-to-1 transitions or to 1-to-0 transitions. Whichever edge is used is, by convention, the start of a clock period.

- State elements may have an enable control. If so they change state only on clock transitions where this control is asserted (has value 1).

#### Clock Time
The clock time, one of the three factors in the performance equation, is set to be greater than the combinational gate delays plus any setup time required for state elements. The setup time is usually small compared to the combinational gate delays.


## ALU OPERATION :
The ALU can be used in three different ways:

- It performs the arithmetic or logical operation specified by the instruction mnemonic. This is how it is used for all arithmetic and logical instructions.
- It does a subtraction in order to compare two numbers. This is how it is used for branches and compare instructions.
- It calculates a memory address by adding a register and the sign-extended immediate field. This is how it is used for memory loads and stores.

The main control block only decodes the opcode bits of the instruction. When these bits are not all 0 the ALUOp signal from the main control block specifies the ALU operation and this signal is passed to the ALU without modification.

When the opcode bits are 000000 it indicates that the instruction is an R-type instruction. Then the function (fn) bits specify the operation performed by the ALU. The ALUOp signal is then just a special code that indicates that the ALU Control block should determine the ALU operation from the function bits.

### ALU control

![App Screenshot](https://github.com/bhim4078652/MIPS_32_SINGLE_CYCLE/blob/main/images_req/ALU1.jpg)

![App Screenshot](https://github.com/bhim4078652/MIPS_32_SINGLE_CYCLE/blob/main/images_req/ALU2.jpg)

![App Screenshot](https://github.com/bhim4078652/MIPS_32_SINGLE_CYCLE/blob/main/images_req/ALU3.jpg)

## MIPS Instruction Types

When MIPS instructions are classified according to coding format, they fall into four categories: R-type, I-type, J-type, and coprocessor. The coprocessor instructions are not considered here.

The classification below refines the classification according to coding format, taking into account the way that the various instruction fields are used in the instruction. The details of the execution activities and the required control signal values depend almost entirely on the instruction type in this classification.

- Non-Jump R-Type
- Immediate Arithmetic and Logic
- Branch
- Load
- Store
- Non-Register Jump
- Register Jump

further details about MIPS instruction class can be found [here](https://www.d.umn.edu/~gshute/mips/single-cycle-summary.pdf). 

## CONTROL SIGNALS :
The control signals are grouped according to the following instruction execution activities.

- Instruction fetch.
- PC update.
- Instruction decode.
- Source operand fetch.
- ALU operation.
- Memory access.
- Register write.

![App Screenshot](https://github.com/bhim4078652/MIPS_32_SINGLE_CYCLE/blob/main/images_req/CONTROL1.jpg)

![App Screenshot](https://github.com/bhim4078652/MIPS_32_SINGLE_CYCLE/blob/main/images_req/CONTROL2.jpg)

### deriving the ALU operation using ALU_OP and FUNCTION field of instruction.
![App Screenshot](https://github.com/bhim4078652/MIPS_32_SINGLE_CYCLE/blob/main/images_req/CONTROL3.jpg)
