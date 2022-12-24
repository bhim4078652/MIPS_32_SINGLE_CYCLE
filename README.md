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

#### Clocking
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
