## PMT(Periodic Payment For A Loan)

What is **PMT FUNCTION?**

The **PMT Function** is categorized under financial **EXCEL FUNCTIONS**. The function helps calculate the total payment **(Principal and Interest)** required to settle a loan or an investment with a fixed interest rate over a specific time period.

**Formula**
=PMT(rate, nper, pv, [fv], [type])

The **PMT FUNCTION** uses the following arguments:

1. **Rate:**(required argument) - The interest rate of the loan
2. **Nper:**(required argument) - The total number of payments for the loan taken
3. **Pv:**(required argument) - The present value or total amount that a series of future payments is worth now. it is also called **Principal** 
4. **Fv:**(optional argument) - The **FV** or a cash balance we want to attain after the last payment is made. if **FV** is omitted, it is assumed to be 0, that is, the future value of the loan is 0
5. **TYPE:**(optional argument) - The security's price, it is the type of day count basis to use. The possible values of basis are:

**Basis** | **Day count basis**
    ----      |      ---- 
0 or omitted | US(NASD) 30/360
1                    | Actual/actual
2                   | Actual/360
3                   | Actual/365
4                   | European 30/360 

**How to use the PMT Function in Excel**

Example: Let's assume that we need to invest in such a manner that after two years, we'll receive $75,000. The rate of interest is 3.5% per year and the payment will be made at the start of each month the details are;


![image 1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1650989080331/ivc8EPFbo.png)


![image 2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1650989092103/kP50DOVkQ.png)

 
![image 3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1650989103564/5q16SwMNj.png)

The above function returns **PMT** as $3,240.20. It is the monthly cash outflow required to realize $75,000 in two years.

**Things to remember about the PMT Function**

1. #NUM! error - Occurs when:
 - The given rate value is less than or equal to -1
 -  The given nper value is equal to 0

-  #VALUE! error - Occurs when any of the arguments provided are non-numeric.

- When calculating monthly or quarterly payments, we need to convert annual interest rates or the number of periods to months or quarters.

- If we wish to find out the total amount that was paid for the duration of the loan, we need to multiply the **PMT** as calculated by **nper.**

