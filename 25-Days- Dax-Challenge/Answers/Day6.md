Day 6 : Whats the average number of products per order

DAX: AVERAGEX(), CALCULATE(), SUMMARIZE()


              AverageOrderbyProduct = AVERAGEX(
              
                                            SUMMARIZE(Orders, 
                                                              Orders[OrderID], 
                                                                      "ProdCount",COUNTA(Orders[ProductID])),
                                        [ProdCount])
