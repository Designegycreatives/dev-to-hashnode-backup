## Excel Function For Financial Modeling

#### Excel is a major modeling tool for Financial Analyst and Financial Modeling.
#### This post reference can be gotten from [Corporate Financial Institute](https://www.corporate Financial Institute).
**Duration Function:** is categorized under Financial Functions. it helps to calculate the duration of a security that pays interest on a periodic basis with par value of $100

**Duration** is commonly used by **Portfolio Managers** to predict cash flow of investments.

**Formula:** =DURATION(settlement, maturity, coupon, yield, frequency, [basis])

**Settlement:** is the security's settlement date or the date on which the coupon is purchased.
**Maturity:** is the security's maturity date or the date on which the coupon expires.
**Yield:** is the the security's annual yield.
**Frequency:** is the number of coupon payments per year. For annual payments, the frequency = 1, for semiannual frequency = 2; and for quarterly frequency = 4.
**Basis:** is the type of day count basis to be used.

###### The possible values of basis are;
**Basis** | **Day Count Basis**
---- | ----
0 or omitted | US(NASD) 30/360
1 | Actual/actual
2 | Actual/360
3 | Actual/365
4 | European 30/360 


**Using Duration Function In Excel**
Example 1; Let us calculate the duration of a coupon purchased on April 1, 2022 with a maturity date of April 1, 2025 and a coupon rate of 6%. The yield is 5% and payments are made quarterly.


![image 1.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1649800167331/J8zTaRWD9.jpg)


![image 2.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1649800181200/3lx8i9pPf.jpg)

**Things to remember about the DURATION Function**

1. #NUM! error - Occurs if either:
a. The Supplied Settlement date is >= maturity date; or 
b. Invalid numbers are supplied for the coupon yield, frequency or [basis] arguments

2. #VALUE! error - Occurs if either:
a. Any of the given arguments is non-numeric or
b. One or both of the given settlement or maturity dates are not valid Excel dates.

3. Settlement, maturity, frequency and basis are truncated to integers
