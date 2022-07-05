## Building a CRM Web App With Python

What motivated me build this web app is my desire to be able to have a personal form app built with my own desired questions and database structure.

It took me a while to finally put this few lines of code together, but i am glad i did.

This CRM Web App, is built with python programming, [streamlit](https://streamlit.io) and [Deta Base](https://deta.sh)  an open source data base structure that allows you store your data in a **JSON** Format.

**Importing Necessary Libraries For Our App**
```
import streamlit as st
import pandas as pd
from deta import Deta
import json
import base64
``` 
**Adding Animation at the top of web app**

```
file_ = open("image_1.png", "rb")
contents = file_.read()
data_url = base64.b64encode(contents).decode("utf-8")
file_.close()

st.markdown(
    f'<img src="data:image/gif;base64,{data_url}" alt="dashboard gif">',
     unsafe_allow_html=True
)
``` 
**Our Form Codes**

```
st.header("Pink Data Hub CRM")

pink_data = st.sidebar.selectbox("choose:",("Chose","Database", "Database Connection"))


deta = Deta(st.secrets["deta_key"])

db = deta.Base("CRM-Records")
 
          
if pink_data == "Database":
          with st.form("Submit", clear_on_submit=True):
               id_name = st.text_input("Company's ID")
               name = st.text_input("Company's Name")
               phone = st.text_input("Company's Phone Number")
               email = st.text_input("Company's Email Address")
               location = st.text_input("Company's Location")
               submitted = st.form_submit_button("Submit")
               if submitted:
                     db.put({"company_id":id_name, "company_name":name, "email_address":email, "location":location})

"---"

``` 
**To View Your Collected Data**

```
if pink_data ==  'Database Connection':
    db_content = db.fetch().items
    st.write(db_content)
``` 
To retrieve your stored database in **DETA BASE**
here are links to do so

**[NODE JS](https://docs.deta.sh/docs/base/node_tutorial/)**,
**[PYTHON](https://docs.deta.sh/docs/base/py_tutorial/)**

Here is the [repo](https://github.com/Designegycreatives/crm-form.py) to this project

You can deploy your app to [Streamlit Cloud](https://share.streamlit.io)