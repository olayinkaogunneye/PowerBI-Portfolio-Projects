Day 21: How many employees(%) are female?

DAX: DIVIDE(), VAR(), CALCULATE(), COUNTA(), COUNT()

    VAR femaleemployees =
    
                    CALCULATE(COUNTA(Employees[EmployeeID]), Employees[Gender] = "Female")
                    

    VAR allemployess = COUNT(Employees[EmployeeID])

       RETURN 
                 FORMAT(DIVIDE(femaleemployees, allemployess), "0%")
