# Algorithm for QR Decomposition
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
Developed by: JYOTSHANA S R
RegisterNumber: 24006322
'''
import numpy as np
def QR_Decomposition(A):
    # Find the dimensions of the matrix
    n,m=A.shape
    #Q - Matrix
    Q=np.empty((n,m))
    u=np.empty((n,m))
    # R - Matrix
    R=np.zeros((n,m))
    u[:,0]=A[:,0]
    # Finding e value 
    Q[:,0]=u[:,0]/np.linalg.norm(u[:,0])
    # Finding Q matrix
    for i in range(1,n):
        u[:,i]=A[:,i]    # initialize 
        for j in range(n):
            u[:,i]-=(A[:,i] @ Q[:,j])*Q[:,j]
        Q[:,i]=u[:,i]/np.linalg.norm(u[:,i])  # Updating q matrix
    # Finding R matrix
    for i in range(n):   # Row 
        for j in range(i,m):   # Column
            R[i,j]=A[:,j]@Q[:,i]   # @-dot operator
    print("The Q Matrix is")
    print("",Q)
    print("The R Matrix is")
    print("",R)
        
a = np.array(eval(input()))
QR_Decomposition(a)
```

## Output
![OUTPUT](<Screenshot from 2024-12-25 13-35-01.png>)

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.