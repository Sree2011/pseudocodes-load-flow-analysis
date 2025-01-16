[Home](./README.md)

# Bus Impedance Matrix

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
    Det = DETERMINANT(ybus)
    IF Det == 0
        DISPLAY "Matrix is singular"
    ELSE
        DISPLAY "Bus Impedance matrix:"
        Inv = INVERSE(ybus)
        FOR i in Inv
            DISPLAY i
        END FOR
    END IF
END FUNCTION
</pre>

> INVERSE(ybus) method is defined in [Matrix functions](./matrix-functions.md) for the java version