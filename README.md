METHODOLOGY
We started with defining the segments of code as follows:
A. Data Segment
The data segment contains various message strings that are displayed to the user
during program execution.
• msg_intro: Provides an introduction to the calculator, listing available
operations.
• msg_A, msg_S, msg_M, etc.: Messages that display results for specific
operations (addition, subtraction, multiplication, etc.).
• cont: Asks the user if they want to use the calculator again.
• bye: A thank-you message when the program exits.
• Variables val1, val2, temp, and agn are defined for storing intermediate values
used in operations and control flow.
B. Code Segment
The code segment contains the main logic for the calculator. It defines a set of
functions for arithmetic and logical operations, and the main flow that guides the user
through the calculator's interface.
Main Procedure
The code starts by setting up the data segment (MOV AX, @data and MOV DS,
AX).
The Start label marks the beginning of the calculator's user interaction:
• It displays the introduction message (msg_intro) and asks the user to select
an operation.
• After receiving the user's choice, the code uses a series of comparisons (CMP)
and jumps (JE) to direct the flow to the corresponding operation function.
5
Operations:
Each arithmetic and logical operation has its own label and associated code. Here's a
summary of the key operations:
• Addition: Takes two numbers, adds them, and displays the result.
• Reads two inputs from the user, stores them in val1 and val2.
• Adds them (ADD AX, val2), stores the result in temp, and displays it.
• Subtraction: Takes two numbers, subtracts the second from the first, and displays
the result.
• Similar to addition, but uses SUB for subtraction.
• Multiplication: Multiplies two numbers and displays the result.
• Uses the MUL instruction to multiply AX by val2.
• Division: Divides the first number by the second and displays the result.
• Checks if the divisor is zero (CMP BX, 0) and jumps to Error if true.
• Resets DX to zero before division to avoid overflow.
• Uses DIV BX to divide AX by BX and stores the result in temp.
• Logical Operations (OR, AND, XOR, NOT): These operations perform bitwise
logical operations between two numbers or on a single number (for NOT).
• Each operation uses the corresponding assembly instruction (e.g., OR, AND,
XOR, NOT).
• Modulus: These operations provide additional functionality.
• Modulus: Divides two numbers and retrieves the remainder (DIV BX, MOV
temp, DX).
6
• Error Handling and Control Flow:
The code includes basic error handling for division by zero, jumping to an error message if the divisor is zero.
The Con label allows the user to choose whether to use the calculator again, with
options for "yes" or "no."
The _Bye label is the exit point, displaying a thank-you message and halting the
program.
• Additional Definitions and Endpoints:
DEFINE_SCAN_NUM, DEFINE_PRINT_NUM, and DEFINE_PRINT_NUM_UNS are
assumed to be macros or subroutines that handle input scanning and printing
numbers.
The code ends with a halt (HLT) and a return (ret).
