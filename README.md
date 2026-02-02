# Quantum Coherent Transport Simulator
A Qiskit-based framework demonstrating coherent state transfer across a 3-node quantum network using cascaded CNOT operations.
### NOTE

This repository implements a minimal but fully transparent simulation of quantum state transport using native Qiskit operations. It visualizes the transport pathway, generates measurement statistics, and exports circuit diagrams and histograms automatically.

---

## Introduction
Quantum coherent transport moves a quantum state across spatially separated nodes using unitary, reversible operations.
Here, the network has three nodes:
|Node|Qubits|
|----|------|
|Node 1|q0, q1, q2|
|Node 2|q3, q4, q5|
|Node 3|q6, q7, q8|

Initial state:
∣ψ<sub>0</sub>⟩=∣101000000⟩

## Transport Mechanism
Each hop is implemented using two CNOT layers:
### Forward CNOTs

CNOT(q<sub>i</sub>→q<sub>i+3</sub>)

### Backward CNOTs

CNOT(q<sub>i+3</sub>→q<sub>i</sub>)

This pair transfers the 3-qubit state coherently between nodes without destroying superposition.

Mathematically, the hop unitary is:

$$
U_{\text{hop}} = \prod_{i=0}^{2} \mathrm{CNOT}(i \rightarrow i+3)\mathrm{CNOT}(i+3 \rightarrow i)
$$

Equivalent to a reversible SWAP-like operation:

$$
U_{\text{hop}}|xyz\rangle |000\rangle = |000\rangle|xyz\rangle
$$

Applying it twice routes the state through Node 2 to Node 3.

---

## Results

### Simulator Output

Ideal simulation yields:

```yaml
'101000000': 1024
```

### Auto-generated Files

- **circuit.png** — rendered quantum circuit  
- **histogram.png** — final measurement histogram

---

## Repository Structure

```text
├── src/transport.py
├── results/circuit.png
├── results/histogram.png
├── README.md
└── requirements.txt
```
--- 

## References
- Qiskit Textbook
- IBM Quantum Aer Documentation
- “Quantum State Routing via CNOT Networks”, 2023
--- 

**_Authored by: Abhiroop Gohar_**

---
