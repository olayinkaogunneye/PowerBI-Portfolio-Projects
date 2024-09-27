CountProductAboveAvg =
 
              
              
              VAR AvgAll = CALCULATE ( [AvgUnitPrice], ALL ( Products ) )
            
                              VAR Result = CALCULATE ( COUNTROWS ( Products ), 
                    
                                                     FILTER ( Products, [Unit Price] > AvgAll ) )
                                                     
              RETURN

                              Result
