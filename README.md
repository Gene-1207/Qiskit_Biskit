# Qiskit_Biskit
## Aim :
Building a fully functional BB84 Quantum Key Distribution system using Qiskit. 
The project generates a shared secret key between two parties(Alice and Bob), performs basis sifting, estimates the error rate to detect eavesdropping, and measures how noise affects protocol performance. 

## Overview
This project is a full implementation of the BB84 Quantum Key Distribution protocol using:
1. Qiskit for quantum circuit generation
2. IBM Quantum Runtime (ibm_fez backend) for real hardware execution
3. Flask-based networking simulating Alice, Bob, and Eve across multiple laptops
4. It demonstrates how quantum states can be used to establish a shared cryptographic key, detect eavesdropping using QBER, and transmit an encrypted message securely.

## Features
Quantum Protocol
Random bit generation (Alice & Bob)
Basis selection (Z / X)
Qubit preparation according to BB84 rules
Real hardware execution using ibm_fez backend
Bob’s measurement using random bases
Basis sifting
Raw key extraction
Quantum Bit Error Rate (QBER) computation
Security / Attack Simulation
Eve intercept-resend attack
Optional depolarizing noise
QBER impact visualization
Secure key acceptance/rejection based on thresholds
Networking

## Three independent Flask servers:
Alice (prepares qubits)
Eve (optional intercept)
Bob (measures)
Communicates over LAN using REST APIs
Works across 3 different laptops

## Encryption
Final sifted key used to XOR-encrypt a message
Bob receives ciphertext and can decrypt using the shared key

## Setup & Usage
1. Install Requirements
pip install qiskit qiskit-ibm-runtime flask requests numpy
2. Configure IBM Quantum
from qiskit_ibm_runtime import QiskitRuntimeService
QiskitRuntimeService.save_account(channel="ibm_quantum", token="YOUR_API_KEY")
3. Run the Servers
On each laptop:
Role	   Command	                  Port
Eve	      python eve.py	              5001
Bob       python bob.py	              5002
Alice	  python alice.py	          5000
Update IP addresses in each file as required.

## Metrics & Analysis
Quantum Bit Error Rate (QBER)
After sifting, errors are counted:
         𝑄𝐵𝐸𝑅= Number of mismatched bits/Total sifted bits
	​
Interpretation:
< 11% → secure channel
≥ 11% → possible eavesdropping or noise

## Results & Validation
This system outputs:
Alice’s prepared bits/bases
Eve’s intercept results (if enabled)
Bob’s measured bits and bases
Sifted key length
Final shared key
QBER value
Security decision (Accept/Reject key)


## Protocol Comparison
Protocol	         Key Idea	             Pros	                  Cons
BB84	         Random bases,4 states	   Simple, practical	    Needs classical channel
B92	           2-state protocol	         Simpler physically	    Less robust
E91	           Entanglement-based	       Strong security	      Harder to implement


## References
Qiskit Documentation
IBM Quantum Cloud Documentation
BB84 original research paper (Bennett & Brassard, 1984)
Quantum Cryptography lectures
Qiskit IBM official youtube series




