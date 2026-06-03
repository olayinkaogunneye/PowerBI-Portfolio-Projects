Day 13: How many Lost customers (no purchases in current year) in 2024?

DAX : VAR(), COUNTROWS(), SUMMARIZE(), FILTER(), LASTNONBLANKVALUE(), MAX()

              VAR Jan = DATE(YEAR(TODAY()),1,1)
                      RETURN
                            COUNTROWS(
                                        FILTER(
                                                SUMMARIZE(
                                                              Orders, 
                                  Orders[CustomerID], "Last Date", 
                            
                                    LASTNONBLANKVALUE(Orders[CustomerID],
                                    
                                                    MAX(Orders[OrderDate]))),[Last Date] < Jan))
