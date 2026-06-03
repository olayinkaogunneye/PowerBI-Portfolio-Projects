Day 20: Which vendor has the highest stock value?

DAX: TOPN(), SUMX(), CALCULATE(), SELECTEDVALUE, SUMMARIZE()

          CALCULATE(
                        SELECTEDVALUE(Suppliers[CompanyName]),
                        
                                 TOPN(1,
                                         SUMMARIZE(Suppliers, Suppliers[CompanyName], 
                                         
                                                    "Stock value", SUMX(Products, [Stocked units]*[Unit Price])), 
                                                    
                                                    [Stock value], DESC))
