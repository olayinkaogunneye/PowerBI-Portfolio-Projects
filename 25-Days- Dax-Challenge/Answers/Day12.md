Day 12: How many New customers (first purchase in current year) in 2024?

VAR(), COUNTROWS(), FILTER(), SUMMARIZE(), FIRSTNONBLANKVALUE, MIN()

    VAR Jan = DATE(YEAR(TODAY()),1,1)
    
      RETURN
      
          COUNTROWS(
          
                FILTER(SUMMARIZE(Orders, Orders[CustomerID], "First Date", 
                
                  FIRSTNONBLANKVALUE(Orders[CustomerID], MIN(Orders[OrderDate]))),
                  
                                          [First Date] > Jan))
