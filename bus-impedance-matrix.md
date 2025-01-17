[Home](./README.md)

# Bus Impedance Matrix


## Algorithm

1. **Get Input from the User:**
    - Define a function `get_input(choice, n)`:
        - If `choice` is 1:
            - For each bus `i` from 1 to `n`:
                - For each bus `j` from 1 to `n`:
                    - Prompt the user to enter the impedance between bus `i` and bus `j`.
                    - Store the reciprocal of the entered impedance in `y[i][j]`.
        - Else if `choice` is 2:
            - For each bus `i` from 1 to `n`:
                - For each bus `j` from 1 to `n`:
                    - Prompt the user to enter the admittance between bus `i` and bus `j`.
                    - Store the entered admittance in `y[i][j]`.
        - Return the matrix `y`.

2. **Calculate the Bus Admittance Matrix:**
    - Define a function `calculate_matrix(y, n)`:
        - For each bus `i` from 1 to `n`:
            - For each bus `j` from 1 to `n`:
                - If `i` is equal to `j`:
                    - For each bus `k` from 1 to `n`:
                        - Add `y[i][k]` to `Ybus[i][j]`.
                - Else:
                    - Set `Ybus[i][j]` to `-y[i][j]`.
        - Return the matrix `Ybus`.

3. **Calculate the Bus Impedance Matrix:**
    - Define a function `calculate_zbus(ybus)`:
        - Calculate the determinant of `ybus` and store it in `Det`.
        - If `Det` is 0:
            - Display "Matrix is singular".
        - Else:
            - Display "Bus Impedance matrix:".
            - Calculate the inverse of `ybus` and store it in `Inv`.
            - For each element `i` in `Inv`:
                - Display the element `i`.


## Pseudocode

<pre>
<h2><b>MAIN PROGRAM </b></h2>
FUNCTION main()
    DISPLAY "Enter the no.of buses:"
    INPUT n
    DISPLAY "Enter 1 for impedance and 2 for admittance"
    INPUT choice

    CALL get_input(choice,n) AND STORE THE RESULT INTO y
    CALL calculate_matrix(y,n) AND STORE THE RESULT INTO Ybus
    CALL calculate_zbus(Ybus,n) AND STORE THE RESULT INTO Zbus
    CALL display_matrix(Zbus,n)
    
END FUNCTION
</pre>
<pre>
<h2>GET INPUT FROM THE USER</h2>
FUNCTION get_input(choice, n)
    IF choice == 1 THEN
        FOR each bus i from 1 to n DO
            FOR each bus j from 1 to n DO
                PRINT "Enter the impedance between bus i and bus j:"
                yij = INPUT complex number
                y[i][j] = 1 / yij
            END FOR
        END FOR
    ELSE IF choice == 2 THEN
        FOR each bus i from 1 to n DO
            FOR each bus j from 1 to n DO
                PRINT "Enter the admittance between bus i and bus j:"
                y[i][j] = INPUT complex number
            END FOR
        END FOR
    END IF
    RETURN y
END FUNCTION
</pre>

<pre>
<h2><b>CALCULATE THE BUS ADMITTANCE MATRIX: </b></h2>
FUNCTION calculate_matrix(y, n)
    FOR each bus i from 1 to n DO
        FOR each bus j from 1 to n DO
            IF i == j THEN
                FOR each bus k from 1 to n DO
                    Ybus[i][j] = Ybus[i][j] + y[i][k]
                END FOR
            ELSE
                Ybus[i][j] = -y[i][j]
            END IF
        END FOR
    END FOR
    RETURN Ybus
END FUNCTION
</pre>
<pre>
<h2><b>CALCULATE THE BUS IMPEDANCE MATRIX</b></h2>
FUNCTION calculate_zbus(ybus)
    INITIALISE Inv matrix with zeros
    Det = DETERMINANT(ybus)
    IF Det == 0
        DISPLAY "Matrix is singular"
    ELSE
        DISPLAY "Bus Impedance matrix:"
        Inv = INVERSE(ybus)
    END IF
    RETURN Inv
END FUNCTION
</pre>

> INVERSE(ybus) method is defined in [Matrix functions](./matrix-functions.md) for the java version