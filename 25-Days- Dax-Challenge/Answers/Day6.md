DAX: AVERAGEX(), CALCULATE(), SUMMARIZE()


              AverageOrderbyProduct = AVERAGEX(
              
                                            SUMMARIZE(Orders, 
                                                              Orders[OrderID], 
                                                                      "ProdCount",COUNTA(Orders[ProductID])),
                                        [ProdCount])
