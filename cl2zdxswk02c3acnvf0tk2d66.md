## XIRR Function

**What is XIRR Function**?

XIRR Function is a financial function that will calculate the **The Internal Rate Of Return**, for a series of cash flows that may not be periodic by assigning specific dates to each individual cash flow.

In **Financial Modelling**, the XIRR Function is useful in determining the value of an investment or understanding the feasibility of a project without periodic cash flows. It helps us understand the rate of return earned on an investment.

**Formula**

=XIRR(Values, dates, [guess])


1. **Values:** (required argument) - It is the array of values that represent the series of cash flows.
2. **Dates:**  (required argument) - It is a series of dates that correspond to the given values.
3. **[guess]** (optional argument) - It is an initial guess of what the IRR would be. if omitted, Excel takes the default value that 10%.

**XIRR Example**

![image 1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652140023737/LbLjduQcU.png align="left")


![image 2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652140043598/GrUgFI3Hv.png align="left")


![image 3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652140053237/Ioh4VkL7i.png align="left")

**Things to remember about the XIRR Function**
1. Numbers in dates are truncated to integers.
2. XNPV and XIRR are closely related.
3. Dates should be entered as references to cells containing dates or values returned from excel formulas
4. #Num error -Occurs If either:

- The Values and dates arrays are of different lengths

-  The given arrays do not contain at least one negative and at least one positive value

-  Any of the given dates precedes the first date provided; or 

- The calculation fails to converge after 100 iterations
5. #VALUE! error - Occurs when either of the dates given cannot be recognized by Excel as valid dates.






