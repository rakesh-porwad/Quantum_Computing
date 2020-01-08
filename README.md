The Berstein-Vazarni Algorithm is commonly knows for finding a secret number in a single attempt. 
So say lets assume a secret number in a box is 10011 (in binary). 

The Classical Approach: 
The way a classical algorithm would go about approaching this problem, is by going through a series of 5(because bits are 5) AND operations assuming 00001 at the first, 
to find our secret number.
For Example: 
secrete number: 		100011
Classical 1st approach:		000001

We can see that they both have a 1 as the last bit, so this means that the algorithm has found a 1 in that place. (Since AND(1,1) = 1)

This series of guesses is repeated for every bit and this algorithm will have to perform as many steps as there are bits in our secrete number (it is 5 here). 

So if we had a bitstring with half million bits, we would have to query for half million times!

This is where quantum computers can help here. 

Quantum computers can solve this problem, and find the secret number with just one step.

Using IBM’s Qiskit and Aer backend simulator, I have tried and implemented the same algorithm, along with cicuit visualizations step by step.

1) What we want to do first is initialize as many qubits as there are bits. we would initialize 5 qubits, and then Hadamard them (put them into superposition).
When we Hadmard qubits that start off in state 0, we get the superpostion state of |+⟩.

2) we want to initizalize one more qubit (5+1) ontop of the ones representing the bits in the secret bitstring.
We will have to apply a X Gate (also called the quantum NOT gate) onto extra qubit to change its phase from state 0 to state 1 and then we will Hadamard it.
Since this qubit is Hadamarded from state 1, it’s superposition is going to be |-⟩.

This qubit is more important as it plays imp role for implementeing logic for quantum algo.

3) The Quantum algorithm performs a bunch of CNOT(controlled Not) unlike AND operations in classical way.A CNOT gate acts on two qubits; the control bit and the target bit. The control bit determines whether or not the target bit will flip. 
Logic for Controlled NOT gate, target bit will flip if and only if the control bit is a 1.Otherwise it target bit remains the same. 

4) we apply another Hadamard gate onto all our qubits, to reverse their states back into fixed values. So every qubit that was in state |-⟩ gets turned back into state 1, and every qubits in state |+⟩ gets turned back into state 0!

5) We finally measure the qubits and store them into some classical bits (excluding the last extra qubit) and our result should shows us the secrete number. 

The most important part of this quantum algorithm is, it will do this all in just one step, irrespective of lengh of input bitstring.
It demonstrates something knows as “quantum supremacy”.
 
It’s yet another algorithm that proves the exponential speed up of quantum computers.
