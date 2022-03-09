# QOSFapp

This repository contains solution(s) to the QOSF Spring 2022 Mentorship application screening task(s).

Task 1:

The task is to implement a quantum algorithm which takes as input a vector of integers, e.g., [1,3,6,4,2], and a target, e.g., 6, and outputs bitstrings corresponding to subsets of the vector which sum to the target. In this example, with bitstrings being read from right to left, the desired outputs are '10011' (corresponding to [1,3,2]), '11000' (corresponding to [4,2]), and '00100' (corresponding to [6]).

This is implemented in Qiskit via the function vector_subsets_sum, which takes as inputs vector (as above), target (as above), and backend (Qiskit backend simulator or quantum device to run the program).

The implementation uses a standard quantum counting and Grover search on a set of indexing qubits, with each qubit indexing one component of the vector. The oracle is implemented by:
(1) using Draper adders (controlled by the indexing qubits) to sum the vector components referenced by the indexing qubits set to 1, 
(2) bitwise adding the complement of the target so that all qubits of the sum are set to 1 only in case the target is met, 
(3) using a multi-control Toffoli on an ancilla qubit initialized to |-> to implement the phaseflip, and then
(4) uncomputing steps (1-2).