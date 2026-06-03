Day 19: What is the stocked value of the discontinued products?

DAX: SUMX(), CALCULATE()

          CALCULATE(
                    SUMX(Products,
                            [Unit Price]*[Stocked units]),Products[Discontinued] =TRUE())
