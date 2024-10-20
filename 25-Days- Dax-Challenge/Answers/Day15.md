Day 15: How many customers have purchased only Queso Cabrales (per OderID)?

DAX: FILTER(), SUMMARIZE(), COUNT(), DISTINCT(), INTERSECT(), COUNTROWS()

    VAR Singleorder =SUMMARIZE( 
                     FILTER(
                         SUMMARIZE(Orders, Orders[CustomerID], Orders[OrderID],  
                            
                                         "ProductCount", COUNT(Orders[ProductID])), [ProductCount] = 1),
                                            
                                                  Orders[CustomerID],Orders[OrderID])
    VAR QCpurchases = SUMMARIZE(
                        FILTER(
                          SUMMARIZE(Orders,Orders[OrderID], Orders[CustomerID], 
                        
                              Orders[ProductID]), Orders[ProductID]=11),Orders[CustomerID], Orders[OrderID])   
        RETURN
        
        COUNTROWS(
                    DISTINCT(INTERSECT
                            (Singleorder,QCpurchases)))
