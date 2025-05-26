# Grover's Algorithm Implementation using Qiskit

This project demonstrates the classical and quantum search of an element using **Grover's Algorithm**. It includes a comparison between:
- **Classical Linear Search** and
- **Quantum Search using Grover's Algorithm** (with a 2-qubit system)

The quantum part is implemented using **Qiskit** and run on the local simulator from the `qiskit-aer` module.

---

## What is Grover's Algorithm?

Grover's Algorithm is a **quantum search algorithm** that finds the unique input to a black box function (oracle) that outputs `True`, using approximately √N queries instead of N — giving it a **quadratic speedup** over classical search algorithms.

Given an unstructured list of `N` items and a single "marked" item, Grover’s algorithm finds that item in **O(√N)** time complexity instead of **O(N)** as in classical search.

---



## Steps Followed in the Quantum Circuit

### Step 1: Import Required Modules
- Load Qiskit components including `QuantumCircuit`, `AerSimulator`, and visualization tools.

### Step 2: Classical Linear Search (For Comparison)
- Iterate through a Python list.
- Use a simple function to simulate an oracle (returns True if number matches target).

### Step 3: Oracle Construction (Quantum)
- Build an oracle circuit that flips the phase of the target state `|11⟩`.
- Uses a Controlled-Z gate to mark the state.

### Step 4: Superposition Initialization
- Apply Hadamard gates to all qubits to put them in equal superposition (representing all states equally).

### Step 5: Oracle Application
- Apply the oracle gate to "mark" the target state by flipping its amplitude's sign.

### Step 6: Diffusion Operator (Inversion about the Mean)
- Apply a sequence of gates (Hadamard, Z, controlled-Z, Hadamard) to amplify the probability of the target state.
- This is the **reflection** step that boosts the marked state.

### Step 7: Measurement
- Measure the final quantum state to classical bits.
- Most frequent output should be the target state (`11` in binary).

### Step 8: Run Simulation
- Use `qiskit_aer`’s `AerSimulator` to simulate the circuit.
- Run for 1024 shots to get a good probability distribution.
- Plot the histogram of output results.

---

## Result

After one iteration of Grover’s algorithm, the target state `|11⟩` (binary for decimal 3) appears with the highest probability in the measurement results.

This demonstrates the **probability amplification** that makes Grover's algorithm powerful.

---

## Requirements

- matplotlib~=3.10.0
- qiskit~=2.0.1
- qiskit-aer~=0.17

---

## How to Run

1. Clone this repository or copy the code into a Jupyter notebook.
2. Ensure you have Qiskit and matplotlib installed.
3. Run each cell step-by-step.
4. Observe the histogram output at the end to verify the search result.

---


