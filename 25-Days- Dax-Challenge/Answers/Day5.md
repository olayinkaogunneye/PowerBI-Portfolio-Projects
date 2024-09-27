Count Product that Cost between 15-25 =

        CALCULATE (
            COUNTROWS ( Products ),
                Products[UnitPrice] >= 15 && Products[UnitPrice] <= 25
                )
