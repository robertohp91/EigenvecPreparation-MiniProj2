# Eigenvector Preparation-MiniProj2
Uses quantum phase estimation and Grover's algorithm for eigenvector preparation

Mini-Project #2, Quantum Comp Bootcamp Summer 2025
Eigenvalue Preparation
Author: Roberto Hernández Palomares
Title: Eigenvector Preparation


Goal: 
	find/prepare the eigenvector associated to a black-box/oracular unitary U in n-qubits using Quantum Phase Estimation (QPE) and Grover's Algorithm.

Assumptions: 
	- U has 2^n different eigenvalues parameterized by a function \Theta: {0,1}^n\to [0,1].
	- There is a natural d such that 2^d\Theta is an integer.
	- There's a given number t in [0,1] such that exp{i*2*pi*t} = exp{i*2*pi*\Theta(x_0)} for a unique x_0 in {0,1}^n

Input: 
	1.- n: number of qubits for the unitary U which we have oracular access to.
	2.- d as above, which corresponds to precision in approximation and counts number of ancilla qubits. 
	3.- t as above.
	Note: Algorithm works for any values of n and d.

Rough Strategy: 
	Use QPE to mark x_0 and then use Grover's to find it. 

Description of Notebook: 
Step 1.- Implements QPE: This is the point where you can assign values to n, d and t. Built in is construction of oracle U. 

Step 2.- Use Step 1 to mark x_0 and use Grover's algorithm.
	1.- We construct U_Grov, which is a gate with |x_0> as eigenvector for -1 and 1 on the perp.
	2.- 'Digitize' t: Construct best binary approximation to t using d bits.
	3.- Constructs d-dimensional multi-controlled Z gate to be used in Grover's circuit.
	4.- Constructs Grover's Diffusion operator and Grover's Circuit
