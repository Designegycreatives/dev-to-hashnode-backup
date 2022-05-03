## PPMT Function

**PPMT FUNCTION** Helps you get principal for given period.

**PPMT FUNCTION** is a financial function, that calculates the payment on the principal for an investment based on periodic, constant payments and a fixed interest rate for a given period of time.

**Formula**

=PPMT(rate, per, nper, pv, [fv], [type])

The PMT FUNCTION uses the following arguments:

1. Rate:(required argument) - The interest rate per period.
2. Per:(Required argument) - It is the bond's maturity date, that is, the date when bond expires.
3. Nper:(required argument) - The total number of payments period in an annuity.
4. Pv:(required argument) - The present value of the loan/investment.
5. Fv:(optional argument) - Specifies the future value of the loan/investments.
6. TYPE:(optional argument) - It specifies whether the payment is made at the start or the end of the period.

**How to use the PPMT Function in Excel**

Example: We need to calculate the payment on the principal for months 1 and 2 on a $50,000 loan, which is to be paid off in full after 5 years. Interest is charged at a rate of 5% per year and the loan repayments are to be made at the end of each month.


![image 1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651550818408/47TV5AjIz.png align="left")


![image 2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651550875297/WaLgx8j7n.png align="left")

**For Month 2**


![image 3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651550977316/Us2c79C52.png align="left")


![image 4.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651551021139/6JpYRzAlK.png align="left")

**Things to remember about the PMT Function**

1. #NUM! error - Occurs when:

 given rate value is less than or equal to -1
 given nper value is equal to 0

2. #VALUE! error - Occurs when any of the arguments provided are non-numeric.

3. An error can arise if we forget to convert the interest rate or the number of periods to months or quarters when calculating monthly or quarterly payments.
