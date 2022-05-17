## XNPV Function

Get the **Net Present Value (NPV)** for a series of cash flows that may not be periodic.

**XNPV** uses specific dates that correspond to each cash flow being discounted in the series, whereas the regular** NPV Function** automatically assumes all the time periods are equal.


![image 1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652747934818/8TP3gtZjw.png align="left")

**XNPV FORMULA**

=XNPV(Rate, Cash Flows, Dates of Cash Flow)

**Rate**: The discount rate to be used over the length of the period

**Values**: This is an array of numeric values that represent the payments and income where;

- **Negative values** are treated as **outgoing payment**.

- ** Positive values** are treated as **income **

**Dates**: It is an array of dates corresponding to an array of payments.

**XNPV IN Excel**

**Assumptions in the XNPV Example**

- The discount rate is 10

- Start date is June 30, 2018

-  Cash Flow are received on the exact date they correspond to

-  The time between the start date and first cash flow is only 6 months.


![image 2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652749386784/z2TELavJq.png align="left")


![image 3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652749404901/e9iQXlpzY.png align="left")


![image 4.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652749414987/bFzi8DekU.png align="left")

The difference between the **XNPV** and **NPV** formulas is that **XNPV** recognizes that time period between the start date and first cash flow is only 6 months, while the NPV function treats it as a full-time period.

**Things to remember about XNPV**

1. Numbers in dates are indicated as integers
2. XNPV doesn't discount the initial cash flow
3. #NUM! error occurs when either;

- The values and date arrays are of different length

-  Any of the other dates are earlier than the start date

4. #VALUE error - occurs when either;

-  The values or rates arguments are non-numeric; or

-  The given dates are not recognized by Excel as valid dates.







 



