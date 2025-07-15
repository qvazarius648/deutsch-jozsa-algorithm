# Implementation of the Deutsch-Jozsa Algorithm in Qiskit

This repository contains a Python implementation of the Deutsch-Jozsa quantum algorithm using the Qiskit framework. The project is designed to demonstrate a clear quantum advantage for a specific computational problem.

## 📝 Problem Description

The Deutsch-Jozsa algorithm addresses the problem of determining a property of a function $f$, often called an oracle. The function takes an n-bit binary string as input and returns a single bit (0 or 1):

$$f: \{0,1\}^n \rightarrow \{0,1\}$$

The function `f` is **promised** to be of one of two types:
* **Constant**: It returns the same value (either 0 or 1) for all possible inputs.
* **Balanced**: It returns 0 for exactly half of the inputs and 1 for the other half.

The task is to determine whether the function is constant or balanced by querying it as few times as possible.

###  Quantum Advantage

* **Classical Approach:** In the worst-case scenario, a classical computer would need to evaluate the function up to **$2^{n-1} + 1$** times to be certain of its type.
* **Quantum Approach:** The Deutsch-Jozsa algorithm solves this problem with **only one** query to the quantum oracle, demonstrating an exponential speedup.

---

## 🛠️ Implementation Details

This implementation uses **Qiskit's `AerSimulator`** to perform an ideal local simulation of a quantum computation. The code is structured modularly for clarity and can be easily adapted to run on real quantum hardware through the `QiskitRuntimeService`.

The logical flow closely follows the canonical description of the algorithm found in standard textbooks like "Quantum Computation and Quantum Information" by Nielsen and Chuang.

### Oracle Construction

The core of the algorithm is the construction of a quantum oracle that implements the function **$f(x)**$. In this demonstration, two types of oracles are implemented:

1.  **Constant Oracle:** Implements a function $f(x) = 0$ for all $x$. This is achieved with an identity transformation.
2.  **Balanced Oracle:** Implements the parity function $f(x) = (x_0 \oplus x_1 \oplus ... \oplus x_{n-1})$, where $\oplus$ is addition modulo 2. This is a common and robust example of a balanced function that utilizes all input qubits. It is constructed using a cascade of CNOT gates.

---

## 🚀 Getting Started

### Prerequisites

* Python 3.8+
* Jupyter Notebook or any Python IDE

### Installation

1.  Clone the repository to your local machine:
    ```bash
    git clone [https://github.com/qvazarius648/deutsch-jozsa-algorithm.git](https://github.com/qvazarius648/deutsch-jozsa-algorithm.git)
    cd deutsch-jozsa-algorithm
    ```

2.  Install the required Python packages:
    ```bash
    pip install -r requirements.txt
    ```
   

### Usage

To run the demonstration, open and execute the cells in the Jupyter Notebook `deutsch_jozsa_algorithm.ipynb`.

You can easily switch between testing a `constant` and `balanced` function by changing the `function_type` variable in the main script block.

---

## 📊 Example Output

Running the script for a **4-qubit balanced function** generates the following quantum circuit and measurement results:

**Quantum Circuit:**

![Circuit Diagram](path/to/your/circuit_diagram.png)

**Measurement Results:**

![Measurement Histogram](path/to/your/histogram.png)

As predicted by the algorithm, the measurement result for a balanced function is never the zero-string (`0000`), confirming its type with high probability.
