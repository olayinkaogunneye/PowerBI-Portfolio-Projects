Day 25: How many employees got hired in 1994?

DAX: CALCULATE(), COUNTROWS(), YEAR()

      #25Employee1994 =

            CALCULATE ( COUNTROWS ( Employees ), YEAR ( Employees[HireDate] ) = 1994 )
