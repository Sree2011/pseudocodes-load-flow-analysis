<pre>
<h2><b>MAIN PROGRAM: </b></h2>
FUNCTION main()
    INITIALIZE Ybus matrix of size (n x n) with 0+0j
    INITIALIZE y matrix of size (n x n) with 0+0j
    PRINT "Enter the number of buses:"
    n = INPUT integer
    PRINT "Enter 1 for impedance and 2 for admittance"
    choice = INPUT integer
    y = get_input(choice, n)
    Ybus = calculate_matrix(y, n)
    display_matrix(Ybus)
END FUNCTION
</pre>
<pre>
<h2><b>GETTING INPUT FROM THE USER: </b></h2>
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
<h2><b>DISPLAY THE BUS ADMITTANCE MATRIX: </b></h2>
FUNCTION display_matrix(Ybus)
    PRINT "Bus Admittance Matrix:"
    FOR each row in Ybus DO
        FOR each element in row DO
            PRINT element
        END FOR
        PRINT new line
    END FOR
END FUNCTION
END
</pre>
