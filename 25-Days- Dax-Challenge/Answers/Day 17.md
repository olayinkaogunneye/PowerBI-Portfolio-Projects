Day 17: How many products need to be restocked? (based on restock levels)

DAX: FILTER(), COUNTA()

            CALCULATE(
                      COUNTA(
                            Products[ProductName]),  
            
                                FILTER(Products, 
                                
                                      Products[Stocked units]<  [Restock level]))
