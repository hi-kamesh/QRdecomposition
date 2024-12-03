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

import numpy as np

def QR_Decomposition(A): 

    n, m = A.shape # get the shape of A
    
    Q = np.empty((n,n)) # initialize matrix Q
    
    u = np.empty((n,n)) # initialize matrix u
    
    u[:,0]=A[:,0]       
    
    Q[:,0]=u[:,0]/np.linalg.norm(u[:,0])
    
    for i in range(1,n):
    
        u[:,i]=A[:,i]
        
        for j in range(i):
        
            u[:,i]-=(A[:,i]@ Q[:,j])*Q[:,j]
        
        Q[:,i]=u[:,i]/np.linalg.norm(u[:,i])
    
    R=np.zeros((n,m ))
    
    for i in range(n):
    
        for j in range(i,m):
        
            R[i,j]=A[:,j] @ Q[:,i]
    
    print(Q)
    
    print(R)

a=np.array(eval(input()))

QR_Decomposition(a)


### Gram-Schmidt Method
```
 Step 1: Define the Vectors
Start with a set of linearly independent vectors {v₁, v₂, ..., vₙ} in an inner product space.

Step 2: Normalize the First Vector
Set u₁ = v₁ / ||v₁||, where ||v₁|| is the norm (or length) of v₁.

Step 3: Find the Second Orthogonal Vector
Compute w₂ = v₂ - <v₂, u₁>u₁, where <v₂, u₁> is the inner product of v₂ and u₁.

Step 4: Normalize the Second Vector
Set u₂ = w₂ / ||w₂||.

Step 5: Repeat the Process
For each subsequent vector vᵢ (i = 3, 4, ..., n), compute:

wᵢ = vᵢ - ∑[<vᵢ, uⱼ>uⱼ] from j=1 to i-1

uᵢ = wᵢ / ||wᵢ||








```

## Output


```
![Screenshot 2024-12-03 103006](https://github.com/user-attachments/assets/bbb83061-624a-4b68-a4fd-de1401e2ffd2)

```

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
