Day 2: Which product is the most expensive?

DAX: TOPN(), DISTINCT(), CALCULATE()


    MostExpensiveProduct =
                          TOPN (
                              1,
                          
                                DISTINCT ( Products[ProductName] ),
                                
                                                            CALCULATE (
    
                                                                    Products[Unit Price]
                                                                                              )
                                                                                                  )
