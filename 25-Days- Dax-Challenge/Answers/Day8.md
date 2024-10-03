Day 8: How many orders are "single item" (only one product ordered)?

DAX: SUMMARIZE(), COUNTROWS(), FILTER()

      CountSingleItemorder = COUNTROWS(

                                FILTER(
                                            SUMMARIZE(Orders, Orders[OrderID], 
                                            
                                                      "No of product", COUNT(Orders[ProductID])),
                                                      
                                                                      [No of product] = 1))
