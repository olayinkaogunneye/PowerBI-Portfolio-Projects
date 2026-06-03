Day 22: How many employees are 60 years old or over?

DAX: COUNTROWS(), FILTER(), DATEDIFF(), TODAY()

          COUNTROWS(
          
                FILTER(
                
                SUMMARIZE(Employees, Employees[EmployeeID], 
                
                      "age", DATEDIFF(VALUES(Employees[BirthDate]), TODAY(),YEAR)), 
                      
                                                [age] > 60))
