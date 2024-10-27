Day 24: How many employee sold over $100k in the current year?

DAX: COUNTROWS(), CALCULATE, FILTER(),

      VAR disyear = YEAR(TODAY())

    RETURN
            CALCULATE(
            
                  COUNTROWS(

            FILTER( VALUES(Employees[EmployeeID]),
            
                             [Total sales] > 100000)),
                             
                                        'Calendar'[Year] = disyear)
        
