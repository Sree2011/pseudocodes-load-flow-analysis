[Home](./README.md)

# Matrix_Functions

Functions for matrix operations involving complex numbers

<pre>
    // Function to get the cofactor matrix
    Function getCofactor(A, temp, p, q, n) 
        Initialize i = 0, j = 0
        
        For each row from 0 to n
            For each col from 0 to n
                If row is not p and col is not q
                    temp[i][j] = A[row][col]
                    j++
                    If j equals n - 1
                        j = 0
                        i++
                    END IF
                END IF
            END FOR
        END FOR
    END FUNCTION

    // Function to find determinant of a matrix
    Function determinant(A, n) 
        Initialize D as Complex(0, 0)
        
        If n equals 1
            Return A[0][0]
        END IF
        
        Initialize temp as n x n matrix
        Initialize sign as 1
        
        For each f from 0 to n
            Call getCofactor(A, temp, 0, f, n)
            D = D + (A[0][f] * determinant(temp, n - 1) * sign)
            sign = -sign
        END FOR
        
        Return D
    END FUNCTION

    // Function to find adjoint of a matrix
    Function adjoint(A, adj) 
        Initialize N as length of A
        
        If N equals 1
            adj[0][0] = Complex(1, 0)
            Return
        END IF
        
        Initialize sign as 1
        Initialize temp as N x N matrix
        
        For each i from 0 to N
            For each j from 0 to N
                Call getCofactor(A, temp, i, j, N)
                sign = (i + j) % 2 == 0 ? 1 : -1
                adj[j][i] = determinant(temp, N - 1) * sign
            END FOR
        END FOR

    END FUNCTION

    // Function to find inverse of a matrix
    Function inverse(A) 
        Initialize N as length of A
        Initialize det as determinant(A, N)
        
        If det is zero
            Print "Singular matrix, can't find its inverse"
            Return null
        END IF
        
        Initialize adj as N x N matrix
        Call adjoint(A, adj)
        
        Initialize inv as N x N matrix
        For each i from 0 to N
            For each j from 0 to N
                inv[i][j] = adj[i][j] / det
            END FOR
        END FOR
        
        Return inv
    END FUNCTION
</pre>