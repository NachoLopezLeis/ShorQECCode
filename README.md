# Quantum Computing Laboratory: Quantum Error Correction Code (QECC) Implementation

This repository contains the code and material developed for **Practice 2** of the laboratory. The project centers on the implementation and simulation of a **Quantum Error Correction Code (QECC)** designed to protect a quantum state against common single-qubit errors (Bit-Flip, Phase-Flip, and general Pauli Errors).

## Objective

The main objective is to demonstrate the capability of a QECC to encode, detect, diagnose, and correct errors that degrade quantum information. The key objectives are:

1.  Design and apply the quantum circuit for **Encoding** to transform one logical qubit into a redundant physical register.
2.  Implement the **Detection and Diagnosis** logic for errors using Syndrome measurements.
3.  Simulate the application of different **Pauli Errors** (X, Y, Z) on the data qubits.
4.  Execute the **Correction** operation to restore the original quantum state and measure the Fidelity of the recovery.

## Theoretical Background

### Quantum Error Correction Codes (QECC)
Unlike classical codes, QECCs cannot simply copy the state (due to the No-Cloning Theorem) nor measure the state directly (as it would collapse the superposition). Instead, they utilize **entanglement** and **Syndrome** parity measurements on auxiliary qubits to locate the error without revealing the state of the information itself.

### Circuit Components

The notebook implements and tests the following steps:

1.  **Encoding:** The state of a data qubit is entangled with auxiliary qubits. This creates a redundant state spanning a larger Hilbert space (Code Subspace).
2.  **Error Injection:** A Pauli error ($X, Y,$ or $Z$) is applied to a specific physical qubit in the register.
3.  **Syndrome Detection:** Parity measurements (using CNOT gates and auxiliary qubit measurements) are performed. The measurement results (Syndrome) indicate the **location** and **type** of the error, without collapsing the encoded information qubit.
4.  **Correction:** Based on the measured Syndrome, the necessary inverse Pauli gate is applied to the affected qubit to return the system to the original Code Subspace.

### Fidelity Metric
The success of the correction is quantified using **Fidelity** ($\mathcal{F}$), which measures the similarity between the initial state and the final corrected state ($\mathcal{F} = |\langle \psi_{initial} | \psi_{final} \rangle|^2$). A fidelity close to 1.0 indicates a successful recovery.

## Project Structure

The notebook `Practica2IC.ipynb` addresses the following elements:

1.  **Gate Implementation:** Definition of functions for encoding, decoding, error application, and correction logic.
2.  **Fidelity Calculation:** Use of the Fidelity metric to quantify the success of the correction process.
3.  **Error Simulation:** Testing various examples, injecting X, Y, or Z errors on different physical qubits to verify that the correction circuit can:
    * Correctly diagnose the error (Syndrome).
    * Restore the fidelity of the decoded state to approximately 1.0.

## Requirements and Installation

This project relies on standard Python libraries for numerical computation and simulation.

### Prerequisites
* Python 3.8+
* Jupyter Notebook

### Installation of Dependencies
The code requires the following libraries, which are often used for quantum state manipulation and numerical analysis:

```bash
pip install numpy scipy matplotlib
