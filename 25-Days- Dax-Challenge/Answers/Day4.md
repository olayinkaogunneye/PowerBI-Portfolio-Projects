How many product are above the average unit price

DAX: CALCULATE(), ALL(), COUNTROWS(), FILTER()
 
              
              
              VAR AvgAll = CALCULATE 
              
                                 ( [AvgUnitPrice], ALL ( Products ) )
            
                                         VAR Result = CALCULATE ( COUNTROWS ( Products ), 
                    
                                                     FILTER ( Products, [Unit Price] > AvgAll ) )
                                                     
              RETURN

                              Result
