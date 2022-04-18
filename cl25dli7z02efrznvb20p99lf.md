## NPV Function

What is NPV Function?

**NPV Function** is categorized under **Financial Functions.**

NPV means **NET PRESENT VALUE (NPV)**

The NPV Function calculates the periodic cash flows and the Net Present Value of an investment.

It is calculated for an investment by using a **discount rate** and **series of future payments and income.**

In **Financial Modeling** NPV Function is useful in determining the value of an investment or understanding the feasibility of a project.

**NB**

 It is better for **Analysts** to use **XNPV Function** instead of the regular NPV Function.

**Formula**

**=NPV(rate, value1, [value2],...)**

Rate: It is the rate of discount over the length of the period

Value1, Value2: Value1 is required option, They are numeric values that represent series of payments and income where;

- Negative payments represent outgoing payments

- Positive payments represent incoming payments

**Using NPV Function In Excel**


![image 1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1650325298112/maKuUx0Mw.png)


![image 2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1650325419817/0yzuptEt9.png)


![image 3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1650325481223/eLlRGUvKj.png)

The **NPV Formula** is based on future cash flows. if the first cash flow occurs at the start of the first period, the first value must be added to the NPV result, not included in the values arguments.

**Things to remember about NPV Function**

1. Arguments are the empty cells, logical values, or text representations of numbers, error values, or text that cannot  be translated into numbers are ignored.

2. If an argument is an array or reference, only numbers in that array or reference are counted. Empty cells, logical values, text, or error values in the array or reference are ignored.

3. We need to enter our payments and income values in the right sequence as NPV uses the order of value1, value2,... to interpret the order of cash flows.

4. Value1, value2,... must be equally spaced in time and occur at the end of each period.

5. The NPV function is related to the IRR Function **(Internal Rate Of Return)**, IRR is the rate for which the NPV equals zero.

6. The primary difference between PV Function and NPV is that PV allows cash flows to begin either at the end or at the beginning of the period.
