Day 23: Which employee had the highest sales in the current year?

DAX: TOPN(), VAR(), CALCULATE()


            VAR disyear = YEAR(TODAY())

              RETURN
                    CALCULATE(
                    
                        SELECTEDVALUE( Employees[Full Name]),
                                
                              TOPN(1, Employees,
        
                CALCULATE([Total sales], 'Calendar'[Year] = disyear)))
