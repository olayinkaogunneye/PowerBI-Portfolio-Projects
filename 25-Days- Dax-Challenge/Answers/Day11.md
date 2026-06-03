Day 11: How many customers have ordered only once?

DAX: SUMMARIZE(), DISTINCTCOUNT(), COUNTROWS, FILTER()

#11 CountCustomerOrderOnce =

              COUNTROWS(
              
                     FILTER(
                 
                         SUMMARIZE(
                     
                              Orders, 
                        
                                    Orders[CustomerID], "Count", DISTINCTCOUNT(Orders[OrderID])),
                            
                      [Count] = 1))
                            
