Day 10: How many days since "North/South" last purchase?

DAX: CALCULATE(), LASTDATE(), DATEDIFF(), TODAY()

    DaysSinceLastPurchase =
            
            VAR NS_LastDate =
            
                    CALCULATE ( LASTDATE ( Orders[OrderDate] ),
                        
                                        Customers[CompanyName] = "North/South")
              VAR Result =
                          
                          DATEDIFF ( NS_LastDate, TODAY (), DAY )
                          
              RETURN Result
