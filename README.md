
# Hello-Quantum-world

Beginner's cirq program to display the canonical hello world string - using superdense encoding.

Starting with an example of superdense encoding from Jack Hildary's book "Quantum Computing; An applied approach", I modified the example code to superdense encode the canonical "hello world" string for a starter application.  In the book's original example:

  A sender (Alice) encodes two bits of data and sends the encoded qubit to a receiver (Bob).  

  Upon receipt, the receiver (Bob) applies a Bell state to the qubit, measures the qubit to decode the original 2 bits sent by Alice.

# Hello world modification

To create an Hello World quantum computing example, I started with the above example, and added the following:

1) converted a string ("Hello World" in this example) to its corresponding bit string:

   "01101000 01100101 01101100 01101100 01101111 00100000 01110111 01101111 01110010 01101100 01100100"

       h        e         l       l        o                w          o       r       l         d

2) The above bit string is then parsed into "bit pairs", encoding each bit pair using superdense encoding gates (from Hildary's example). the first character ("h") bit pairs look like:

   '01', '10', '10', '00'  

           "h"

   The circuit for the first character ("h") is generated as such:

   0: ───H───@───Z───@───H───M───
   
   1: ───────X───────X───M───────

3) The remaining characters are processed in a loop, generating and running the appropriate circuit for each remaining bit pair.

# program execcution

Note:  Superdense encoding "hi" for brevity :)

from hi_quantum_world.txt file:

C:\Users\x>c:\python38\python.exe  c:\cirq\hello_quantum_world.py

#received hi

#received 01101000 01101001

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
