# Algorithm for QR Decomposition
EX 08 Algorithm for QR Decomposition
Date: 17.10.2023
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)
## Program:
### Gram-Schmidt Method
```
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: Sriram V
RegisterNumber: 23013561
'''
import numpy as np
def QR_Decomposition(A):
    n, m = A.shape
    
    Q = np.empty((n, n))
    u = np.empty((n, n))
    
    u[:, 0] = A[:, 0]
    Q[:, 0] = A[:, 0] / np.linalg.norm(u[:, 0])
    
    for i in range(1, n):
        
        u[:, i] = A[:, i]
        for j in range(i):
            u[:, i] -= (A[:, i] @ Q[:, j]) * Q[:, j]
            
        Q[:, i] = u[:, i] / np.linalg.norm(u[:, i])
        
    R = np.zeros((n, m))
    for i in range(n):
        for j in range(i, m):
            R[i, j] = A[:, j] @ Q[:, i]
            
    print(Q)
    print(R)
a = np.array(eval(input()))
QR_Decomposition(a)
```
## Output
![Screenshot 2023-11-18 110020](https://github.com/praveenv23013808/QRdecomposition/assets/145824728/a9282a4b-63bd-42f8-8a13-0b0ce3311124)
## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
