Day 7: What is the order value in $ of open orders? (Not Shipped yet)

DAX: CALCULATE(), SUM(), FILTER(), BLANK()

            OpenOrdersValue =
                                  CALCULATE (
                                  
                                          SUM ( Orders[_Sales] ),
                                          
                                                      FILTER ( Orders, Orders[ShippedDate] = BLANK () )

)

