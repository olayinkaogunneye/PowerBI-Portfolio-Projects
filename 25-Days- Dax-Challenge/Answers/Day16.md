Day 16: How many products are out of stock?

DAX: SUMMARIZE(), COUNTROWS(), FILTER()

              COUNTROWS
                        (
                            FILTER  
                                    (
                                    
                                      SUMMARIZE(Products, Products[ProductID],
                                      
                                                  "Stock", SUM(Products[UnitsInStock])),[Stock] = 0))
