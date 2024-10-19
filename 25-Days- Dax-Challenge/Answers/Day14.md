Day 14: How many customers have NEVER purchased Queso Cabrales?

DAX: DISTINCT(), CALCULATETABLE(), EXCEPT(), COUNTROWS()

#14 No Queso Cabrales Customers =
        
        VAR CustID =
                      
                      DISTINCT ( Customers[CustomerID] )
        VAR Queso =
        
                    CALCULATETABLE ( DISTINCT ( Orders[CustomerID] ),
          
                              Products[ProductName] = "Queso Cabrales")
    
        VAR No_Queso =
        
                      EXCEPT ( CustID, Queso )
          
        VAR Result =
                              COUNTROWS ( No_Queso )
        RETURN
      
                            Result
    )
