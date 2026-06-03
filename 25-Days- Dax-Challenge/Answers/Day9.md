Day 9: Average sales per transaction(orderID) for "Romero y Tomillo"?

DAX: AVERAGEX(), VALUES(), CALCULATE()

      AvgSales Romero =

            CALCULATE (
                      AVERAGEX (
                                VALUES (Orders[OrdersID]), 
                                                    
                                                    [Total sales]),
                                                                  Customers[companyName] = "Romero y Tomillo")
