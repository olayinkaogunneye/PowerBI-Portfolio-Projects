
How many current products cost less than $20?

DAX: CALCULATE(), COUNTROWS(), FILTER()


    Count CurrProduct <$20 =
    
                        CALCULATE
                                    (
                                        COUNTROWS ( Products ),
                                        
                                            Products[Discontinued] = FALSE,
                                            
                                                FILTER ( Products, Products[UnitPrice] < 20 )
                                                )
