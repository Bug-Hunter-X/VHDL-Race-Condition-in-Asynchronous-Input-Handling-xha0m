# VHDL Race Condition Example

This repository demonstrates a potential race condition in VHDL code that involves asynchronous inputs.  The `bug.vhdl` file contains the buggy code, while `bugSolution.vhdl` offers a corrected version.  The issue arises from the sensitivity list of the process only including the clock and reset.  When `data_in` changes, this is not immediately reflected until the next clock cycle, making the system unpredictable if `data_in` changes near the clock edge.

## How to reproduce

Synthesize and simulate the `bug.vhdl` code.  Observe the behavior of `data_out` when `data_in` changes rapidly near the clock's rising edge.  Inconsistent or unexpected values of `data_out` indicate the race condition.

## Solution

The `bugSolution.vhdl` file addresses the issue by using a more robust approach that handles asynchronous input changes properly and avoids the race condition.  The solution employs a synchronizer to sample the input signal before registering it.