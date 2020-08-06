
# Hello-Quantum-world

Beginner's cirq program to display the canonical hello world string - using a quantum communication protocol, superdense coding.  

From wikipedia:
"Superdense coding is the underlying principle of secure quantum secret coding. The necessity of having two qubits to decode the information being sent eliminates the risk of eavesdroppers intercepting messages."

Starting with an example of superdense encoding from Jack Hidary's book "Quantum Computing; An applied approach", I modified the example code to superdense encode the canonical "hello world" string for a starter application.  In the book's original example:

A sender (Alice) encodes two bits of data and sends the coded/entangled qubit to a receiver (Bob).  

Upon receipt, the receiver (Bob) applies a Bell state to the qubit, measures the qubit to decode the original 2 bits sent by Alice.

# Hello world modification

To create an Hello World quantum computing example, I started with the above example, and added the following:

1) converted a string ("Hello World" in this example) to its corresponding bit string:

   "01101000 01100101 01101100 01101100 01101111 00100000 01110111 01101111 01110010 01101100 01100100"

       h        e         l       l        o                w          o       r       l         d

2) The above bit string is then parsed into "bit pairs", encoding each bit pair using superdense encoding gates (from Hildary's example). the first character ("h") bit pairs look like:

   '01', '10', '10', '00'  

           "h"

   The circuit for the two first bits ("01"),  in the first character ("h"), is generated as such:

   0: ───H───@───Z───@───H───M───
   
   1: ───────X───────X───M───────
   
   The above is generated with the followin circ gates:<br/>
   <br/>
   circ.append(cirq.H(qreg[0]))<br/>
   circ.append(cirq.CNOT(qreg[0], qreg[1]))<br/>  // entangle the two qubits
   <br/>
   #sender encodes the message with the apropriate quantum operation<br/>
   circ.append(message[cirq.Z(qreg[0]) //  for bits "01" <br/>
   <br/>
   #receiver measures the bell state<br/>
   circ.append(cirq.CNOT(qreg[0], qreg[1])) <br/> // decode the bits from the entangled qubit
   circ.append(cirq.H(qreg[0])) <br/>

3) The remaining bit pairs, for each remaining character are processed in a loop, generating and running the appropriate circuit for each remaining bit pair.

# program execution

Note:  Superdense coding "hi" for brevity :) - please see the hello_quantum_world.txt output file for full "hello quantum world" circuits.

from hi_quantum_world.txt file:

C:\Users\x>c:\python38\python.exe  c:\cirq\hello_quantum_world.py

# received hi

# received 01101000 01101001

0

sender's sent message = 01

cirquit:

0: ───H───@───Z───@───H───M───

1: ───────X───────X───M───────

recv'ers recv'd message = 01

1

sender's sent message = 10

cirquit:

0: ───H───@───X───@───H───M───

1: ───────X───────X───M───────

recv'ers recv'd message = 10

2

sender's sent message = 10

cirquit:

0: ───H───@───X───@───H───M───

1: ───────X───────X───M───────

recv'ers recv'd message = 10

3

sender's sent message = 00

cirquit:

0: ───H───@───@───H───M───────

1: ───────X───X───M───────────

recv'ers recv'd message = 00

01101000

4

4

sender's sent message = 01

cirquit:

0: ───H───@───Z───@───H───M───

1: ───────X───────X───M───────

recv'ers recv'd message = 01

5

sender's sent message = 10

cirquit:

0: ───H───@───X───@───H───M───

1: ───────X───────X───M───────

recv'ers recv'd message = 10

6

sender's sent message = 10

cirquit:

0: ───H───@───X───@───H───M───

1: ───────X───────X───M───────

recv'ers recv'd message = 10

7

sender's sent message = 01

cirquit:

0: ───H───@───Z───@───H───M───

1: ───────X───────X───M───────

recv'ers recv'd message = 01

01101001

Received string is: hi
