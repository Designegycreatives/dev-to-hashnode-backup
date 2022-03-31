## Bar Chat Webapp With Streamlit & Plotly

#### I need to celebrate this little but purposeful achievement of mine lol.

#### My journey to get to work with Stream lit was a very rough but exciting journey

#### I just couldn't understand how it worked after several trials, I am glad to say i finally did it.

#### I love Stream lit and Plotly a whole lot now.

#### I built a simple bar chat web app using Streamlit and Plotly. 

#### The reason I am sharing my simple project is to help anyone struggling with building a web app using Streamlit.

#### It took me a very long time to finally understand and be able to build a simple bar chat with Stream lit.

#### And I know there are several other people like me who is currently battling with building a data science project with Stream lit.

#### Deploying my apps to [Heroku](https://www.heroku.com/) is still a work in progress for me, but the Heroku team have been extremely helpful by guiding me through emails.

#### Here is how I built my first ever simple bar chat with Stream lit & Plotly 

[Streamlit Documentation](https://docs.streamlit.io/)

[Plotly Graph Guides](https://plotly.com/python/)

**Step 1:**
#### I used Pycharm as my IDE for this project.

#### I installed Streamlit, Plotly, Numpy & Pandas as my library frame work

#### I downloaded a supermarket sales dataset from [Kaggle](https://www.kaggle.com/datasets)


```
import streamlit as st
import pandas as pd
import plotly.express as px

st.title('Streamlit')
st.subheader('An App By Pink Data Hub')

st.markdown("""
This Web app will help you analyze the following;
* Your top 10 selling products
* Your Total Profits For Each Month and Year
* Your top 10 best buying Customers and their locations
""")

sales_data = pd.read_csv('supermarket_sales.csv')
st.write(sales_data.head())

select_branch=st.selectbox('What Branch would you like to visualize?',
                             ['A','B','C'])

select_xaxis = st.selectbox('What variable do you want on the X axis',
                            ['Customer type','Gender',
                             'Date','Payment','Rating'])

select_yaxis = st.selectbox('What variable do you want on the Y axis',
                            ['Unit price','Quantity','Tax5%','Total',
                             'cogs','gross margin percentage','gross income'])


select_product = st.selectbox('What product do you want to visualize?',
                              ['Food and beverages','Fashion accessories',
                               'Electronic accessories','Sports and travel',
                               'Home and lifestyle','Health and beauty'])
sales_data = pd.read_csv(r'C:\Users\user\Documents\Data Sets\CSV\supermarket_sales.csv')
sales_data = sales_data[sales_data['Branch'] == select_branch]
sales_data = sales_data[sales_data['Product line'] == select_product]
sales_data = sales_data.groupby(sales_data[select_xaxis])[select_yaxis].sum().head(10).reset_index()

fig = px.bar(x=sales_data[select_xaxis], y=sales_data[select_yaxis])
st.plotly_chart(fig, use_container_width=True)


``` 

**Step 2:**
#### I deployed my app using [Streamlit cloud](https://share.streamlit.io/)

#### To deploy my app I uploaded my project file to GitHub [Read more..](https://github.com/Designegycreatives/streamlit_project.py)

#### I created a Requirements.txt file. A Requirement file just contains all the libraries you used for your project 

```
streamlit==0.86.0
streamlit-folium
pandas<1.2.0
plotly==5.2.1
dash
numpy==1.21.2
pillow
plotly-express
``` 
**Step 3:**
#### I deployed my app to [Streamlit cloud](https://share.streamlit.io/)

#### Here is a link to my app [My Streamlit App](https://share.streamlit.io/designegycreatives/streamlit_project.py/main)

#### This is just the beginning for me, I will still develop more amazing data app and deploy them all to  [Heroku](https://www.heroku.com/) 

#### Thank you for starting this journey with me  

