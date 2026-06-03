Day 18: How many products on order we need to restock?

DAX: FILTER(), COUNTROWS()

#18 Restock-InOrder =

        VAR Temp1 =

                FILTER
                          ( 
                                Products, Products[Units In Order] > Products[UnitsInStock] )
          
        RETURN
            
              COUNTROWS ( Temp1 )
