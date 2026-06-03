Day 2: Which product is the most expensive?

DAX: TOPN(), DISTINCT(), CALCULATE()


    MostExpensiveProduct =
                          CALCULATE (
                          
                              SELECTEDVALUE (
                          
                                    (Products[ProductName] ),
                                
                                                            TOPN (1,
    
                                                                    Products,
                                                                            
                                                                            [Unit Price] DESC
                                                                                              )
                                                                                                  )
