Count Product that Cost between 15-25 =

DAX: CALCULATE(),COUNTROWS()

        CALCULATE (
            COUNTROWS ( Products ),
                Products[UnitPrice] >= 15 && Products[UnitPrice] <= 25
                )
